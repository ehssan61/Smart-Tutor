# Smart-Tutor: Smart Tutor Knowledge Hub: Clustering Academic Abstracts

An interactive system that semantically clusters academic papers in data science and machine learning using unsupervised learning techniques. This project enables users—students, researchers, and independent learners—to explore thematically grouped research topics and retrieve relevant resources using natural language queries.

## Objective
To build a scalable knowledge base from scraped academic abstracts that:

- Organizes research papers into semantically coherent clusters.

- Enables semantic search and personalized content retrieval.

- Supports academic navigation through a user-friendly interface.

## Method Overview
1. Data Collection
Scraped 30,000+ papers from Google Scholar using a keyword list. Retained top 30% of papers by citation count to ensure content quality.


2. Sentence Embedding
Used SentenceTransformers (all-MiniLM-L6-v2) to generate 384-dimensional embeddings. Efficient for large-scale text embedding while maintaining semantic fidelity.

3. Dimensionality Reduction
Built a symmetric autoencoder in PyTorch to compress embeddings to 64 dimensions.Trained for 50 epochs using Adam optimizer, ReLU activation and MSE loss


4. Clustering Algorithms
Used K-Means (hard clustering) and Evaluated cluster counts using Silhouette Score (best at k = 23) and Elbow Method (best at k = 12)
. We Selected 23 clusters for finer semantic granularity.

5. Keyword Extraction
Used TF-IDF to extract top 10 keywords per cluster for interpretability.

6. Semantic Search Interface
User query → Embedded with BERT → Reduced with autoencoder. Query matched to closest cluster and top papers selected using cosine similarity. Returned top 10 papers based on semantic relevance.
