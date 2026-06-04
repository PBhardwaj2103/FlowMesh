# 📦 FlowMesh — Smart Supply Distribution Optimizer

<p align="center">
  <img src="https://img.shields.io/badge/Language-C%2B%2B-blue?style=for-the-badge&logo=cplusplus" />
  <img src="https://img.shields.io/badge/Visualization-SFML-purple?style=for-the-badge" />
  <img src="https://img.shields.io/badge/Algorithm-Min--Cost%20Max--Flow-orange?style=for-the-badge" />
  <img src="https://img.shields.io/badge/Status-Completed-brightgreen?style=for-the-badge" />
</p>

> A minimum-cost maximum-flow based supply distribution optimizer that allocates limited resources across demand centres under capacity constraints, with a real-time SFML simulation interface.

---

## 📌 Overview

FlowMesh models a supply chain as a directed flow network and solves the **minimum-cost maximum-flow (MCMF)** problem to find the globally optimal allocation of supplies from warehouses to demand centres. A greedy post-optimisation pass further reduces residual cost, and an SFML-powered simulation visualises the entire distribution process in real time.

---

## ✨ Features

- 🔄 **Min-cost max-flow engine** — successive shortest paths with heap-based Dijkstra (SPFA variant)
- 💰 **Optimal allocation** — guarantees minimum total cost while maximising supply throughput
- 🧠 **Greedy refinement** — local-search post-processing to squeeze out residual cost
- 🏭 **Capacity-constrained** — respects per-edge and per-node limits across the network
- 🎮 **SFML simulation** — real-time visualisation of warehouses, routes, flow values, and bottlenecks
- ⚙️ **Text-based graph input** — configure any supply network topology via a simple input file

---

## 🛠️ Tech Stack

| Category | Technology |
|---|---|
| Language | C++17 |
| Visualisation | SFML 2.6 |
| Algorithm | Min-Cost Max-Flow (Successive Shortest Paths) |
| Data Structures | Priority Queue (Min-Heap), Adjacency List |
| Build System | CMake |

---

## 🚀 Getting Started

### Prerequisites

```bash
# Install SFML and CMake
sudo apt install libsfml-dev cmake g++
```

### Build & Run

```bash
git clone https://github.com/priyanshu-bhardwaj/FlowMesh.git
cd FlowMesh
mkdir build && cd build
cmake ..
make
./FlowMesh --input ../data/network.txt
```

### Input Format

```
# network.txt
# <num_nodes> <num_edges>
6 8
# <from> <to> <capacity> <cost>
0 1 100 2
0 2 80  3
1 3 60  1
...
```

---

## 📁 Project Structure

```
FlowMesh/
├── src/
│   ├── main.cpp
│   ├── graph.cpp / graph.h         # Flow network model
│   ├── mcmf.cpp / mcmf.h           # Min-cost max-flow solver
│   ├── greedy.cpp / greedy.h       # Post-optimisation pass
│   └── visualizer.cpp / visualizer.h # SFML simulation
├── data/
│   └── network.txt                 # Sample network
├── CMakeLists.txt
└── README.md
```

---

## 🧠 Algorithm Details

### Min-Cost Max-Flow
Uses the **Successive Shortest Paths** algorithm: repeatedly find the shortest (minimum cost) augmenting path using Dijkstra with Johnson's re-weighting (to handle zero-cost edges), then push flow along it. Runs in **O(V · E · log V)** per augmentation.

### Greedy Refinement
After the MCMF solution, a greedy local-search pass identifies flow cycles with negative cost and cancels them, reducing total cost without changing the flow value.

### Bottleneck Detection
Edges where flow equals capacity are flagged as bottlenecks and highlighted in the SFML visualisation, making capacity constraints immediately visible.

---

## 📸 Screenshots

> *(Add SFML simulation screenshots here)*

---

## 👤 Author

**Priyanshu Bhardwaj**
B.Tech Mechanical Engineering — IIT Guwahati
📧 p.bhardwaj@iitg.ac.in | bhardwajpriyanshu2102@gmail.com
🔗 [LinkedIn](https://linkedin.com/in/priyanshu-bhardwaj-4bb652213)

---

## 📄 License

This project is open-source and available under the [MIT License](LICENSE).
