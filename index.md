---
layout: default
---

# Introduction

![LGGBench](LGGBench.png)

LGGBench is a comprehensive benchmark designed to evaluate large graph generation methods crucial for secure and effective data sharing. It integrates a variety of large graph datasets, advanced graph generation techniques, and thorough evaluation schemes to assess the quality of the shared synthetic graphs. By comparing existing methods through extensive experiments, LGGBench highlights their strengths and limitations, providing a holistic approach to improve graph generation techniques. This benchmark facilitates safer and more effective data sharing practices, essential for collaborative research in domains such as social networks and molecular biology. LGGBench focuses on four key aspects: fidelity, utility, privacy, and scalability, which are further introduced below.

## Fidelity

Fidelity evaluation focuses on how accurately synthetic graphs replicate the statistical properties of the original graphs. This involves calculating graph-level statistics like mean degree, power-law exponent, and clustering coefficient, as well as node-level statistics such as degree, closeness centrality, and betweenness centrality. By comparing these metrics between the target and synthetic graphs, researchers can quantify the structural and feature similarity, ensuring the synthetic graphs maintain essential characteristics of the target graphs.

## Utility

Utility evaluation assesses whether synthetic graphs can effectively replace original graphs for specific tasks. This involves training models on synthetic graphs and evaluating their performance on target graphs. Metrics such as model transfer accuracy and performance correlation (e.g., Pearson and Spearman correlation coefficients) are used to measure how well a model trained on synthetic data performs on real data. This ensures that synthetic graphs not only resemble real graphs statistically but also retain the practical utility for tasks like node classification and link prediction.

## Scalability

Scalability evaluation examines the efficiency of graph generation methods in handling large datasets. It focuses on the time and memory consumption during the generation process, assessing whether the methods can generate large-scale graphs without excessive computational resources. This evaluation is critical for ensuring that graph generation methods are practical for real-world applications where data size can be substantial. Scalability metrics include memory usage and generation time, which are correlated with the size of the synthetic graphs.

## Privacy

Privacy evaluation measures the extent to which synthetic graphs protect against inference attacks. This involves assessing the vulnerability of synthetic graphs to attribute and edge membership inference attacks, where attackers try to infer sensitive information from the graph structure and attributes. Metrics like mean squared error of predicted node attributes and AUC of edge prediction are used to quantify privacy protection. Higher attribute prediction error and lower edge prediction AUC values indicate better privacy, demonstrating that synthetic graphs can effectively mask sensitive information while still being useful for analysis.
