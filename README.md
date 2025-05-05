# Adaptive-Kernel-Based-Approximation-for-Efficient-LLM-Reranking-in-RAG-Pipelines
This repository implements the approach described in "Adaptive Kernel-Based Approximation for Efficient LLM Reranking in RAG Pipelines" by Thomas Bordino (Columbia University). The technique uses Nyström kernel approximation to significantly reduce computational costs during the reranking phase of RAG systems while preserving ranking quality.
## Overview
Retrieval-Augmented Generation (RAG) systems enhance Large Language Models (LLMs) by providing relevant external knowledge during inference. However, as these systems scale to handle larger document collections and higher query volumes, the reranking stage becomes a computational bottleneck.
This implementation demonstrates how to:
- Approximate reranker scoring functions using Nyström kernel approximation techniques
- Project documents and queries onto a low-dimensional landmark space
- Reduce computational complexity from O(nd) to O(md), where n is the number of documents, d is the embedding dimension, and m ≪ n is the number of landmarks
- Maintain high ranking correlation with exact computation results
## Key Features
- **Three landmark selection strategies**:
  - Uniform random sampling (baseline)
  - K-means clustering (better overall ranking preservation)
  - Determinantal point processes (better top-result preservation)
- **Comprehensive evaluation metrics**:
  - Computational efficiency (ranking speedup)
  - Spearman rank correlation
  - Top-k overlap
  - Mean absolute difference in similarity scores
  - Top-1 match ratio
- **Theoretical foundations**:
  - Mathematical framework with error bounds
  - Analysis of approximation quality
  - Complexity reduction analysis
## Results
Experiments on the MS MARCO dataset demonstrate:
- Up to 3.30× speedup in ranking time
- High correlation with exact computation results (up to 0.89 Spearman correlation)
- Different landmark selection strategies optimize for different quality aspects:
  - K-means better preserves overall ranking order (higher Spearman correlation)
  - DPP better maintains the most relevant documents in top positions (higher top-k overlap)

## Data Source
This implementation uses the MS MARCO (Microsoft Machine Reading Comprehension) dataset, which is a large-scale information retrieval dataset created by Microsoft. The dataset contains real-world queries from Bing search engine and human-annotated relevant passages. It serves as a widely-used benchmark for evaluating retrieval and reranking systems in research. For more information and to access the dataset, visit: https://microsoft.github.io/msmarco/
