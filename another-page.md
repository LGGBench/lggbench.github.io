---
layout: default
title: Evaluation Results
description: Evaluating graph generation methodologies.
---

# Graph Datasets

| Dataset | Network Type | \#Nodes | \#Edges | \#Features | \#Classes | Source |
|:---:|:---:|:---:|:---:|:---:|:---:|---|
| Amazon-Photo | Item | 7,650 | 238,162 | 745 | 8 | [Link](https://arxiv.org/abs/1811.05868) |
| Amazon-Computers | Item | 13,752 | 491,722 | 767 | 10 | [Link](https://arxiv.org/abs/1811.05868) |
| Pubmed | Citation | 19,717 | 44,338 | 500 | 3 | [Link](https://github.com/tkipf/gcn) |
| T-Finance | Social | 39,357 | 21,222,543 | 10 | 2 | [Link](https://github.com/squareRoot3/Rethinking-Anomaly-Detection) |
| Flickr | Item | 89,250 | 449,878 | 500 | 7 | [Link](https://github.com/GraphSAINT/GraphSAINT) |
| Ogbn-arxiv | Citation | 169,343 | 1,157,799 | 128 | 40 | [Link](https://ogb.stanford.edu/docs/nodeprop/#ogbn-arxiv) |
| Bitcoin | Item | 203,769 | 234,355 | 165 | 2 | [Link](https://www.kaggle.com/datasets/ellipticco/elliptic-data-set) |
| IMDB | Item | 11,616 | 17,106 | 3,066 | 3 | [Link](https://github.com/cynricfu/MAGNN) |
| Amazon-Fraud | Social | 11,944 | 4,398,392 | 25 | 2 | [Link](https://github.com/squareRoot3/Rethinking-Anomaly-Detection) |
| Yelp-Fraud | Item | 45,954 | 3,846,979 | 32 | 2 | [Link](https://github.com/squareRoot3/Rethinking-Anomaly-Detection) |

We adopt the widely used node classification datasets in different domains and provide statistics.

# Fidelity

|  | Deviation of Graph-level Statistics (↓) |  |  |  |  |  | Node-level MMD (↓) |  |
|:---:|:---:|:---:|:---:|:---:|:---:|:---:|:---:|:---:|
| Generator | PLE | Ent | Homo\% | CC | BC | CF | CC | CF |
| G.RNN | 0.22 | 0.0233 | 48.53 | 0.2641 | 0.0030 | 0.1209 | 0.1339 | 0.0657 |
| G.VAE | 0.21 | 0.0143 | 56.77 | 0.4269 | 0.0013 | 0.4112 | 0.3320 | 0.1307 |
| G.GMG | 0.23 | 0.0113 | 58.99 | 0.4634 | 0.0011 | 0.0110 | 0.3892 | 0.1954 |
| CGT | 2.96 | 0.3452 | 34.58 | 0.0043 | 0.0001 | 0.0155 | 0.0000 | 0.0022 |
| G.Maker | 2.07 | 0.0983 | 34.51 | 0.0054 | 0.0001 | 0.3549 | 0.0001 | 0.0063 |
| SBM | 0.34 | 0.0032 | 49.05 | 0.3634 | 0.0019 | 0.0016 | 0.2501 | 0.0223 |
| GCond | 0.04 | 0.0164 | 46.06 | 0.2203 | 0.0036 | 0.6228 | 0.0892 | 0.0568 |
| DosCond | 2.18 | 0.1358 | 34.48 | 0.0028 | 0.0000 | 0.0878 | 0.0000 | 0.0065 |
| Coarsen | 0.08 | 0.0002 | 45.06 | 0.1579 | 0.0028 | 0.0066 | 0.1289 | 0.0709 |
| Herding | 2.05 | 0.3957 | 7.72 | 0.0027 | 0.0000 | 0.2516 | 0.0000 | 0.0066 |

Graph fidelity metrics for Ogbn-arxiv. The deviation of graph-level statistics is computed by taking the absolute difference of the graph statistics. The maximum mean discrepancy (MMD) measures the distance between two node-level distributions. (Deg: mean degree. \#CC: number of maximally connected components. LCC: size of the largest connected component. PLE: power-law exponent of degree distribution. Ent: relative edge distribution entropy. Homo\%: edge homophily ratio in percentage. CC: closeness centrality. BC: betweenness centrality. CF: clustering coefficient.)

# Utility

| Generator | Pearson (↑) | Spearman (↑) | Transfer Accuracy\% (↑) |
|:---:|:---:|:---:|:---:|
| GraphRNN | 0.7880 | 0.8286 | 43.2±0.3 |
| GraphVAE | 0.5683 | 0.6000 | 40.2±0.7 |
| GraphGMG | 0.7415 | 0.6571 | 42.2±0.5 |
| CGT | 0.9718 | 0.7537 | 56.3±0.4 |
| GraphMaker | 0.8668 | 0.8857 | 59.3±0.1 |
| SBM | 0.3996 | 0.6000 | 46.6±0.1 |
| GCond | 0.8738 | 0.8659 | 59.2±0.4 |
| DosCond | 0.9654 | 0.9429 | 60.9±0.3 |
| Coarsen | 0.2545 | 0.0137 | 27.4±1.7 |
| Herding | 0.8546 | 0.8857 | 58.4±0.1 |

Graph utility metrics for Ogbn-arxiv. Pearson and Spearman correlations are calculated on the accuracy scores across an array of graph models separately trained on two graphs. Transfer Accuracy is evaluated by first training a GCN model on the synthetic graph, then report the accuracy of the trained model on the target graph.

# Scalability

| Generator \ VRAM (GB) \ Generation Size | 1,000 | 5,500 | 10,000 | 100,000 |
|:---:|:---:|:---:|:---:|:---:|
| GraphRNN | 2.8 | 2.8 | 2.8 | 2.8 |
| GraphVAE | 3.5 | 3.5 | 3.5 | 3.5 |
| GraphGMG | 5.1 | 5.1 | 5.1 | 5.1 |
| CGT | 1.4 | 1.4 | 1.4 | 1.4 |
| GraphMaker | 2.6 | 5.9 | 12.7 | OOM |
| SBM | 0.5 | 0.5 | 0.5 | 0.6 |
| GCond | 5.0 | OOM | OOM | OOM |
| DosCond | 1.2 | 2.2 | 5.6 | OOM |
| Coarsen | 0.0 | 0.0 | 0.0 | 0.0 |
| Herding | 1.6 | 1.6 | 1.6 | 1.6 |

Scability evaluation. GPU memory usage (GB) of different graph generation methods when generating different graph sizes. OOM indicates an out-of-memory error on a single V100-SXM2-32GB GPU. 

# Privacy

| Generator | Attribute MSE (↑) | Edge AUC (↓) |
|:---:|:---:|:---:|
| GraphRNN | 1.6517 | 0.7321 |
| GraphVAE | 5.7220 | 0.6315 |
| GraphGMG | 5.8524 | 0.6944 |
| CGT | 0.8122 | 0.7315 |
| GraphMaker | 0.7992 | 0.7661 |
| SBM | 1.1321 | 0.6035 |
| GCond | 1.5670 | 0.6662 |
| DosCond | 0.7978 | 0.7709 |
| Coarsen | 1.0595 | 0.6137 |
| Herding | 0.8088 | 0.7617 |

Privacy evaluation. Attribute MSE: train an attribute inference attack model on the synthetic graph, then evaluate the model on the target graph using mean squared error. Edge AUC: train and evaluate an edge membership inference attack model by measuring the area under the ROC-curve. An unsuccessful attack yields high MSE and low AUC, indicating a higher privacy level of the synthetic graph.
