---
title: "Mapping Pokémon to Real-World Biomes and Locations"
description: "A project combining Pokémon, real-world biomes, and APIs to map habitats interactively."
author: "Vignesh & Team"
layout: default
---

# **Mapping Pokémon to Real-World Biomes and Locations**

## **Goals**
1. Allocate Pokémon to biomes and habitats based on their types, traits, and power scales.
2. Use APIs and datasets to map these biomes to real-world locations, incorporating environmental and ecological data.
3. Visualize the results on an interactive map with Pokémon-specific details (e.g., create a global view of where Pokémon would exist, using tools like Folium or GeoPandas).
4. **Ambitious extension:** Enable Pokémon search by name with satellite imaging of their habitats using NASA APIs.

---

## **Outline**

### **1. Introduction (@CHANG)**

**Step 1:** Allocate Pokémon types to specific biomes based on their characteristics and environmental traits.  
**Step 2:** Identify potential real-world locations where these biomes exist, providing a range of geographic coordinates for each biome. (Hailey)  
**Step 3:** Assign Pokémon within their respective biomes and rank them based on factors like power scaling. For example, stronger Pokémon such as Charizard would inhabit the hottest parts of a desert, while weaker Pokémon like Charmander would stay in less extreme areas. (vig)  
**Step 4:** Rank real-world coordinates based on their 'biome strength.' Continuing the earlier example, we'd rate the Lut Desert (hottest desert in the world) 100.  
**Step 5:** Use the scaling criteria to allocate Pokémon to precise global locations on a map.

---

### **Step 1: Categorizing Pokémon**

#### **Goal**  
Categorize all Generation 1 Pokémon based on their habitats, types, and base stats.

#### **Process**
1. **Fetch Pokémon Data**
   - Use **PokéAPI**'s endpoints:
     - **Generation Endpoint**: Fetch all Pokémon in Generation 1 (providing a list of Pokémon IDs).  
     - **Pokémon Endpoint**: Extract types (e.g., Grass, Fire) and base stats (e.g., HP, Attack, Defense).  
     - **Pokémon Species Endpoint**: Identify each Pokémon's in-game habitat.

2. **Habitat Breakdown (Generation 1)**:
   - **Grassland**: 35 Pokémon  
   - **Urban**: 22 Pokémon  
   - **Forest**: 21 Pokémon  
   - **Water's Edge**: 19 Pokémon  
   - **Mountain**: 18 Pokémon  
   - **Sea**: 15 Pokémon  
   - **Rough Terrain**: 8 Pokémon  
   - **Cave**: 8 Pokémon  
   - **Rare**: 5 Pokémon  

3. **Classification Process**
   - **Group Pokémon by Habitat**: Assign each Pokémon to its corresponding habitat.
   - **Refine by Type**: Distinguish Pokémon in the same habitat by type (e.g., Fire-types vs. Water-types in grasslands).  
   - **Calculate Strength**: Derive a numerical "strength" for each Pokémon using their base stats.

#### **Example**
- **Bulbasaur (ID 1)**  
   - Habitat: Grassland  
   - Types: Grass, Poison  
   - Base Stats: HP: 45, Attack: 49 → Assign strength value (e.g., 30).  
   - Result: Bulbasaur is matched to a grassland biome with strength 30.

By the end of Step 1, Pokémon will be grouped by habitat, further categorized by types, and ranked by strength.

---

### **Step 2: Mapping Real-World Biomes**

#### **Goal**  
Create a world map highlighting locations corresponding to biomes, along with geographic coordinates.

#### **Challenges and Filters**  
1. **Overabundance of Biome Locations**: 
   - Use APIs (e.g., Open-Meteo) to narrow down locations based on environmental specifics.  
   - For deserts, choose metrics like temperature.  
   - Filter locations by key landmarks or randomly sample locations.  

---

### **Step 3: Allocating Pokémon**

#### **Biome Matching for Types**  
| **Type**      | **Primary Biomes**                | **Justification**                                       |  
|----------------|-----------------------------------|---------------------------------------------------------|  
| **Fire**       | Hot areas, deserts, volcanic regions | Match to high-temperature regions.                      |  
| **Water**      | Rainfall-heavy areas, lakes, oceans | Use precipitation and water coverage as metrics.        |  
| **Electric**   | Cities, lightning-heavy areas      | Match to high thunderstorm zones (lightning APIs).      |  
| **Grass**      | Grasslands, jungles               | Match to vegetation density metrics.                    |  
| **Ice**        | Tundra, polar regions             | Match to low-temperature areas.                         |  
| **Fighting**   | Urban areas, high-crime zones     | Use socio-economic crime datasets.                      |  
| **Poison**     | Jungles, polluted regions         | Match to toxic and pollution-heavy zones.               |  
| **Ground**     | Caves, arid lands                 | Match to dry and underground terrains.                  |  
| **Flying**     | Mountain peaks                    | Match to high-elevation coordinates.                    |  
| **Psychic**    | Isolated regions                  | Possible correlation to peaceful, quiet zones.          |  
| **Bug**        | Grasslands, jungles               | Overlap with Grass biomes.                              |  
| **Rock**       | Mountain bases                    | Match to rocky low-elevation zones.                     |  
| **Ghost**      | Swamps, mangroves                 | Associated with dark and mysterious environments.        |  
| **Dragon**     | Rare biomes                       | Match to ancient forests or unique landscapes.          |  

#### **Example**  
- **Water-Type Pokémon**  
   - Biomes: Lakes, Oceans  
   - Metric: Use marine forecast data (e.g., wave height max via Open-Meteo).  

#### **Dual-Typed Pokémon**  
- Assign manually based on predominant type (feasible for Generation 1).

---

### **Ranking Real-World Locations**

#### **Goal**  
Rank locations by biome "strength" for precise Pokémon placement.

#### **Algorithm Example**
1. **Normalizing Data**  
   - Formula:  
     \[
     z_i = \frac{x_i - \text{min}(x)}{\text{max}(x) - \text{min}(x)} \times 100
     \]  
     - \( z_i \): Normalized value for the i-th location.  
     - \( x_i \): Raw metric (e.g., temperature).  

2. **Example: Fire Biome**  
   - Input: Lut Desert has the highest historical average temperature.  
   - Output: Ranked as 100 (highest strength).  

#### **Limitations**  
1. **API Call Limitations**  
   - Filter locations to cities/landmarks or randomly sample coordinates.  

2. **Multiple Metrics**  
   - Use vectors for multi-metric ranking (e.g., temperature + solar radiation).  

---

### **Justification for Data Sources**
- **Google Earth Engine Dataset**: World ecoregions and biome classifications.  
- **Open-Meteo API**: Environmental data (e.g., temperature, precipitation).  
- **Global Biodiversity Information Facility (GBIF)**: Species distribution insights.  
- **PokéAPI**: Pokémon attributes, stats, and habitats.

---

### **Timeline**
- **Week 1**: Finalize data sources; refine Pokémon-biome matching logic.  
- **Weeks 2–4**: Process geographic and environmental data; implement biome-Pokémon mapping.  
- **Weeks 5–7**: Develop ranking system; integrate Open-Meteo data.  
- **Weeks 8–9**: Visualize Pokémon distribution using GeoPandas; finalize presentation.  

---

