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
    Make a .csv file with one column using 'smiles' as the column header. Each row is the SMILES of whatever compound you're using as input.
    If you did molecular docking with Vina, SMILES can be found from the output .pdbqt file.
    If you know the ligand you're interested in, you can look up the SMILES on <a href="https://www.rcsb.org/">RCSB PDB</a>.
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
    <p><h2 id="header-3">Analyzing Compounds and Visualizing Results</h3><p>
      To perform predictions, run this code in the terminal:
      <pre><code>admet_predict --data_path [input_filename].csv --save_path [desired_output_filename].csv --smiles_column smiles</code></pre>
      You can make radial summaries of key properties using their Python scripts:
      <pre><code>python plot_radial_summaries.py --data_path [output_from_admet].csv --save_dir radialplot --image_type png</code></pre>
    <p><h2 id="header-3">Results Interpretation</h3><p>
    The outputs are probabilities ("What's the probability this molecule is carcinogenic?") and percentiles ("Compared to all reference molecules this
      neural network was trained on, how carcinogenic is this molecule predicted to be?"). 
      Unless you have a pharmacology background, some of the output may be unfamiliar to you. I recommend reading 
      <a href="https://admetmesh.scbdd.com/static/explanation/files/Explanation.pdf">their own explainer</a> which goes in depth as to what these mean.
      I personally prioritize high bioavailability, moderate lipophilicity, minimizing violations of Lipinski's rule, and as low as possible scores for clinical toxicity,
      carcinogenicity, and hERG inhibition, but since these are all probabilistic, you will really have to decide and test for yourself eventually.
