---
layout: default
title: Results
description: Evaluating graph generation methodologies.
---

# Graph Datasets

| Type | Dataset | Net. Type | \#Nodes | \#Edges | \#Feats. | \#Cls. |
|:---:|:---:|:---:|:---:|:---:|:---:|:---:|
| Homo. | Amazon-Photo \citep{shchur2018pitfalls} | Item | 7,650 | 238,162 | 745 | 8 |
|  | Amazon-Computers \citep{shchur2018pitfalls} | Item | 13,752 | 491,722 | 767 | 10 |
|  | Pubmed \citep{kipf2016semi} | Citation | 19,717 | 44,338 | 500 | 3 |
|  | T-Finance \citep{tang2022rethinking} | Social | 39,357 | 21,222,543 | 10 | 2 |
|  | Flickr \citep{zeng2019graphsaint} | Item | 89,250 | 449,878 | 500 | 7 |
|  | Ogbn-arxiv \citep{hu2020open} | Citation | 169,343 | 1,157,799 | 128 | 40 |
|  | Bitcoin \citep{weber2019anti} | Item | 203,769 | 234,355 | 165 | 2 |
| Hetero. | IMDB \citep{fu2020magnn} | Item | 11,616 | 17,106 | 3,066 | 3 |
|  | Amazon-Fraud \citep{tang2022rethinking} | Social | 11,944 | 4,398,392 | 25 | 2 |
|  | Yelp-Fraud \citep{tang2022rethinking} | Item | 45,954 | 3,846,979 | 32 | 2 |

# Fidelity

|  | Deviation of Graph-level Statistics ($\downarrow$) |  |  |  |  |  | Node-level MMD ($\downarrow$) |  |
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

| Category | Generator | Pearson ($\uparrow$) | Spearman ($\uparrow$) | TransferAcc\% ($\uparrow$) | RefAcc\% |
|:---:|:---:|:---:|:---:|:---:|:---:|
| Set Gen. | GraphRNN \citep{you2018graphrnn} | 0.7880 | 0.8286 | \ms{43.2}{0.3} | \ms{71.4}{0.1} |
|  | GraphVAE \citep{simonovsky2018graphvae} | 0.5683 | 0.6000 | \ms{40.2}{0.7} |  |
|  | GraphGMG \citep{li2018learning} | 0.7415 | 0.6571 | \ms{42.2}{0.5} |  |
|  | CGT \citep{yoon2023graph} | 0.9718 | 0.7537 | \ms{56.3}{0.4} |  |
| Scalable | GraphMaker \citep{li2023graphmaker} | 0.8668 | 0.8857 | \ms{59.3}{0.1} |  |
|  | SBM \citep{holland1983stochastic} | 0.3996 | 0.6000 | \ms{46.6}{0.1} |  |
| Reduction | GCond \citep{jin2021graph} | 0.8738 | 0.8659 | \ms{59.2}{0.4} |  |
|  | DosCond \citep{jin2022condensing} | 0.9654 | 0.9429 | \ms{\textbf{60.9}}{0.3} |  |
|  | Coarsen \citep{huang2021scaling} | 0.2545 | 0.0137 | \ms{27.4}{1.7} |  |
|  | Herding \citep{welling2009herding} | 0.8546 | 0.8857 | \ms{58.4}{0.1} |  |

Graph utility metrics for Ogbn-arxiv. Pearson and Spearman correlations are calculated on the accuracy scores across an array of graph models separately trained on two graphs. TransferAcc is evaluated by first training a GCN model on the synthetic graph, then report the accuracy of the trained model on the target graph. A referential accuracy (RefAcc) is given by training and evaluating the same GCN model on the target graph.

# Scalability

|  |  | VRAM (GB) at synthetic sizes ($N'$) |  |  |  |
|---|:---:|:---:|:---:|:---:|:---:|
| Category | Generator | 1,000 | 5,500 | 10,000 | 100,000 |
| Set Generation | GraphRNN | 2.8 | 2.8 | 2.8 | 2.8 |
|  | GraphVAE | 3.5 | 3.5 | 3.5 | 3.5 |
|  | GraphGMG | 5.1 | 5.1 | 5.1 | 5.1 |
|  | CGT | 1.4 | 1.4 | 1.4 | 1.4 |
| Scalable | GraphMaker | 2.6 | 5.9 | 12.7 | OOM |
|  | SBM | 0.5 | 0.5 | 0.5 | 0.6 |
| Reduction | GCond | 5.0 | OOM | OOM | OOM |
|  | DosCond | 1.2 | 2.2 | 5.6 | OOM |
|  | Coarsen | 0.0 | 0.0 | 0.0 | 0.0 |
|  | Herding | 1.6 | 1.6 | 1.6 | 1.6 |

Scability evaluation. GPU memory usage (GB) of different graph generation methods when generating different graph sizes. OOM indicates an out-of-memory error on a single V100-SXM2-32GB GPU. Graph set generation methods produce graph sets containing small graphs, which are then combined into a single large graph, incurring a constant memory usage. Methods that directly learn a single large graph, such as GraphMaker, GCond, and DosCond, cannot scale to large synthetic sizes due to the large synthetic graph structure.

# Privacy

| Category | Generator | Attr MSE ($\uparrow$) | Attr Ref | Edge AUC ($\downarrow$) | Edge Ref |
|:---:|:---:|:---:|:---:|:---:|:---:|
| Set Gen. | GraphRNN | 1.6517 | 0.7458 | 0.7321 | 0.8840 |
|  | GraphVAE | 5.7220 |  | 0.6315 |  |
|  | GraphGMG | 5.8524 |  | 0.6944 |  |
|  | CGT | 0.8122 |  | 0.7315 |  |
| Scalable | GraphMaker | 0.7992 |  | 0.7661 |  |
|  | SBM | 1.1321 |  | 0.6035 |  |
| Reduction | GCond | 1.5670 |  | 0.6662 |  |
|  | DosCond | 0.7978 |  | 0.7709 |  |
|  | Coarsen | 1.0595 |  | 0.6137 |  |
|  | Herding | 0.8088 |  | 0.7617 |  |

Privacy evaluation. Attr MSE: train an attribute inference attack model on the synthetic graph, then evaluate the model on the target graph using mean squared error. Edge AUC: train and evaluate an edge membership inference attack model by measuring the area under the ROC-curve. Ref: The reference metrics are given by training and evaluating the attack model directly on the target graph, which yield the best attack performances. An unsuccessful attack yields high MSE and low AUC, indicating a higher privacy level of the synthetic graph.
