# star-ensembling

This repository contains the code to reproduce the experiments in the paper

[Star algorithm for NN ensembling](https://google.com)

by Zinchenko Sergei and Dmitriy Lishudi

Please cite our work if you find our results useful in your research:

## Overview

## Dependencies

```
torch==1.10.2
torchvision==0.11.3
numpy==1.20.3
pandas==1.4.1
sklearn==1.0.2
```


## Data downloading

BOSTON HOUSE PRICING downloading is handled by `sklearn.datasets`, FMNIST is hadled by `torch.torchvision`.


## File structure

```
+-- tables/
|   +-- BOSTON/ (tables of results for BOSTON HOUSE PRICING)
|   +-- FMNIST/ (tables of results for FASHION MNIST)
+-- notebooks (jupyter notebooks used to generate tables) 
```

