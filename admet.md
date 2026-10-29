---
layout: default
title: ADMET, or How to Predict Small Molecule Toxicity
---
  Prediction of absorption, distribution, metabolism, excretion, and toxicity of drug candidates.
  <p><h2 id="header-3">Installing ADMET-AI</h3><p>
    Though the <a href="https://admet.ai.greenstonebio.com/">web server</a> works, <a href="https://github.com/swansonk14/admet_ai">installing it locally</a> 
      gives you more customization and data.
    <pre><code>pip install admet-ai</code></pre>
  <p><h2 id="header-3">Preparing Input Files</h3><p>
    Make a .csv file with one column using 'smiles' as the column header. Each row is the SMILES of whatever compound you're using as input.<br>
    If you did molecular docking with Vina, SMILES can be found from the output .pdbqt file.<br>
    If you know the ligand you're interested in, you can look up the SMILES on <a href="https://www.rcsb.org/"RCSB PDB</a>.
    Though several SMILES formats exist, this program was robust to accept the ones I tested (ACDLabs, CACTVS).
    <p></p>
    <table>
  <tr>
    <th>smiles</th>
  </tr>
  <tr>
    <td>Cn1cnc2N(C)C(=O)N(C)C(=O)c12</td>
  </tr>
</table>
    <br>Alternatively, obtain SMILES by looking up the ZINC ID
    in <a href="https://cartblanche22.docking.org/">Carteblanche</a> or with curl, supplying a list of ZINC IDs as input:
    <pre><code>curl -X POST https://cartblanche22.docking.org/substances.txt -F zinc_ids=@[file name here].txt -F output_fields='smiles,zinc_id'</code></pre>
