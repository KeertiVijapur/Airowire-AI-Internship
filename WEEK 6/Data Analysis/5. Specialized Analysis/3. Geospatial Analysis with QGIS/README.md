# Geospatial Analysis with QGIS (https://www.youtube.com/watch?v=tJhehs0o-ik)

Geospatial analysis using QGIS helps us work with **geographic data, shapefiles, and maps** to support location-based decision making.

QGIS is a **free and open-source Geographic Information System (GIS)** used for:

* Creating maps
* Managing spatial data
* Performing geospatial analysis

---

## Objective

The goal of this tutorial is to:

* Work with shapefiles and geographic data
* Visualize spatial information
* Create custom shapefiles when data is unavailable
* Export data for use in tools like Google Earth

---

## What are Shapefiles and KML Files?

File Type	Description
Shapefile (.shp)	Stores geographic shapes (countries, cities, regions)
KML	File format used in Google Earth for visualization

These files contain:

* Latitude & Longitude
* Geographic boundaries
* Attributes (name, population, etc.)

---

## Step 1: Installing QGIS

* Go to Google → Search "QGIS"
* Download from official website
* Choose version based on OS (Windows / Mac / Linux)

---

## Step 2: Understanding QGIS Interface

Key Components:

Component	Description
Toolbars	Provide editing and data tools
Browser Panel	Access files from system
Layers Panel	Manage map layers

Important Tool:
👉 Digitizing Toolbar (used for creating shapes)

---

## Step 3: Downloading Shapefiles

Use free sources like:

👉 Diva-GIS

Steps:

* Search for country (e.g., Sudan)
* Download shapefile (ZIP format)
* Extract files

---

## Step 4: Loading Shapefiles

* Drag and drop shapefile into QGIS
* Multiple layers appear (admin levels)

Example:

* Country level
* State level
* District level

---

## Step 5: Exploring Attributes

Each shapefile contains an **attribute table**.

### Example Attributes

* Country name
* State name
* District name
* City name

👉 You can also include:

* Population
* Demographics
* Other business data

---

## Step 6: Visualization

### Customize Map

* Change colors
* Adjust styles
* Highlight regions

### Add Labels

* Enable labels
* Select attribute (e.g., city name)
* Display on map

---

## Step 7: Adding Base Map

Use plugin:

👉 QuickMapServices

Steps:

* Install plugin
* Go to Web → OSM → Standard Map

👉 This overlays your shapefile on a real-world map

---

## Step 8: Creating Custom Shapefiles

If shapefile is missing (e.g., South Sudan):

### Steps:

1. Create new shapefile
2. Select geometry type → Polygon
3. Add attributes (e.g., name, ID)
4. Enable editing mode
5. Draw boundaries manually
6. Save shape

---

## Example

* Created shapefile for South Sudan
* Defined boundary manually
* Assigned attributes

---

## Step 9: Exporting Data

Export shapefile into different formats:

### Options

* Shapefile (.shp)
* KML (for Google Earth)

### Steps

* Right-click layer
* Export → Save As
* Choose format

---

## Visualization in Google Earth

* Open KML file
* View created shapefile on map
* Interact with regions and attributes
