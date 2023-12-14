# Toy Models of Superposition
This repository is replication of the paper Toy Models of Superposition conducted in association with Anthropic and Harvard in 2022.

## Summary

I replicated the paper Toy Models of Superposition section by section. An indepth report of my findings can be found in FINDINGS.pfd. For a breif overview,
I have written up my findings in this markdown file.

### Introduction:

In the introduction of the original paper, the provide this interesting graphic, illustrating superposition within a model. They graph each column of
a model's wieghts as a vector and display how the model changes as you vary sparsity.

<img width="720" alt="section1_anthropic_graphic_" src="https://github.com/zroe1/toy_models_of_superposition/assets/114773939/529cced1-05e8-4eef-ad0b-1b4d9f6cb993">  

I was able to get the same result using the information from the paper:

<img width="730" alt="section1_replicated_graphic" src="https://github.com/zroe1/toy_models_of_superposition/assets/114773939/1d968aee-ec92-4abf-81bf-4eb9b9bfe894">  

Note that the bold lines display the length of the vector while the dotted ones merely show what the vector would look like if it was extended. The patern is the same:
if there is no sparsity in the input, the model encodes the two most important features orthogonally. When you introduce sparsity, you begin to see superposition.


