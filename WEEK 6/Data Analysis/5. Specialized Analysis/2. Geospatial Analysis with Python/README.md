# Geospatial Analysis with Python (https://www.youtube.com/watch?v=m_qayAJt-yE)

Geospatial analysis helps us analyze data based on **location and distance**. It is widely used for decision-making such as:

* Opening new stores
* Choosing business locations
* Planning services based on proximity

In this tutorial, we analyze **Starbucks and McDonald's store locations in New York** to support location-based decisions.

---

## Objective

The goal is to:

* Analyze store locations using coordinates
* Compute distances from a reference point
* Visualize store distribution on a map
* Identify optimal locations for new stores

---

## Data Used

The dataset contains:

Variable	Description
Latitude	Store latitude
Longitude	Store longitude
Store	Type (Starbucks / McDonald's)
Address	Store location details

---

## Libraries Used

* pandas → Data handling
* numpy → Numerical operations
* folium → Map visualization
* geopy → Distance calculation

---

## Steps in Geospatial Analysis

---

### 1. Import Libraries and Load Data

Load the dataset containing store coordinates.

* Read CSV file
* Inspect columns (latitude, longitude, store type)

---

### 2. Create Coordinates Column

Combine latitude and longitude into a single column:

👉 Helps simplify distance calculations

---

### 3. Define Reference Location

We use:

👉 **Empire State Building (New York)**

This acts as the **central reference point**.

---

### 4. Distance Calculation

Compute distance between:

* Store location
* Reference point

Using **geopy distance function**

---

### Example Insight

* Distance of each store from Empire State Building
* Helps understand spatial distribution

---

### 5. Data Visualization (Map)

Use **folium** to create an interactive map.

#### Map Features:

* Center → Empire State Building
* Zoom level → Adjustable
* Markers:

  * Green → Starbucks
  * Blue → McDonald's

---

### Example Observations

* More Starbucks stores than McDonald's
* Starbucks clustered in lower Manhattan
* McDonald's more spread toward upper regions

---

### 6. Store Density Analysis

Analyze number of stores within a given radius.

Example:

* Radius = 10 km

Find:

* Stores beyond 10 km
* Store concentration in different regions

---

### 7. Proximity Analysis

Identify:

* Closest store
* Farthest store

---

### Example Results

Store Type	Closest Distance	Farthest Distance
Starbucks	~37 meters	~13.9 km
McDonald's	~300 meters	~14 km

---

### Interpretation

* High density near central locations
* Some areas have fewer stores
* Distance variation indicates expansion opportunities

---

## Visualization Insight

Maps help identify:

* Clusters of stores
* Coverage gaps
* Competitive positioning

---

## Decision Making

Using this analysis, businesses can decide:

* Where to open new stores
* Whether an area is saturated
* How far customers must travel

---

### Example Insight

Near Empire State Building:

* High store density
* Strong competition
* New store may not be needed
