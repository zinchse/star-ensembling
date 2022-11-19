This repository contains the code to reproduce the experiments in the paper:

# "Star algorithm for NN ensembling"

by _Sergey Zinchenko_ and _Dmitry Lishudi_

> ICML DyNN workshop 2022 - [accepted](https://dynn-icml2022.github.io/papers/paper_17.pdf), NeurIPS 2022 - reject:), AISTATS - under review


## Abstract

Neural network ensembling is a common and robust way to increase model efficiency. In this paper, we propose a new neural network ensemble algorithm based on Audibert's empirical star algorithm. We provide optimal theoretical minimax bound on the excess squared risk. Additionally, we empirically study this algorithm on regression and classification tasks and compare it to most popular ensembling methods.

## Overview

In short, the procedure we proposed can be described as follows: we run  𝑑  independent learning processes of neural networks, obtaining empirical risk minimizers (black box), freeze their weights, after that we initialize a new model and connect all  𝑑+1  models with a layer of convex coefficients, after that we start the process of optimizing all non-frozen parameters (red elemenents). This whole procedure can be viewed as a search for an empirical minimizer in all possible  𝑑 -dimensional simplices spanned by  𝑑 -minimizers and a class of neural networks. As is known, the minimization of the empirical risk with respect to the convex hull is not optimal in the same way as with respect to the original class of functions. Our method, however, minimizes over some set intermediate between the original class of functions and its convex hull, allowing us to combine the advantages of model ensembling and the star procedure.

<p align="center">
  <img width="500" src="https://user-images.githubusercontent.com/58306690/202836165-d36cefe4-1dd8-4c94-bea9-0b69a07384ea.png" />
</p>


The algorithm proposed by us can be perceived as a new way of training neural networks of block architecture and as a new way of model aggregation. See the article for details.

## Dependencies

`FMNIST` & `BOSTON HOUSE PRICING`:

```
torch==1.10.2
torchvision==0.11.3
numpy==1.20.3
pandas==1.4.1
sklearn==1.0.2
```

`MILLION SONG DATASET`:

```
torch==1.11.0
numpy==1.21.6
pandas==1.3.5
CUDA=11.3.1
```


## Data downloading

`BOSTON HOUSE PRICING` downloading is handled by `sklearn.datasets`, `FMNIST` is hadled by `torch.torchvision`.

`MILLION SONG DATASET` can be downloaded from the [link](https://archive.ics.uci.edu/ml/datasets/yearpredictionmsd).


## File structure

```
+-- tables/
|   +-- BOSTON/ (tables of results for BOSTON HOUSE PRICING)
|   +-- FMNIST/ (tables of results for FASHION MNIST)
|   +-- MSD/ (tables of results for MILLION SONG DATASET)
+-- notebooks (jupyter notebooks used to generate tables and their short description in the file description.md) 
```

## Best Results


| Name                    | d | accuracy  | entropy   | TIME   |
|-------------------------|---|-----------|-----------|--------|
| Snap Star (shot wrmp)   | 5 |   0.898   |   1.152   | 2588.0 |
| Snap Star (new wrmp)    | 5 |   0.898   |   1.136   | 2369.0 |
| Snap Ensemble           | 5 |   0.902   |   0.330   | 2036.0 |
| Ensemble                | 5 |   0.918   |   0.229   | 2052.0 |
| Classic Star (no wrmp)  | 5 |   0.922   |   0.229   | 2589.0 |
| Classic Star (new wrmp) | 5 |   0.923   |   0.228   | 2239.0 |
| Big NN                  | 5 |   0.910   |   0.481   | 1560.0 |

(results after `epochs=25` by using parameter `d=5`)

These scores are 11-12 according to the dataset `FMNIST` in the [leaderboard](https://paperswithcode.com/sota/image-classification-on-fashion-mnist). Note the fact that our model takes a few minutes to learn on a laptop.

This table corresponds to the `tables/FMNIST/FMNIST_ep(25)_p(0.0)_lr(0.001).csv`
