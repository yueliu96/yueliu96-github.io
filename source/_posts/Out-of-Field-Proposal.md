---
title: Out of Field Proposal
date: 2019-01-16 15:47:38
tags:
categories:
- NoteBook
---

# Goal

- how concentration, temperature, bilayer, time and pH affects gp41
  - secondary structures ($\alpha$-helix, $\beta$-strand and turn/loop?)
  - tilt angles (if all $\alpha$-helix, or one is $3_{10}$ helix)

## [Oligomeric Structure and Three-Dimensional Fold of the HIV gp41 Membrane-Proximal External Region and Transmembrane Domain in Phospholipid Bilayers](https://pubs.acs.org/doi/10.1021/jacs.8b04010)

### HIV-1 glycoprotein, gp41

- mediate fusion of the virus lipid envelope with the target cell membrane during virus entry into cells
- MPER and TMD
  - membrane-proximal external region (MPER)
    - harbors the epitopes for four broadly neutralizing antibodies
    - binds to the membrane surface
  - transmembrane domain (TMD)
    - anchors the protein to the virus lipid envelope
    - spans the bilayer
  - both are important for HIV entry into cells
    - Trp-to-Ala mutations in MPER and deletion of the MPER $\rightarrow$ abrogate virus entry and membrane fusion
    - replace gp41 TMD with other TMD $\rightarrow$ impact fusion activity
    - truncate C-terminus of TMD in simian HIV $\rightarrow$ reduce fusogenicity

  structure unchanged within 235K to 303K

### MPER-TMD Structure

- Turn Structure
  - helix-turn-helix
  - MPER as bound to the membrane surface while TMD spans the bilayer
  - monomeric
- Continuous Helix
  - continuous helix, perpendicular to the membrane plane
  - tilted orientation for long helix to reduce the hydrophobic mismatch between the peptide adn the bilayer portion of the bicelle
- trimeric-MPER + monomeric-TMD
- Helix-turn-helix trimer
  - most $\alpha$-helix: membrane-independent
  - TMD 50% $\beta$-strand: a combination of the amino acid sequence and the spontaneous negative curvature of PE membranes
  - but not uniquely constrian the turn structure bewteen W678 and K683 at the atomic level

These divergent structural conclusions may arise from the truncated nature of th epeptide sequences in most studies, but could also reflect an inherent conformational plasticity of this region of gp41, which may be importanct for the protein to fold into different structures at different stages of virus-cell fusion

heterogeneity in the protein oligomeric states, differenced in th ebicelle stability and size and the differenct P/L ratios used

### Notes

- $\beta$-strand conformation is correlated with membrane dehydration
- a monomeric membrane-spanning $\alpha$-helix is expected to undergo rapid uniaxial diffusion in the membrane, while a highly oligomerized peptide or a peptide that contains an extended segment on the membrane surface is expected to be immobilized
- MPER-TMD trimer is insensitive to the peptide concentration

### Question
- inconsistent and contradictory structural information abounds in the literature about the C-terminal membrane-interaction region of gp41
- difficulty of crystallizing and solubilizaing the MPER-TMD, most structural studies of this functionally important domain were carried out using either only MPER or only TMD
- FP and TMD disorder the cell and virus membranes by mechanisms that still poorly understood

# SFG Theory

## [Biological Macromolecules at Interfaces Probed by Chiral Vibrational Sum Frequency Generation Spectroscopy](https://pubs.acs.org/doi/10.1021/cr4006044)

Second-order nonlinear optical technique, which uses two pulsed lase sources, one at infrared (IR) frequency ($\omega_{IR}$) and the other at visible frequency ($\omega_{VIS}$). When this two beams are made to spatially and temporally overlap at surfaces, a second order nonlinear optical process producing polarization at the sum frequency ($\omega_{IR}+\omega_{VIS}$) can be induced to generate SFG signal.

