<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Mapping Pokémon to Real-World Biomes and Locations</title>
    <style>
        body {
            font-family: Arial, sans-serif;
            line-height: 1.6;
            margin: 0;
            padding: 0 20px;
            background-color: #f4f4f4;
        }
        header {
            background: #333;
            color: #fff;
            padding: 10px 0;
            text-align: center;
        }
        section {
            margin: 20px 0;
            background: #fff;
            padding: 20px;
            border-radius: 8px;
            box-shadow: 0 2px 4px rgba(0, 0, 0, 0.1);
        }
        h1, h2, h3 {
            color: #333;
        }
        ul, ol {
            margin: 10px 0;
        }
        .timeline {
            background: #e7f3ff;
            border-left: 4px solid #2196F3;
            padding: 10px;
            margin: 20px 0;
        }
    </style>
</head>
<body>
    <header>
        <h1>Mapping Pokémon to Real-World Biomes and Locations</h1>
    </header>

    <section>
        <h2>Goals</h2>
        <ul>
            <li>Allocate Pokémon to biomes and habitats based on their types, traits, and power scales.</li>
            <li>Map these biomes to real-world locations using environmental and ecological data.</li>
            <li>Visualize results on an interactive map with Pokémon-specific details using tools like Folium or GeoPandas.</li>
            <li>Ambitious Extension: Enable Pokémon search by name with satellite imaging of their habitats using NASA API.</li>
        </ul>
    </section>

    <section>
        <h2>Outline</h2>
        <ol>
            <li><strong>Introduction</strong>: Overview of steps for Pokémon allocation and biome mapping.</li>
            <li><strong>Step 1</strong>: Categorize Generation 1 Pokémon based on their habitats, types, and base stats.</li>
            <li><strong>Step 2</strong>: Identify real-world biomes and geographic coordinates for Pokémon habitats.</li>
            <li><strong>Step 3</strong>: Assign Pokémon to biomes, rank locations by biome strength, and map Pokémon.</li>
        </ol>
    </section>

    <section>
        <h3>Details of Step 1</h3>
        <p>Classify Generation 1 Pokémon using three endpoints from PokéAPI:</p>
        <ul>
            <li><strong>Generation Endpoint:</strong> Fetch all Pokémon in Generation 1.</li>
            <li><strong>Pokémon Endpoint:</strong> Extract type (e.g., Fire, Water) and base stats (e.g., HP, Attack).</li>
            <li><strong>Pokémon Species Endpoint:</strong> Identify habitats for each Pokémon.</li>
        </ul>
        <p>Pokémon habitats in Generation 1 include:</p>
        <ul>
            <li>Grassland: 35 Pokémon</li>
            <li>Urban: 22 Pokémon</li>
            <li>Forest: 21 Pokémon</li>
            <li>... (full list continued).</li>
        </ul>
        <p>Example: Bulbasaur (Grass/Poison) is allocated to Grasslands with strength value calculated from base stats.</p>
    </section>

    <section>
        <h3>Details of Step 2</h3>
        <p>Generate a world map with highlighted biomes using APIs like Open-Meteo for environmental data.</p>
        <p>Filter locations by metrics like temperature, precipitation, and vegetation density to determine Pokémon habitats.</p>
    </section>

    <section>
        <h3>Details of Step 3</h3>
        <p>Allocate Pokémon to real-world locations based on biome strength:</p>
        <ul>
            <li>Fire-type Pokémon: Deserts or volcanic regions ranked by temperature.</li>
            <li>Water-type Pokémon: Lakes or oceans ranked by precipitation and wave height.</li>
            <li>... (more types outlined).</li>
        </ul>
        <p>Example: Charizard allocated to the Lut Desert (hottest desert globally).</p>
    </section>

    <section>
        <h2>Justification for Data Sources</h2>
        <ul>
            <li><strong>Google Earth Engine Dataset:</strong> Provides a classification of global ecoregions.</li>
            <li><strong>Open-Meteo API:</strong> Supplies environmental data for ranking Pokémon habitats.</li>
            <li><strong>Global Biodiversity Information Facility (GBIF):</strong> Adds ecological realism by comparing Pokémon to real species.</li>
            <li><strong>Pokémon API (PokeAPI):</strong> Offers detailed Pokémon attributes for habitat matching.</li>
        </ul>
    </section>

    <section class="timeline">
        <h2>Timeline</h2>
        <ul>
            <li><strong>Week 1:</strong> Finalize data sources and research Pokémon-biome matching logic.</li>
            <li><strong>Weeks 2-4:</strong> Process geographic and environmental data.</li>
            <li><strong>Weeks 5-7:</strong> Develop ranking system and integrate Open-Meteo data.</li>
            <li><strong>Weeks 8-9:</strong> Visualize Pokémon distribution and prepare final presentation.</li>
        </ul>
    </section>
</body>
</html>

