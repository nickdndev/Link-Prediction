# Link-Prediction
The dataset contains publications that is described by a binary vector indicating the presence of the corresponding word. The dateset can be represented as a graph where nodes are publications and edges are citations. For simplicity, let us say that this graph is undirected. The most similar pairs of nodes which are not connected was selected in the same amount as existent edges. The used proximity metric is cosine similarity, which is a normalized dot product of adjacency matrix. Let us denote existent edges by label 1 and additionally selected pairs by label 0.

The dataset is represented by 3 files:
* features.txt contains description of the papers in the format:
    * `<node id> <3703 unique one-hot encoded words>`
* labeled_edges.txt contains labeled pairs of nodes in the format:
    * `<node id> <node id> <label>`
* unlabeled_edges.txt contains unlabeled pairs of nodes in the format:
    * `<node id> <node id>`

Your task is to predict labels for unlabeled pairs of nodes: 0 — disconnected, 1 — connected.

Hints:
* Consider the features only. Transform the sparse feature matrix into low-dimensional dense embeddings. Fit a classificator to predict links.
* Consider the structure only. Create a graph that consists of edges with labels 1. Train any structural embedding model to obtain node embeddings. Fit a classificator to predict links.
* Consider the both structure and features. Create a graph that consists of edges with labels 0, labels 1 and no labels. Train any GNN model to obtain node embeddings. Minimize the link prediction error by gradient descent.
* Concatenate (multiply, sum up, average) pairs of node embeddings to obtain edge embeddings.
* You can combine embeddings from heterogeneous models.
