---
layout: default
title: MD, or How to Simulate Molecular Trajectories
---

  Using Newtonian physics to calculate the trajectories of all atoms in a system over time.
  <i>J Phys Chem B.</i> 2024 Jan 11;128(1):109-116. doi: 10.1021/acs.jpcb.3c06662.
  <p><h3 id="header-3">Installing OpenMM</h3><p>
    I recommend using Conda to create an environment for OpenMM. Dependencies and version mismatches can be tricky. There are several ways to install Conda, but I usually use <a href="https://conda-forge.org/download/">Miniforge</a>. Then, to make an environment using Conda, in Bash:
    <pre><code>conda create -n openmm-test -c conda-forge python openmm jupyterlab ipykernel parmed pdb2pqr</code></pre>
    Then, to test whether OpenMM works and print the version, also in Bash:
    <pre><code>python -m openmm.testInstallation</code></pre>
    To check your GPU:
    <pre><code>nvidia-smi</code></pre> or <pre><code>amd-smi</code></pre>
    If OpenMM cannot connect to your GPU, you may have to update CUDA (or ROCm) or update GPU drivers.
  <p><h3 id="header-3">Preparing Proteins</h3><p>
  <p><h3 id="header-3">Preparing Ligands</h3><p>
  <p><h3 id="header-3">References for Further Reading</h3></p>
Eastman P, Galvelis R, Peláez RP, Abreu CRA, Farr SE, Gallicchio E, Gorenko A, Henry MM, Hu F, Huang J, Krämer A, Michel J, Mitchell JA, Pande VS, Rodrigues JP, Rodriguez-Guerra J, Simmonett AC, Singh S, Swails J, Turner P, Wang Y, Zhang I, Chodera JD, De Fabritiis G, Markland TE. OpenMM 8: Molecular Dynamics Simulation with Machine Learning Potentials. <i>J Phys Chem B. 2024</i> Jan 11;128(1):109-116. doi: 10.1021/acs.jpcb.3c06662.
