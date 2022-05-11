# star-ensembling

This repository contains the code to reproduce the experiments in the paper

[Star algorithm for NN ensembling](https://google.com)

by Zinchenko Sergei and Dmitriy Lishudi

Please cite our work if you find our results useful in your research:

## Overview

In short, the procedure we proposed can be described as follows: we run  𝑑  independent learning processes of neural networks, obtaining empirical risk minimizers (black box), freeze their weights, after that we initialize a new model and connect all  𝑑+1  models with a layer of convex coefficients, after that we start the process of optimizing all non-frozen parameters (red elemenents). This whole procedure can be viewed as a search for an empirical minimizer in all possible  𝑑 -dimensional simplices spanned by  𝑑 -minimizers and a class of neural networks. As is known, the minimization of the empirical risk with respect to the convex hull is not optimal in the same way as with respect to the original class of functions. Our method, however, minimizes over some set intermediate between the original class of functions and its convex hull, allowing us to combine the advantages of model ensembling and the star procedure.

<img width="542" alt="image" src="https://user-images.githubusercontent.com/58306690/167785574-9ebd9b2b-0c98-4801-9e08-cc648ac7f080.png">


The algorithm proposed by us can be perceived as a new way of training neural networks of block architecture and as a new way of model aggregation. See the article for details.

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

(results after 25 epoch by using parameter d = 5)

These scores are 10-11 according to the dataset FASHION MNIST in the [ledearbord](https://paperswithcode.com/sota/image-classification-on-fashion-mnist).
