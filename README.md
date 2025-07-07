# Dynamic Pricing Engine for Urban Parking Lots
**Capstone Project – Summer Analytics 2025**  
**Hosted by Consulting & Analytics Club × Pathway**

---

## Overview

This project implements a real-time **Dynamic Pricing System** for **14 urban parking lots** based on occupancy, demand patterns, and competition.  
The goal is to develop a **smart, data-driven pricing model** that adjusts prices dynamically throughout the day to:

- Optimize lot usage  
- Improve revenue potential  
- Avoid over-congestion

---

## Models Developed

Three progressive models were developed using **Python** (Numpy, Pandas) and **Pathway** for real-time streaming:

1. **Model 1 – Linear Occupancy-Based Pricing**
2. **Model 2 – Demand-Based Dynamic Pricing**
3. **Model 3 – Competitive-Aware Smart Pricing**

---

## ⚙️ Tech Stack

- **Python**  
- `numpy`, `pandas` – data handling & logic  
- **Pathway** – real-time stream simulation & processing  
- **Bokeh** – live data visualization  
- **Google Colab** – execution environment

---

##  Project Architecture

mermaid
flowchart TD
- A[Real-Time Data Stream (Pathway)] --> B[Data Preprocessing]
-   B --> C[Model 1: Linear Occupancy Pricing]
-   B --> D[Model 2: Demand-Based Pricing]
-   B --> E[Model 3: Competitive Pricing Engine]
- C --> F[Price Output CSV]
- D --> F
- E --> F
- B --> G[Bokeh Live Visualization]
- E --> H[Competitor Proximity & Price Check]
- H --> E

- style E fill:#ffd966,stroke:#dba400,stroke-width:2px
- style F fill:#d9ead3,stroke:#6aa84f
- style A fill:#d0e0e3

--- 

## Architecture & Workflow

1️⃣ Real-Time Data Ingestion
Data simulated via Pathway mimics live input from 14 parking lots, over 73 days, 18 time steps/day.
- Features include:
- Occupancy
- Capacity
- Queue Length
- Traffic Level
- Vehicle Type
- Latitude & Longitude
- Special Day Indicator

2️⃣ Model 1: Linear Occupancy-Based Pricing - Price increases linearly with the occupancy ratio.
- Formula: Price_(t+1) = Price_t + α * (Occupancy / Capacity)

3️⃣ Model 2: Demand-Based Dynamic Pricing
Constructs a demand score using multiple features: Occupancy Ratio, Queue Length, Traffic Level, Special Day, Vehicle Type (weighted). Formula:
- Demand = α*(Occupancy/Capacity) + β*Queue - γ*Traffic + δ*SpecialDay + ε*VehicleType
- Price_t = BasePrice * (1 + λ * NormalizedDemand)

4️⃣ Model 3: Competitive-Aware Smart Pricing
Adds spatial intelligence:
- Calculates Haversine distance to nearby lots
- Checks competitor prices

Strategy:
- If nearby lots are cheaper → decrease price or reroute vehicles
- If nearby lots are more expensive → increase price
- Ensures bounded variation: [0.5x, 2x] of base price

--- 

## Visualization (Bokeh)
Real-time plotting of prices for all lots
Competitor comparison for insights

--- 

## Output Files
File Name	Description
- Model1_pricing_output.csv	Output of baseline linear model
- Model2_pricing_output.csv	Output of demand-based model
- Model3_competitive_pricing_output.csv	Final model with competition logic

---

## Assumptions
All lots start with a base price of $10
Price range bounded between 0.5x and 2x base price
Vehicle types mapped to weights:
- Car = 1, Bike = 0.5, Truck = 1.5
- Haversine distance used for spatial proximity

---

## Resources
- Pathway Developer Docs
- Summer Analytics 2025 Course

--- 
## Author
-- Abhijeet Singh Parihar
-- Capstone Participant 

--- 
