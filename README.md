# Toy Models of Superposition Replication
This repository is replication of the paper Toy Models of Superposition conducted by researchers at Anthropic and Harvard in 2022. This repository includes
a replication of the experiments from the introduction and sections 2 and 3 of the original paper.

I write up all my findings in a PDF document which can be found under the filename <b><a href="https://github.com/zroe1/toy_models_of_superposition/blob/main/FINDINGS.pdf">FINDINGS.pdf</a></b> in this repository. This document details the results
of my experiments along with additional commentary from section 1 of the original paper.

## What this respository includes

<ol>
  <li>
    <b>A complete writeup of all my findings: </b> This is found under the filename <b><a href="https://github.com/zroe1/toy_models_of_superposition/blob/main/FINDINGS.pdf">FINDINGS.pdf</a></b> in this repository. Because this repository is
    dedicated to being a paper replication, it felt natural to write down my findings in the format of a paper so they are all found in
    one place. The LaTeX file used to create the pdf if also provided under the name FINDINGS.tex.
  </li>
  <li>
    <b>The code: </b>Jupyter notebooks are provided which can be used to generate the results of all experiments I ran to replicate the findings of the original paper.
    These experiments are organized into folders which share the same name as the titles of the sections in the original paper so everything is easy to find. 
  </li>
  <li>
    <b>Summary: </b> For people who (reasonably) don't want to read through all of FINDINGS.pdf, I have provided a more concise summary of my findings
    in this markdown file (which admittedly also isn't too short). This can be found in the section below.
  </li>
</ol>

## Summary

This summary is a breif overveiw of my findings from <b><a href="https://github.com/zroe1/toy_models_of_superposition/blob/main/FINDINGS.pdf">FINDINGS.pdf</a></b>.

### Introduction:

In the introduction of the original paper, the provide this interesting graphic, illustrating superposition within a model. They graph each column of
a model's wieghts as a vector and display how the model changes as you vary sparsity.

I was able to get the same result using the information from the paper:

<img width="730" alt="section1_replicated_graphic" src="https://github.com/zroe1/toy_models_of_superposition/assets/114773939/1d968aee-ec92-4abf-81bf-4eb9b9bfe894">  

Note that the bold lines display the length of the vector while the dotted ones merely show what the vector would look like if it was extended. The patern is the same:
if there is no sparsity in the input, the model encodes the two most important features orthogonally. When you introduce sparsity, you begin to see superposition.

### Demonstrating Superposition:

#### Linear Models:
<p align="center">
<img width="400" alt="relu_linear_0_sparsity" src="https://github.com/zroe1/toy_models_of_superposition/assets/114773939/403f2eec-4773-479b-9a0f-6419fd464387">
</p>

#### Models With Sparsity:

<p align="center">
<img width="600" alt="sparsity_superposition1" src="https://github.com/zroe1/toy_models_of_superposition/assets/114773939/827eeba9-bc02-47a8-b8eb-bde6700adaf8">
</p>

<p align="center">
<img width="600" alt="sparsity_superposition2" src="https://github.com/zroe1/toy_models_of_superposition/assets/114773939/560eb12f-c248-4888-b40b-712aec6ed96a">
</p>