The electric field of SFG signals $E_{SFG}^I \propto \sum_{JK}\chi_{IJK}^{(2)} E_{VIS}^J E_{IR}^K$. $\chi_{IJK}^{(2)}$ is an element of the second-order susceptibility tensor, which contains structural and chemical information about the target medium. It is nonzero only when the medium lacks centrosymmetry and the second-order susceptibility of an interface consists of a nonresonant term, $\chi_{NR}^{(2)}$, and a sum of vibrationally resonant terms, $\chi_q^{(2)}$
$$\chi^{(2)}=\chi_{NR}^{(2)}+\sum_q \chi_q^{(2)}=\chi_{NR}^{(2)}+\sum_q \frac{A_q}{\omega_{IR}-\omega_q+i\Gamma_q}$$
where $A_q$ is the amplitude, $\Gamma_q$ is the damping coefficient, $\omega_q$ is the resonat frequency of the qth vibrational mode, and $w_{IR}$ is the frequency of the incident IR beam. The SFG signal is enhanced when $\omega_{IR}$ is in resonance with $\omega_q$. Thus, SFG is a surface-specific vibrational spectroscopy

## [Molecular Chemical Structure on Poly(methyl methacrylate) (PMMA) Surface Studied by Sum Frequency Generation (SFG) Vibrational Spectroscopy](https://pubs.acs.org/doi/full/10.1021/jp013161d) 

In an SFG setup, a pulsed visible laser beam (532nm) and a tunable pulsed IR beam are overlapped spatially and temporally on a surface. The light emitted by the nonlinear process at the sum frequency, $\omega=\omega_1+\omega_2$, is detected by a photodector. The intensity of output is proportional to the square of the samples's second-order nonlinear susceptibility, which vanishes when a material has inversion symmetry under the electric-dipole approximation. Bothe theoretical calculations and experimental results show that SFG is submonolayer sensitive. Aplot of SFG intensities vs the frequency of the IR laser produces the vibrational spectrum of the surface species. As SFG is a polarized light experiment, the orientation of surface molecules can also be deduced by using different polarization combinations of input and output beams.

