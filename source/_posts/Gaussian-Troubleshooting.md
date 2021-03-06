---
title: Gaussian Troubleshooting
date: 2019-01-22 20:05:42
tags:
- Software Tutorial
categories:
- Turecek Lab Tutorial
---

Troubleshooting about:  [Freq: Negative Frequency](#nfreq) | [Freq job never stops calculating vectors](#vecfreq) | [Opt: Energy Oscillates](#eosc) | [Opt: FormBX had a problem](#formbx) | [Opt-Solution: Inv3 failed in PCMMkU](#pcm) | [Transformation cannot fit in the specified MaxDisk](#maxdisk) | To be continue ...

# <jump id='eosc'>Energy oscillates and opt never converges (I)</jump>

If during geometry optimization the energy oscillates as shown in the following figure:
![E_osc](https://raw.githubusercontent.com/yueliu96/blog_images/master/energy_osc.PNG)

Try ([Reference](https://www.researchgate.net/post/What_are_possible_solutions_when_the_during_geometry_optimization_the_energy_oscillates_as_shown_in_attachment)):

1. restart the geometry optimization from the point with the lowest energy (step 60 marked by a red circle for this case). It works for all of my jobs for now. If it doesn't work, try what is listed below. But the following two methods either runs forever or doesn't help in my cases.
2. change `opt` to `opt(calcfc)` on the route card
   - specifies that the force constants be computed at the first point using the current method.
   - ensures that the calculation starts with accurate second derivatives, but may be too expensive to be practical. 
   - e.g., one of my jobs take 9 hours to finish with `opt(calcfc)` compared to 3 hours without it.
3. add another keyword [`Integral(UltraFine)`](http://gaussian.com/integral/) on the route card
   - It is recommended for molecules containing lots of tetrahedral centers and for computing very low frequency modes of systems to use.
   - Also useful for optimizations of larger molecules with many soft modes such as methyl rotations, making such optimizations more reliable.
   - But note that it is very important to **use the same gride for all calculations where you intend to compare energies**.

# Energy oscillates and opt never converges (II)

Another type of energy oscillation is shown in the following figure. Energies always oscillate around a certain number and rarely change due to small gradient values (close to  0). 

![RMS small](https://raw.githubusercontent.com/yueliu96/blog_images/master/energy_osc2.PNG)

Solution:

Load the output file to GaussView and see how structures change with optimation step numbers. Manually modify the structure by a little bit and reoptimize it again. Usually change the angle between two atoms/groups where structres get stuck.

# <jump id='formbx'>FormBX had a problem</jump>

If get error message like:

```
 GradGradGradGradGradGradGradGradGradGradGradGradGradGradGradGradGradGrad
 Berny optimization.
 Using GEDIIS/GDIIS optimizer.
 Bend failed for angle    33 -    87 -    81
 Tors failed for dihedral    32 -    33 -    87 -    81
 Tors failed for dihedral    34 -    33 -    87 -    81
 Tors failed for dihedral    86 -    33 -    87 -    81
 Tors failed for dihedral    15 -    81 -    87 -    33
 FormBX had a problem.
 Error termination via Lnk1e in /sw/contrib/gaussian/g16/B01/g16/l103.exe at Tue Jan 22 12:58:22 2019.
```

That means the angle formed by atom 33, 87 and 81 is 180$^\circ$. So, modify it manually and start over optimization again.

# <jump id='pcm'> Inv3 failed in PCMMkU </jump>

This is related to the solute cavity of the solvent model. The default option for SCRF is Polarizable Continuum Model (PCM), which creates the solute cavities via a set of overlapping spheres centered on the atom and with certain atomic radii. The default atomic radii are small, resulting in the solvent cavity of larger molecules looks like "cheese". There are many holes and grooves that are mathematically exposed to the solvent, while these locations are not exposed to solvents in actual systems. This causes the problem of non-convergence during the iteration of the PCM matrix.

To solve this problem, we can add additional input: [**Surface**=*type*](http://gaussian.com/scrf/): specify the type of molecular surface representing the solute-solvent boundary. Available options are:

- VDW: Van der Waals surface. Uses atomic radii (scaled) and skips the generation of “added spheres” to smooth the surface. This is the default.
- SES: Solvent Excluding Surface. The surface is generated by the atomic or group spheres and by the spheres created automatically to smooth the surface (“added spheres”). This was the default in Gaussian 03. It can eliminate the above mentioned holes and grooves, but the surface made by this method doesn't change continuously with the change of conformation, causing the potential energy surface isn't continuous and smooth and it is difficult to perform geometric optimization.
- SAS: Solvent Accessible Surface. The radius of the solvent is added to the unscaled radii of atoms and/or atomic groups. There is no "cheese problem" and dicontinuity on SAS surface. But it might underestimate the solvation effect compared to VDW and SES due to the large solute cavity.

![scrf](https://raw.githubusercontent.com/yueliu96/blog_images/master/scrf_surface.png)

A good solution is to optimize with SAS following by single point energy calcuation with SES surface. To optimize with SAS or SES, e.g. add `scrf(pcm, solvent=water, read)` on the route card, and `Surface=SAS` or `Surface=SES AddSph` on the additional section, which is after molecular specification and also terminated with a blank line.

```
%mem=60gb
%nprocshared=28
%chk=test.chk
# opt wb97xd/6-31+g(d,p) pop=none scf=(xqc,tight) scrf=(pcm,solvent=water,read)

Title section

Charge Multiplicity
Molecular Coordinates

surface=sas

--Link1--
%chk=test.chk
%mem=60gb
%nprocshared=28
# wb97xd/6-31+g(d,p) pop=none scf=(sqc,tight) scrf=(pcm,solvent=water,read) geom=allcheck

surface=ses addsph
! terminate by a blank line
```

# <jump id='nfreq'> Negative Frequency </jump>

Gaussian optimization algorithm uses the gradient descent to find the closest minmum ($f'(x)=0$). However, the gradient of a local maximum point is also 0, which corresponds to a transition state. A transition state should have one negative/imaginary frequency.

Frequencies can be visualized after loading the output file into GaussView. What we should do is locate the imaginary frequency, move the atom/atom group in the direction of this vibration, reoptimize this modified structure and calculate the frequency again.

# <jump id='vecfreq'> Freq Job Never Stops Calculating Vectors</jump>

Gaussian uses two different algorithms to do a frequency calculation (solving the CPHF equations) The  standard one uses a lot of RAM memory but is very fast. However, when RAM memory is not enough or the number of CPHF  equations exceeds 5000 by default, gaussian uses another algorithm, this tries to save RAM memory  by storing intermediate results on a hard disk. This takes very long making the calculations practically  inactive.

If limited by RAM memory, increase it by linkwords `%mem=xxx`. If  CPHF equations exceed 5000 and there is enough memory available, add an extra keyword: `CPHF(MaxInv=10000)` on the route card. This puts the maximum number of  CPHF equations for the basic algorithm to 10,000.

# <jump id='maxdisk'>Transformation cannot fit in the specified MaxDisk</jump>

We will get this error when specifying `maxdisk=xxx` and the disk is not enough to finish the current job.

The MaxDisk keyword specifies the amount of disk storage available for scratch data. But some jobs, like CCSD, CCSD(T), QCISD(T), and BD(T) energies have fixed disk which cannot be limited by MaxDisk. In this case, if the disk storage is not enough, we will get error information like:

```
 Semi-Direct transformation.
 ModeAB=           4 MOrb=            51 LenV=   26834989397
 LASXX=   3675829080 LTotXX=  3675829080 LenRXX=  7405142880
 LTotAB=  3729313800 MaxLAS=  4334140395 LenRXY=           0
 NonZer= 11080971960 LenScr= 22248854016 LnRSAI=  4334140395
 LnScr1=  8702274560 LExtra=   897554704 Total=  43587966555
 MaxDsk= 13421772800 SrtSym=           T ITran=            4
 Transformation cannot fit in the specified MaxDisk.
 Error termination via Lnk1e in /sw/contrib/gaussian/g16/B01/g16/l804.exe at Wed Dec 19 01:05:37 2018.
 Job cpu time:       0 days  7 hours 19 minutes 44.3 seconds.
 Elapsed time:       0 days  0 hours 15 minutes 43.2 seconds.
 File lengths (MBytes):  RWF=  63349 Int=      0 D2E=      0 Chk=     16 Scr=      1
```

Where, `MaxDsk=13421772800` means I uses `maxdisk=100G` ($\frac{13421772800\times8}{1024^3}$); `Total=43587966555` means the minimum disk should be 325G ($\frac{43587966555\times8}{1024^3}$).

For Hyak, there is around 100G storage space for one node. So we can locate the largest scratch file (read and write file) to `/gscratch/scrubbed/username/` like:

```bash
%rwf=/gscratch/scrubbed/yueliu96/test.rwf
%nosave
```