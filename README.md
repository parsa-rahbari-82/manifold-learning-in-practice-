# Manifold Learning in Practice

## Project Structure

### Part 1: Mapping Iranian Cities with Isomap

**Objective:**  
Reconstruct a 2D map of 31 Iranian cities using a distance matrix and the Isomap algorithm.

**Data:**  
- `distances.csv`: Euclidean distance matrix between 31 cities.

**Steps:**  
1. **Neighborhood Graph Construction:**  
   - For each city, find the 4 nearest neighbors.  
   - Build a weighted graph where edge weights are Euclidean distances.

2. **Geodesic Distance Estimation:**  
   - Apply the **Floyd-Warshall algorithm** to compute shortest paths between all city pairs, approximating manifold distances.

3. **2D Embedding via MDS:**  
   - Use **Classical MDS** to extract 2D coordinates from the geodesic distance matrix.

4. **Rotation for Visualization:**  
   - Apply a rotation (100° for our implementation, −50° for Scikit-learn) to better align the output with the actual map of Iran.

---

### Part 2: Dimensionality Reduction on MNIST

**Objective:**  
Compare **PCA** and **t-SNE** in reducing the dimensionality of the MNIST dataset and evaluate the results using **Trustworthiness**.

**Data:**  
- MNIST (28×28 grayscale images of handwritten digits, flattened to 784-dim vectors).

**Techniques:**
- **PCA:** Linear method preserving variance.
- **t-SNE:** Nonlinear method preserving local neighborhoods, better suited for visualizing clusters.

**Metric – Trustworthiness:**  
Measures how well local neighborhoods are preserved from high-dimensional to low-dimensional space.

| Method | Trustworthiness |
|--------|------------------|
| PCA    | 0.737            |
| t-SNE  | 0.980            |

**Conclusion:**  
- **t-SNE** offers superior cluster separation and neighborhood preservation due to its nonlinear nature.  
- **PCA** is simpler but often overlaps clusters.  
- The `perplexity` parameter in t-SNE significantly affects the outcome — careful tuning is important for minimizing **KL divergence** and improving visualization.

---