![sfg setup](https://raw.githubusercontent.com/yueliu96/blog_images/master/sfg_setup.jpg)
$$I(\omega)=\frac{8\pi^3\omega^2sec^2\beta}{c^3n_1(\omega)n_1(\omega_1)n_1(\omega_2)}|\chi_{eff}^{(2)}|^2I_1(\omega_1)I_2(\omega_2)$$
where $n_i(\omega)$ is the refractive index of medium i at frequency $\omega$, $\beta$ is thereflection angle of the sum frequency field, $I_1(\omega_1)$ and $I_2(\omega_2)$ are the intensities of the two input files. $\chi_{eff}^{(2)}$ is the effective second-order nonlinear susceptibility tensor of the surface, which is related to the second-order nonlinear susceptibility $\chi^{(2)}$ in the lab coordinate system.

Different component of $\chi^{(2)}$ are related to the respective componets of the molecular hyperpolarizability (in the molecular coordinated system, which is a product of IR and Raman transition moments) by the average orientational angle of the functional group. Therefore, we can deduce the orientation information of each functional group after determining the corresponding components of $\chi^{(2)}$ by fitting SFG spectra and knowing the molecular hyperpolarizability.

$$
\chi_{eff,ssp}^{(2)}=L_{yy}(\omega_{SFG})L_{yy}(\omega_{Vis})L_{zz}(\omega_{IR})sin\beta_{IR} \chi_{yyz}^{(2)}
$$

$$
\chi_{eff,ppp}^{(2)}=-L_{xx}(\omega_{SFG})L_{xx}(\omega_{Vis})L_{zz}(\omega_{IR})cos\beta_{SFG}cos\beta_{Vis}sin\beta_{IR}\chi^{(2)}_{xxz}\\\\
-L_{xx}(\omega_{SFG})L_{zz}(\omega_{Vis})L_{xx}(\omega_{IR})cos\beta_{SFG}sin\beta_{Vis}cos\beta_{IR}\chi^{(2)}_{xzx}\\\\
+L_{zz}(\omega_{SFG})L_{xx}(\omega_{Vis})L_{xx}(\omega_{IR})sin\beta_{SFG}cos\beta_{Vis}cos\beta_{IR}\chi^{(2)}_{zxx}\\\\
+L_{zz}(\omega_{SFG})L_{zz}(\omega_{Vis})L_{zz}(\omega_{IR})sin\beta_{SFG}sin\beta_{Vis}sin\beta_{IR}\chi^{(2)}_{zzz} \tag{1}
$$

Here $\chi_{xyz}$ is one componaent of $\chi^{(2)}$ with the lab coordinates chosedn such that z is along the interface normal and x is in the incident plane. $\chi_{eff,ssp}^{(2)}$ is a component of the effective second-order nonlinear susceptibility measured in the experiment, means the element obtained by s-polarized SF beam, s-polarized visible beam and p-polarized IR beam. $\beta_{x}$ is the angle between the surface normal and the x beam. $L_{ii} (i=x,y\ or\ z)$ are the Fresnel coefficients. Using the near total reflection geometry, the first three items in equation (1) are approxiamated to be 0. 

With IR-visible SFG, if the IR frequency is near vibrational resonance, $\chi_{eff}^{(2)}$ can be written as 

$$\chi_{eff}^{(2)}=\chi_{nr}+\sum_q \frac{A_q}{\omega_{IR}-\omega_q+i\Gamma_q}$$

$\chi_{nr}$ arises from the nonresonant background contribution

$$
I_{SFG}=|A_0+\sum_j^\text{num of peaks}\frac{A_j}{\omega-\omega_j+i\Gamma_j}|^2\\
\chi^{(2)}_{eff}(j)=\frac{A_j}{\Gamma_j}$$
where $A_j$, $\omega_j$ and $\Gamma_j$ are the strength, resonant frequency and damping coefficient of the vibrational mode j, respectively. And they can be obtained by fitting the spectrum

# SFG Method

## Tell $\beta$-strand and $\beta$-sheet

### [Misfolding of Human Islet Amyloid Polypeptide at Lipid Membrane Populates through β-Sheet Conformers without Involving α-Helical Intermediates](https://pubs.acs.org/doi/10.1021/jacs.8b08537)

1. advantage of this article
- quickly capture the transient intermediates in situ and in real time
- identify the formation of $\beta$-hairpin-like monomers, $\beta$-sheet oligomers and fibrils
- reveal the mechanism of amyloid aggregation at the lipid membrane
- method
  - X-ray crystallography: high-rsolution, but not enough time resolution to probe the real-time aggregation

2. method

   the combination of interface-sensitive chiral amide I, achiral amide II and amide III spectral signals of the protein backbone generated in sum frequency generation vibrational spectroscopy (SFG-VS) can provide a unique and powerful tool to capture the hIAPP intermediates at the interface d uring the agggregation process with sufficient structural temporal resolutions

   develop a highly-sensitive femtosecond SFG-VS system, can acquire the ssp and psp sepctra simultaneously with a recording time of < 5 seconds

   Amide II vibrations arise from the out-of-phase combination of the C-N stretch and the N-H in-plane deformation

- $\alpha$-helix: achiral: 1660, 1280
- $\beta$-sheet:
  - chiral amide I mode:
    - $\beta$-hairpin-like monomer (2 antiparallel hydrogen bonded $\beta$-strands connected by a $beta$-turn or short loop): 1630-1643
    - B mode parallel $\beta$-sheet oligomers and fibruls: 1624 (<1630)
    - A mode parrallel $\beta$-sheet: 1670
  - chiral N-H stretch mode: 3285 $cm^{-1}$
  - achiral amide I
    - 1625
    - 1680
  - achiral amide II at 1540: $\beta$-sheet oligomers and fibrils
- loop: achiral: 1660, 1230
- coil: achiral: 1660
- turn: achiral: 1660
  
## Orientation angles

### [Observing a Model Ion Channel Gating Action in Model Cell Membranes in Real Time in Situ: Membrane Potential Change Induced Alamethicin Orientation Change](https://pubs.acs.org/doi/10.1021/ja2110784)

![sfg](https://pubs.acs.org/appl/literatum/publisher/achs/journals/content/jacsat/2012/jacsat.2012.134.issue-14/ja2110784/production/images/large/ja-2011-110784_0004.jpeg)

#### $3_{10}$-helix

A $3_{10}$ helix is a type of secondary structure found in proteins and polypeptides. Of the numerous protein secondary structures present, it is the 4th most common type observed; following $\alpha$-helices, $\beta$-sheeots and reverse turns. $3_{10}$ helices constitute nearly 10%-15% of all helices in protein secondary structures, and are typically observed as extensions of $\alpha$-helices fond at either their N- or C- termini.


#### alamethicin

Predominantly helical with an N-terminal $\alpha$-helix and a C-terminal domain containing a $3_{10}$-helical element. The Pro14 residue separating the two domains induces a $20^\circ-35^\circ$ bend in alamethicin

#### SFG result

- 1670$cm^{-1}$: a helical structure dominated by $\alpha$-helix with minor contribution from a $3_{10}$-helix
- 1635: $3_{10}$-helical structure
- 1720: carbonyl groups of lipid bilayer
- the relationship between the measured ppp and ssp intensity ratios of the peaks at 1670 and 1635 $cm^{-1}$, it is possible to determine the orientation angles $\theta_1$ and $\theta_2$
- SFG signal intensity is related to the number of molecules detected and their orientations

[Surpport Information](https://pubs.acs.org/doi/suppl/10.1021/ja2110784/suppl_file/ja2110784_si_001.pdf)

### [Orientation Determination of Protein Helical Secondary Structures Using Linear and Nonlinear Vibrational Spectroscopy](https://pubs.acs.org/doi/abs/10.1021/jp904153z)

SFG amide I signals can be collected using different polarization combinations of the input laser beams and output signal beam to measure the second-order nonlinear hyperpolarizability elements through the orientation distribution of these helices.
$$I_{ssp}\propto (-L_{yy}(\omega)L_{zz}(\omega_1)L_{yy}(\omega_2)sin\beta_2 \chi_{yyz})^2$$
where $L_{ii}(\omega)$ is a Fresnel coefficient and local field correction factor and $\beta,\ \beta_1\ and\ \beta_2$ are angles of the signal, visible and IR beams with respect to the surface normal, respectively.

when input or output beam angle is close to the critical angle of the total internal reflection:
$$I_{ppp}\propto |L_{zz}(\omega)L_{zz}(\omega_1)L_{zz}(\omega_2)sin\beta sin\beta_1sin\beta_2 \chi_{zzz}|^2 $$
![SFG tilt](https://raw.githubusercontent.com/yueliu96/blog_images/master/SFGorien.jpeg)

**Pauling's $\alpha$-Helix**

Pauling's assumption: each peptide bond is planar due to the resonace structure between teh carbonyl C=O bond and teh amide C-N bond. On the basis of this assumption, two helical models were constructed and proposed, a $\gamma$-helix (not discovered in any protein structures) and an $\alpha$-helix, with 5.1 residues per turn and 3.6 residues per turn, respectively.

$\alpha$-helix: it repeats itselt every 5.4
$\overset{\circ}{A}$ along the helical axis. Every backbone carbonyl C=O and N-H group on a peptide unit is hydrogen bonded to another N-H and C=O, respectively. Additionally, the backbone C=O groups point in the same direction, while the N-H groups point in the opposite direction.

Three amide I vibrational modes of $\alpha$-helices, A, $E_1$ and $E_2$. A and $E_1$ are IR-active, while the all three modes are Raman-active. Because a SFG-active mode needs to be both IR- and Raman-active, only the A and $E_1$ modes are SFG-active.

### [Interactions of Alamethicin with Model Cell Membranes Investigated Using Sum Frequency Generation Vibrational Spectroscopy in Real Time in Situ](https://pubs.acs.org/doi/10.1021/jp911174d)
![alam tilt](https://raw.githubusercontent.com/yueliu96/blog_images/master/alam%20helix%20angle.jpeg)

# To Be Read 

[In Situ Molecular Level Studies on Membrane Related Peptides and Proteins in Real Time Using Sum Frequency Generation Vibrational Spectroscopy](https://www.sciencedirect.com/science/article/pii/S1047847709000744?via%3Dihub)



[Structure and Orientation of Interfacial Proteins Determined by Sum Frequency Generation Vibrational Spectroscopy: Method and Application](https://www.sciencedirect.com/science/article/pii/B9780124165960000075?via%3Dihub)

# Useful Link

1. [Protein Secondary Structure](http://www.cryst.bbk.ac.uk/PPS2/course/section8/ss-960531_1.html)