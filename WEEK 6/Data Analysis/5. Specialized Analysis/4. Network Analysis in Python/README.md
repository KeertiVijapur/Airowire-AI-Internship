# Network Analysis with Python (https://www.youtube.com/watch?v=uPL3VuRqOy4)

Network analysis helps us understand **relationships between entities** by representing them as a graph.

* Nodes → Entities (e.g., actors)
* Edges → Connections (e.g., co-acting in movies)

In this tutorial, we build a network using **IMDb movie data** to analyze relationships between actors and detect communities.

---

## Objective

The goal is to:

* Build a network of actors
* Identify clusters (communities)
* Analyze how clusters are connected
* Extract meaningful insights from relationships

---

## Dataset Used

IMDb dataset containing:

Variable	Description
Title	Movie identifier
Actors	Unique actor IDs
Region	Movie language/region
Primary Name	Actor names

---

## Libraries Used

* pandas → Data processing
* numpy → Matrix operations
* sknetwork → Network construction & clustering
* scipy → Sparse matrix representation

---

## Key Concept: Network Representation

* Each **node** = Actor
* Each **edge** = Two actors acted together

👉 Edge weight = Number of movies acted together

---

## Step 1: Data Preparation

* Filter only movies (exclude TV series)
* Load actor names
* Subset by region/language if needed

---

## Step 2: Matrix Construction

Create a matrix:

* Rows → Movies
* Columns → Actors
* Value = 1 if actor appears in movie

---

### Matrix Multiplication Trick

To find actor relationships:

👉 Multiply matrix with its transpose

Result:

* Actor–Actor matrix
* Each cell → Number of movies two actors worked together

---

## Example Insight

If:

* A(i, j) = 10

👉 Actors i and j acted together in 10 movies

---

## Step 3: Sparse Matrix Optimization

Use:

👉 CSR (Compressed Sparse Row) matrix

Benefits:

* Efficient storage
* Faster computation
* Handles large datasets

---

## Step 4: Building the Network

Convert data into a network:

* Edge list → Actor pairs
* Convert to adjacency matrix

---

## Step 5: Community Detection

Apply clustering algorithm:

👉 Louvain / clustering (via sknetwork)

Output:

* Each actor assigned to a cluster
* Clusters represent communities

---

## Example Clusters

Cluster	Description
0	Hollywood actors
1	Hindi (Bollywood) actors
2	Telugu actors
3	Regional cinema groups

---

## Step 6: Cluster Analysis

Analyze:

* Actors within each cluster
* Cross-cluster interactions

---

## Step 7: Identifying Key Connectors

Goal:

👉 Find actors connecting multiple clusters

### Criteria:

* High number of movies
* Low "in-cluster %"

---

## Example Insight

Actor	Movies	In-Cluster %
Actor A	126	18%
Actor B	61	31%

👉 These actors connect different communities

---

## Step 8: Insights from Network

* Clusters represent industry segments
* Cross-cluster actors act as bridges
* Strong relationships indicate frequent collaborations

---

## Applications

Network analysis can be used in:

* Social network analysis
* Movie/actor collaboration analysis
* Fraud detection
* Recommendation systems
* Community detection in real-world data

---

## Example Use Case

Microfinance:

* Identify connected groups
* Reduce risk in group lending
* Understand influence networks

---
