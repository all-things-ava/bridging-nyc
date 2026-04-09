---
title: Bridging Networks - Mobility & Transit Analysis
emoji: 🚇
colorFrom: blue
colorTo: green
sdk: gradio
sdk_version: 4.44.0
app_file: app.py
pinned: false
---

# 🚇 Bridging Networks - Mobility & Transit Analysis Dashboard

An interactive visualization dashboard exploring how NYC's transit network connects neighborhoods across economic mobility rungs. Reveals which areas can access higher-opportunity neighborhoods—and which face "desert" conditions with no upward mobility paths within 45 minutes.

## 🎯 Features

- **Base Maps**: View mobility scores and rungs (1–4) across NYC neighborhoods with MTA overlay
- **Nearest Destinations**: Interactive map showing each origin's nearest higher-rung destination (color-coded by delta rung)
- **Top Attractors**: Explore the 10 neighborhoods that attract the most origins seeking upward mobility
- **Mobility Deserts**: Identify neighborhoods with no +1 rung destination within 45 minutes
- **Interactive Controls**: Pan, zoom, hover for details, and filter by destination

## 📊 Key Concepts

- **Mobility Score**: Neighborhood-level score derived from Opportunity Atlas data
- **Rung**: Categories 1–4 created by KMeans clustering on mobility score
- **Delta Rung**: Destination rung minus origin rung (measures upward mobility potential)
- **Desert**: Origin neighborhood with no +1 rung destination within 45 minutes

## 📈 Data Sources

This analysis uses:
- Opportunity Atlas (economic mobility data)
- NYC NTA (Neighborhood Tabulation Areas)
- MTA subway network
- GTFS transit travel times

## 🛠️ Technical Architecture

This app uses a **two-stage approach** to optimize performance on Hugging Face Spaces:

1. **Preprocessing (Local)**: Heavy data processing and map generation done locally
2. **Display (Hugging Face)**: Lightweight Gradio app serves pre-generated HTML maps

This approach ensures:
- Fast loading times
- No need for large datasets on Hugging Face
- Interactive visualizations remain fully functional
- Minimal computational requirements

## 🚀 How It Works

The interactive maps are generated using [Folium](https://python-visualization.github.io/folium/), which creates HTML/JavaScript visualizations with:
- Zoom and pan capabilities powered by Leaflet.js
- Layer toggle controls
- Popup information windows
- Custom styling and filtering logic

All maps are pre-generated and stored as static HTML files, making the dashboard fast and efficient to serve.

## 📝 Usage

Explore the five main tabs:

1. **Overview: Base Maps**: NYC mobility scores and rungs with MTA subway overlay
2. **Nearest Destinations Analysis**: Each origin linked to its nearest higher-rung destination (197 origins analyzed)
3. **Top Attractor Destinations**: The 10 neighborhoods that attract the most upward-mobility seekers (86 origins, ~39 min avg)
4. **Mobility Deserts**: Neighborhoods with no +1 rung access within 45 minutes
5. **Additional Network Views**: Supplementary route and flow visualizations

Use the interactive controls:
- Hover over elements for detailed statistics
- Zoom/pan to explore specific areas
- Click to filter by destination (on attractor map)
- View paired static summaries below each interactive map

## 🔧 Deployment

For developers looking to deploy similar dashboards:

1. Run preprocessing locally:
```bash
pip install -r requirements-preprocessing.txt
python preprocess.py
```

2. Upload the generated `data/` folder to your Hugging Face Space

3. The Gradio app automatically loads and displays the maps

## 📄 License

This project analyzes public transit and census data for research and visualization purposes.

## 🤝 Credits

Built with:
- [Gradio](https://gradio.app/) - Web interface framework
- [Folium](https://python-visualization.github.io/folium/) - Interactive mapping
- [Hugging Face Spaces](https://huggingface.co/spaces) - Hosting platform
