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

<p align="center">
<img width="730" alt="section1_replicated_graphic" src="https://github.com/zroe1/toy_models_of_superposition/assets/114773939/1d968aee-ec92-4abf-81bf-4eb9b9bfe894">  
</p>

Note that the bold lines display the length of the vector while the dotted ones merely show what the vector would look like if it was extended. The patern is the same:
if there is no sparsity in the input, the model encodes the two most important features orthogonally. When you introduce sparsity, you begin to see superposition.

### Demonstrating Superposition:

This section of my replication explores both a linear model defined by $W^TWx + b$ and a model with an ReLU activation function defined by ReLU($W^TWx + b$).
Each model is trained to reconstruct it's input.

#### Models With Orthogonal Feature Representation (No Superposition):

In the graphic below, the grids on the top represent $W^TW$ with the orange squares representing positive numbers in this matrix. The bar graphs on the bottom
show the extent to which the model represents each input internally. The models studied below have 5 dimensions and were trained with 0 sparsity. In these training
conditions, the toy models represent 5 features: one for each dimension in the model. The features are mapped orthogonally and are therefore not in superposition.

<p align="center">
<img width="330" alt="relu_linear_0_sparsity" src="https://github.com/zroe1/toy_models_of_superposition/assets/114773939/403f2eec-4773-479b-9a0f-6419fd464387">
</p>

#### Models With Sparsity:

Increasing the sparsity of the ReLU model (ReLU($W^TWx + b$)) results in the model abandoning orthogonal representations of features. The grid representations of $W^TW$ begin to
become much less clean. The bar chart at the bottom of the figures show that under these conditions, the model maps more features than it has dimensions. Bars
that are colored blue represent features that are not represented orthogonally to others in weight matrix $W$. These features are therefore in "superposition."

<p align="center">
<img width="600" alt="sparsity_superposition1" src="https://github.com/zroe1/toy_models_of_superposition/assets/114773939/827eeba9-bc02-47a8-b8eb-bde6700adaf8">
</p>

As one continues to increase the sparsity of the ReLU model, it ceases to represent any features orthogonally. Not that all the bar charts in the bottom of the
figure below are colored blue to represent that the model is representing them in superposition. As a result, the grids representing $W^TW$ are far more noisy
than in the examples above.

<p align="center">
<img width="600" alt="sparsity_superposition2" src="https://github.com/zroe1/toy_models_of_superposition/assets/114773939/560eb12f-c248-4888-b40b-712aec6ed96a">
</p>

### Phase changes:

The authors of <i>Toy Models of Superposition</i> claim that transitions from different interal structures within a model can be thought of as phase changes.
The graphic below shows three phase diagrams. Note that I found that when training a group of ReLU models, they do not align with the theoretical phase diagram.
The overall trend and shape, however is somewhat consistent. I also trained a group of linear models and found similar results despite the fact that, in theory,
linear models should not represent any features in superpostion. This all illustrates that even if a model "should" do something, it may not unless the conditions
are highly favorable.

This part of the paper was perhaps the most difficult. It involved training 1,000,000 one-neuron ReLU models and 100,000 one-neuron linear models.

<p align="center">
<img width="765" alt="phase_changes_replication" src="https://github.com/zroe1/toy_models_of_superposition/assets/114773939/654ea739-4c54-45aa-bb2b-c7f6ffd2e263">
</p>

## Conclusions

This replication demostrates that it is possible for models to represent features in superposition. It also shows that phenomenon of superposition is somewhat 
predictable. For example, by increasing the sparsity of a model's input, that model is more likely to represent the input in superposition.

With that being said, there are some serious limitations to thinking about neural networks in this way. In all the examples in this replication, 
the result was highly dependent on the exact training conditions such as learning rate and batch size. Thus, I beleive that it is wise to be cautious when making
broad claims about models such as "model x will represent less information in superposition than model y because model x is larger." The truth is that there
are a number of important factors that influence weather or not a model with represent information orthogonally or in superposition. 
