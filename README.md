<div align="center">

# 🌊 Ocean3D — Interactive Ocean Digital Twin

### Explore, compare, and analyze ocean conditions through an interactive 3D web platform.

[![Live Demo](https://img.shields.io/badge/🌊_Live_Demo-Ocean3D-0ea5e9?style=for-the-badge)](https://ocean3d.vercel.app)
[![React](https://img.shields.io/badge/React-19.2-61DAFB?style=for-the-badge&logo=react&logoColor=black)](https://react.dev/)
[![TypeScript](https://img.shields.io/badge/TypeScript-6.0-3178C6?style=for-the-badge&logo=typescript&logoColor=white)](https://www.typescriptlang.org/)
[![Three.js](https://img.shields.io/badge/Three.js-WebGL-black?style=for-the-badge&logo=three.js&logoColor=white)](https://threejs.org/)
[![FastAPI](https://img.shields.io/badge/FastAPI-0.110+-009688?style=for-the-badge&logo=fastapi&logoColor=white)](https://fastapi.tiangolo.com/)
[![Python](https://img.shields.io/badge/Python-3.10+-3776AB?style=for-the-badge&logo=python&logoColor=white)](https://www.python.org/)

</div>

---

## 🌊 Overview

**Ocean3D** is an interactive ocean digital twin platform designed to visualize ocean conditions across space, depth, and time while comparing modeled ocean states with observational and satellite-derived data.

The platform combines a **3D WebGL visualization layer**, a **FastAPI analytical backend**, and multiple ocean-data sources to provide an intuitive workspace for exploring marine conditions and identifying deviations between model guidance and observations.

Ocean3D is built around a simple workflow:

> **Explore → Compare → Detect → Analyze → Understand**

The interface allows users to move between ocean regions, physical parameters, depth levels, and time steps while inspecting observation points, model values, differences, anomalies, current vectors, and analytical statistics.

### 🚀 Try it live

**[🌊 Open Ocean3D Live Demo](https://ocean3d.vercel.app)**

---

## ✨ Key Features

### 🌐 Interactive 3D Ocean Visualization

- Interactive Three.js / WebGL ocean environment
- Orbit, pan, and zoom navigation
- Regional ocean exploration
- Spatial particle/grid visualization
- Procedural geographic coastlines
- Latitude/longitude reference grid
- Dynamic depth-based visualization

### 🗺️ Ocean Regions

Ocean3D currently supports:

- **Bay of Bengal**
- **Arabian Sea**
- **North Indian Ocean Basin**
- **Global Overview**

### 🌡️ Multi-Parameter Ocean Monitoring

The platform supports eight environmental parameters:

| Parameter | Unit | Data Character |
|---|---|---|
| Sea Surface Temperature (SST) | °C | Operational model |
| Salinity | PSU | Observational product |
| Sea Surface Height (SSH) | m | Satellite-derived |
| Current Velocity | m/s | Operational model |
| Dissolved Oxygen | µmol/kg | Observational product |
| Chlorophyll-a | mg/m³ | Satellite-derived |
| Wind Speed | m/s | Operational model |
| Atmospheric Pressure | hPa | Operational model |

### 🌊 Depth Exploration

The water column can be explored across:

```text
0 m
10 m
50 m
100 m
200 m
500 m
1000 m
1500 m
2000 m
Surface-only variables such as SSH, Chlorophyll-a, Wind Speed, and Atmospheric Pressure are automatically restricted to the surface level.

⏱️ Temporal Exploration

Ocean3D provides multiple time steps for exploring temporal changes in the modeled ocean state and associated observations.

Users can:

Move between time steps
Play the timeline
Inspect changing ocean fields
Compare temporal station behavior
📍 Observation Inspection

Interactive observation markers can be selected directly from the 3D environment.

The inspection workflow exposes:

Model value
Observed value
Difference
Z-score
Anomaly classification
Temporal progression
🌊 Current Flow Vectors

The current visualization layer displays directional flow vectors representing horizontal ocean movement.

Vectors are derived from the active velocity field and are visualized as animated directional arrows across the ocean surface/depth view.

🚨 Anomaly Detection

Ocean3D compares observed and modeled values and normalizes their difference using a regional baseline standard deviation.

This produces three monitoring categories:

Z-score	Classification
`	Z
`1.5 ≤	Z
`	Z

Anomalies are highlighted directly within the 3D environment and analytical interface.

📊 Analytics Dashboard

The analytical layer provides:

Mean
Minimum
Maximum
Standard deviation
RMSE
Model vs observation comparison
Temporal progression
Residual analysis
Anomaly statistics
🔬 How Ocean3D Works

Ocean3D follows a model-observation comparison workflow:

Ocean Data Sources
        ↓
Data Ingestion
        ↓
Processing & Validation
        ↓
Spatial / Temporal Alignment
        ↓
3D Ocean Visualization
        ↓
Model vs Observation Comparison
        ↓
Residual Calculation
        ↓
Anomaly Detection
        ↓
Analytics & Decision Support

The platform is designed to make complex oceanographic information easier to inspect visually rather than relying only on raw numerical datasets.

📐 Analytical Engine
1. Model vs Observation Difference

For matched model and observation values:

Difference = Observed − Model
Interpretation

Positive difference

Observed > Model

The observation is higher than the modeled value.

Negative difference

Observed < Model

The observation is lower than the modeled value.

Near-zero difference

Observed ≈ Model

The model and observation are closely aligned.

2. Z-Score Anomaly Detection

Ocean3D normalizes the model-observation residual against a regional baseline standard deviation:

Z = (Observed − Model) / σbaseline

Where:

Observed = observational value
Model = modeled value
σbaseline = regional baseline standard deviation
Classification
|Z| < 1.5
→ NORMAL

1.5 ≤ |Z| < 2.5
→ MODERATE DEVIATION

|Z| ≥ 2.5
→ SIGNIFICANT ANOMALY

This provides a deterministic statistical framework for highlighting unusually large model-observation deviations.

3. RMSE

Regional model-observation agreement is summarized using Root Mean Square Error:

RMSE = √( 1/N × Σ(Observedᵢ − Modelᵢ)² )

RMSE provides a single measure of the average magnitude of residual differences across matched points.

🛰️ Data Sources & Provenance

Ocean3D integrates multiple categories of ocean and environmental information.

Operational / Model Data
Ocean and atmospheric model variables used for environmental context and visualization
Current velocity fields derived from the model state
NOAA PMEL RFROM

RFROM v2.3 provides an Argo-informed gridded observational product used for oceanographic variables such as temperature and salinity.

NOAA PMEL GOBAI-O2

GOBAI-O2 provides gridded dissolved oxygen information incorporating BGC-Argo and other observational sources.

NOAA CoastWatch Sea Surface Height

Satellite altimetry products provide gridded sea-surface-height information for surface ocean analysis.

NOAA CoastWatch VIIRS Chlorophyll

Satellite ocean-color observations provide chlorophyll-a information for surface ocean monitoring.

Research Vehicle Demonstration

Ocean3D includes an AUV / Glider demonstration layer for visualizing how research-vehicle observations could appear in the platform.

Note: The AUV / Glider layer is a simulated demonstration and does not represent live telemetry from a specific research vehicle.

📊 Supported Parameters
Parameter	Visualization	Depth Support
SST	3D field	Surface → Deep
Salinity	3D field	Surface → Deep
SSH	Surface field	0 m only
Current Velocity	Field + vectors	Surface → Deep*
Dissolved Oxygen	3D field	Surface → Deep
Chlorophyll-a	Surface field	0 m only
Wind Speed	Surface field	0 m only
Atmospheric Pressure	Surface field	0 m only

* Current velocity at deeper levels is derived/attenuated from the surface model representation and is clearly treated as derived rather than direct deep observational telemetry.

🧭 Ocean3D Interface

The dashboard is organized around several interactive components:

┌─────────────────────────────────────────────────────┐
│                    Ocean3D Header                   │
├───────────────┬─────────────────────┬───────────────┤
│               │                     │               │
│ Control Panel │    3D Ocean View    │   Inspector   │
│               │                     │               │
│ Region        │     Three.js        │  Observation  │
│ Parameter     │     WebGL           │  Comparison   │
│ Depth         │                     │  Anomaly      │
│ Time          │                     │               │
├───────────────┴─────────────────────┴───────────────┤
│                  Analytics Panel                    │
│          Time Series / RMSE / Statistics            │
└─────────────────────────────────────────────────────┘
🏗️ System Architecture
☁️ Deployment Architecture

Ocean3D is deployed using separate frontend and backend services:

                    🌊 Ocean3D
                         │
              ┌──────────┴──────────┐
              │                     │
          Vercel                 Render
              │                     │
      React + Vite             FastAPI
      Three.js UI              Backend API
              │                     │
              └──────────┬──────────┘
                         │
                  Ocean Data Sources
Frontend

Hosted on Vercel.

Backend

Hosted on Render.

The frontend communicates with the backend through /api routing.

💻 Tech Stack
Layer	Technology	Purpose
Frontend	React 19	UI and component architecture
Language	TypeScript	Type-safe frontend development
3D Rendering	Three.js	WebGL ocean visualization
3D Framework	React Three Fiber	React integration for Three.js
Build Tool	Vite	Development and production bundling
Styling	Tailwind CSS	Responsive UI and visual design
Charts	Recharts	Analytical visualizations
Icons	Lucide React	UI iconography
Backend	FastAPI	REST API and backend services
Server	Uvicorn	ASGI application server
Validation	Pydantic	API schemas and validation
Scientific Computing	NumPy	Numerical calculations
Data Processing	Pandas	Data manipulation and statistics
Hosting	Vercel	Frontend deployment
Hosting	Render	Backend deployment
🔌 API

The FastAPI backend exposes REST endpoints for the frontend.

Method	Endpoint	Purpose
GET	/api/health	Backend health and service status
GET	/api/parameters	Supported ocean parameters
GET	/api/regions	Available geographic regions
GET	/api/ocean-data	Model ocean field data
GET	/api/observations	Observation data
GET	/api/comparison	Model vs observation comparison
GET	/api/anomalies	Detected deviations/anomalies
GET	/api/statistics	Statistical summaries
GET	/api/timeseries	Temporal station/regional progression
GET	/api/timesteps	Available time steps
GET	/api/research-vehicle	Research vehicle demonstration data

Interactive API documentation is available through FastAPI's Swagger interface when running the backend locally.

📁 Project Structure
Ocean 3d/
│
├── backend/
│   ├── __init__.py
│   ├── data_engine.py
│   ├── live_client.py
│   ├── main.py
│   ├── models.py
│   └── requirements.txt
│
├── data/
│   └── README.md
│
├── frontend/
│   ├── index.html
│   ├── package.json
│   ├── package-lock.json
│   ├── tsconfig.json
│   ├── vercel.json
│   ├── vite.config.ts
│   │
│   └── src/
│       ├── api.ts
│       ├── types.ts
│       ├── index.css
│       ├── main.tsx
│       ├── App.tsx
│       │
│       └── components/
│           ├── Header.tsx
│           ├── ControlPanel.tsx
│           ├── Ocean3DViewer.tsx
│           ├── RiskDecisionSupport.tsx
│           ├── LocationInspector.tsx
│           └── AnalyticsPanel.tsx
│
├── .gitignore
└── README.md
🚀 Run Locally
Prerequisites
Node.js 18+
Python 3.10+
npm
pip
1. Clone the repository
git clone https://github.com/vivek28n/Ocean3d.git
cd Ocean3d
2. Start the Backend
cd backend

pip install -r requirements.txt

uvicorn main:app --reload --host 127.0.0.1 --port 8000

Backend:

http://127.0.0.1:8000

Swagger:

http://127.0.0.1:8000/docs

Health check:

http://127.0.0.1:8000/api/health
3. Start the Frontend

Open another terminal:

cd frontend

npm install

npm run dev

Frontend:

http://localhost:5173
🧪 Built-in Demo Flow

Ocean3D includes a Demo Flow preset that configures a representative monitoring scenario.

The preset demonstrates:

Bay of Bengal region
Sea Surface Temperature
10 m depth
A selected time step
Model visualization
Observation markers
Difference visualization
Anomaly indicators
Current vectors
Station inspection and analytics

This provides a quick way to explore the complete Ocean3D workflow.

🛠️ Engineering Highlights
Type-Safe Data Contracts

FastAPI/Pydantic models and TypeScript interfaces provide structured communication between the backend and frontend.

Resilient API Client

The frontend API layer is designed to handle temporary backend/data-source availability issues gracefully.

Interactive WebGL Rendering

Three.js is used for spatial ocean visualization, particle/grid rendering, observation markers, and current vectors.

Responsive Layout

The dashboard adapts its visualization area when control and inspection panels are expanded or collapsed.

Spatial Inspection

Interactive raycasting allows users to select observation markers directly within the 3D environment.

Analytical Workflow

The application connects visualization with quantitative analysis instead of presenting ocean fields as purely visual layers.

⚠️ Data Transparency & Limitations

Ocean3D combines operational model information, satellite-derived observations, gridded observational products, and simulated demonstration components.

Because these sources have different spatial resolutions, update frequencies, and temporal coverage:

Not every parameter represents current-day observations.
Observational products may have delayed source coverage.
Satellite-derived variables are surface observations.
Surface-only parameters are not extrapolated to arbitrary depths.
The AUV/Glider layer is simulated for demonstration.
Deep current velocity visualization is derived from the model representation rather than direct deep-vehicle telemetry.

Ocean3D should therefore be understood as an interactive monitoring, comparison, and analytical visualization platform, not as a standalone operational emergency prediction system.

🔮 Future Scope

Potential future enhancements include:

 Expanded direct ingestion from Copernicus Marine and NOAA services
 More NetCDF / Xarray based scientific datasets
 Historical observation archives
 PostgreSQL/PostGIS spatial data storage
 High-resolution GEBCO bathymetry
 Full volumetric 3D ocean rendering
 Advanced spatiotemporal anomaly detection
 Additional satellite and observational products
 Exportable analysis reports
 Enhanced scientific visualization and filtering
📸 Screenshots

Screenshots and demo GIFs can be added here to showcase the 3D environment, parameter controls, observation inspection, anomaly visualization, and analytics dashboard.

👨‍💻 Project

Ocean3D is a personal engineering project focused on combining:

🌊 Oceanographic visualization
🛰️ Environmental data
🧮 Scientific computing
📊 Statistical analysis
🎨 Interactive 3D graphics
⚡ Modern full-stack web development

The project explores how complex ocean datasets can be transformed into an interactive visual and analytical experience.

<div align="center">
🌊 Explore Ocean3D

🚀 Launch Live Demo

Built with React, Three.js, FastAPI & Python.

</div> ```