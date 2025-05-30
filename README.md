# Smart Route Optimizer

> A Colab-friendly end-to-end demo of last-mile delivery routing with OR-Tools, Dask, K-Means clustering, and ONNX quantization.

## Table of Contents

- [Features](#features)  
- [Getting Started](#getting-started)  
  - [Prerequisites](#prerequisites)  
  - [Installation](#installation)  
- [Usage](#usage)  
- [Notebook Outline](#notebook-outline)  
- [Project Structure](#project-structure)  
- [Contributing](#contributing)  
- [License](#license)  

## Features

- **Central VRP**: Solve the Vehicle Routing Problem (VRP) using Google OR-Tools.  
- **Network-Aware VRP**: Simulate high latency, split the problem, and recombine.  
- **Distributed VRP**: Parallelize subproblems across a local Dask cluster.  
- **Cluster-Seeded VRP**: Pre-cluster locations via K-Means to reduce solver search space.  
- **ETA Prediction**: Train a toy MLP in PyTorch, export to ONNX, apply INT8 quantization, and benchmark inference.  
- **Interactive Visuals**: Route maps, cluster scatter plots, and performance bar charts—all in Colab.

## Getting Started

### Prerequisites

- Python 3.7+  
- Colab or Jupyter Notebook environment  

### Installation

Install dependencies in Colab or your local virtual environment:

\`\`\`bash
pip install ortools matplotlib numpy dask[distributed] torch onnxruntime onnx scikit-learn
\`\`\`

## Usage

1. **Clone the repo**  
   ```
   git clone https://github.com/atharvayeola/Smart-Route-Optimizer.git
   cd smart-route-optimizer
   ```
2. **Open the notebook**  
   - In Colab: upload \`SmartRouteOptimizer.ipynb\`  
   - Locally:  
     ```
     jupyter notebook SmartRouteOptimizer.ipynb
     ```
3. **Run all cells**  
   Follow the annotated sections to generate data, cluster points, solve VRPs, train & quantize the ETA model, and visualize results.

## Notebook Outline

1. **Overview & Objectives**  
2. **Setup & Imports**  
3. **Data Generation** (\`generate_locations\`, \`compute_euclidean_distance_matrix\`)  
4. **ML Pre-Routing** (K-Means clustering)  
5. **VRP Solvers**  
   - \`solve_vrp\` (central)  
   - \`solve_vrp_with_network\` (edge-aware)  
   - \`solve_vrp_distributed\` (Dask)  
   - **Cluster-Seeded VRP**  
6. **ETA Model**  
   - Train MLP → ONNX  
   - Quantize to INT8  
   - Measure inference latency  
7. **Visualization** (route plots & cluster scatter)  
8. **Results Summary**  

## Project Structure

```
.
├── README.md
├── requirements.txt
├── results/
    └── vrp_clusters.png
    └── network-sim_vrp.png
    └── distributed_vrp.png
    └── central_vrp.png
    └── cluster-seeded_vrp.png
└── SmartRouteOptimizer.ipynb
```


