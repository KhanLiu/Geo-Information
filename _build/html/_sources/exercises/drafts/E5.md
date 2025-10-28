# E5: Spatial Analysis Methods

## Warm Up
### Some Facts

Traditionally, **data analysis** has often been seen as the domain of mathematicians and statisticians — it sounds difficult, and in fact, it really can be :<

**Spatial data analysis** is also named such as *geostatistics* and *quantitative geography*. In practice, we rarely analyze an entire population; instead, we usually work with **samples**. Based on these samples, we try to draw conclusions about the population as a whole.  
> Obtaining complete and infinite data is impossible — which means that the available data can never fully represent the true underlying distributions. This is also why, in general, **having more data is always better**.

However, spatial data analysis brings additional challenges beyond traditional statistics. As discussed in the lecture, some of the most important issues include:  **Spatial dependence (autocorrelation)**; **Spatial heterogeneity**; **MAUP (Modifiable Areal Unit Problem)**. These unique properties make spatial data analysis both more complex and more powerful, offering insights that traditional data analysis cannot capture.  

### Data Quality
In the ML & DL, there is a well-known truth:  
**“Good data + simple model is much better than bad data + complex model.”** or "**data quality matters more than data size**"

Take an example, how to tell if data Is High-Quality in LLM:
| Criteria         | Good Data Looks Like...                        |
|------------------|------------------------------------------------|
| 📘 Accurate      | Facts are true and reliable.                   |
| ✍️ Well-written | Clear grammar, no typos, logical sentences.    |
| 🧠 Informative   | Contains useful knowledge, not fluff.          |
| 🌍 Diverse       | Covers many topics and styles.                 |
| 🚫 Clean         | No spam, hate speech, or repeated content.     |

But when it comes to **spatial data**, quality issues become even more complex. It’s not only about the correctness of attributes, but also about the **location, time, and relationships** of features. A dataset can have perfect attribute values but still be unusable if the geometry is shifted by a few meters, or if the coordinate reference system (CRS) does not match.   
In other words, while ML models suffer mainly from label noise or imbalance, spatial data analysis must also ensure **where, when, and how accurately** features are represented in space.  

### Branches of Spatial Data Analysis

Spatial data analysis can be seen as consisting of several main branches, each focusing on different aspects of spatial information:
- **Spatial Dependence and Spatial Heterogeneity**  
  Focuses on spatial autocorrelation, spatial weight matrices, and spatial regression models (spatial lag, spatial error, geographically weighted regression).
- **Spatial Accessibility**  
  Examines spatial distance relationships, proximity analysis, overlay analysis, and network analysis to study accessibility patterns.
- **Spatial Patterns (Spatial Layouts)**  
  Investigates spatial distributions such as point patterns, grid-based analysis, spatial clustering, and landscape analysis.
- **Spatial Interpolation and Estimation**  
  Deals with prediction at unsampled locations, including deterministic interpolation (e.g., IDW) and geostatistical methods (e.g., kriging).

## Task
### Descriptions
In this exercise, you will practice several **fundamental spatial analysis methods** in ArcGIS Pro.
The goal is to understand how spatial relationships can be modeled and analyzed with GIS. Detailed instructions in {download}`Lesson 5 <../doc/Lesson 5.docx>`

& You can [Click here to look](./lessons/lesson5.md)

#### Data
- `Data Students.gdb` (Buildings, Roads, Underground Stations, Tram Stops, Cafés)
- `orthophoto.tif` (optional reference imagery)

### Overview
```{note}
:class: dropdown
- [ ] **Thiessen (Voronoi) Polygons**  
  - Divide space into catchment areas around underground stations.  
- [ ] **Buffer Analysis**  
  - Create a 50 m buffer around main roads to model zones of influence.  
- [ ] **Multiple Ring Buffers**  
  - Build reachability zones (250 m, 500 m, 750 m, 1000 m) around underground stations and tram stops.  
- [ ] **Intersect Analysis**  
  - Identify overlapping areas of equal distance to public transport points.  
- [ ] **Union and Dissolve**  
  - Combine and aggregate buffer zones for simplified analysis.  
- [ ] **Spatial Join**  
  - Relate attributes of roads and buffers to buildings based on overlap.  
- [ ] **Distance Analysis (Near tool)**  
  - Calculate distances from buildings to the nearest cafés.  
- [ ] **Attribute Join**  
  - Enrich building data by joining café names via key fields.  
- [ ] **Spatial Autocorrelation** && **Generate Near Table**  
  - Calculate Moran’s I for café distribution patterns. 
  - Compute nearest public transport points for each café and visualize connections.  
```


#### 1. Thiessen Polygons
- Input: underground stations.  
- Create Thiessen polygons → each polygon shows the area closest to a given station.  

#### 2. Buffer Analysis
- Input: main roads.  
- Create a 50 m buffer to model zones of influence.  
- Compare with buildings to see which are affected.  

#### 3. Multiple Ring Buffers
- Input: tram and underground stations.  
- Build buffers at 250 m, 500 m, 750 m, and 1000 m to show accessibility.  

#### 4. Overlay (Intersect / Union)
- Intersect buffers from tram + underground stations to find overlapping influence areas.  
- Union or dissolve overlapping buffers for simplified coverage zones.  

#### 5. Proximity Analysis
- Use **Near tool**: measure distance from each building to nearest café.  
- Use **Generate Near Table**: list nearest transport stop for each café.  

#### 6. Spatial Statistics
- Run **Moran’s I** on cafés to check if they are clustered, dispersed, or random.  


### Advance Task
- Try to build up some **basic statistics knowledge** — such as *Gaussian distribution*, *hypothesis testing*, *principal component analysis (PCA)*, and *linear regression*. Meanwhile, practice using **R** or **Jupyter Notebook** to explore these concepts through hands-on examples and simple experiments. 
  - You can check some examples in [Python Statistics Fundamentals: How to Describe Your Data](https://realpython.com/python-statistics/), [How to calculate summary statistics](https://pandas.pydata.org/docs/getting_started/intro_tutorials/06_calculate_statistics.html), [Gaussian_Distribution_Function](https://github.com/amirjahantab/Gaussian_Distribution_Function), [PCA, Sci-kit Learn](https://scikit-learn.org/stable/modules/generated/sklearn.decomposition.PCA.html)
- Write a program to load your analysis results (e.g., Thiessen polygons, buffers, or Near table), **visualize them**, and **export the map** to an image (PNG/SVG) or an interactive HTML map
  - Visualizing standard media files such as images is usually straightforward — for example, with [PIL](https://pypi.org/project/pillow/) or [OpenCV](https://opencv.org/).

## Materials
- [Spatial analysis in ArcGIS Pro](https://pro.arcgis.com/en/pro-app/latest/help/analysis/introduction/spatial-analysis-in-arcgis-pro.htm)
- [What Is Spatial Data Analysis?, USC](https://gis.usc.edu/blog/what-is-spatial-data-analysis/)
- [Spatial analytics Course, Henrikki Tenkanen](https://spatial-analytics.readthedocs.io/en/latest/)
- [Geopandas - spatial operations, Atma's Blog](https://atmamani.github.io/teaching_resources/geopandas/geopandas_spatial_overlays/)  
- [MIT OpenCourseWare: Spatial Database Management and Advanced Geographic Information Systems](https://ocw.mit.edu/courses/11-521-spatial-database-management-and-advanced-geographic-information-systems-spring-2003/)
