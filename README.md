# ⚡ EV-Lakehouse: SUMO + RouteE Integration

This project models **electric vehicle (EV) evacuation bottlenecks** using an integrated data lakehouse pipeline.  
It combines mobility simulation (**SUMO**), energy modeling (**NREL RouteE**), and scalable analytics (**Spark**, **MinIO**, **Airflow**).

---

## 🧠 Overview

| Component | Purpose |
|------------|----------|
| **SUMO** (Simulation of Urban Mobility) | Microscopic traffic simulator used to model evacuation routes, speeds, and congestion. |
| **RouteE** (NREL) | Estimates EV power demand and energy consumption using vehicle dynamics and speed profiles. |
| **Spark + Delta Lake** | Stores simulation results in a scalable, queryable format. |
| **MinIO** | Provides S3-compatible object storage for the lakehouse. |
| **Airflow** (optional) | Orchestrates the full simulation and analysis workflow. |

---

## 🧩 Architecture

```text
          ┌────────────┐       ┌────────────┐
          │   SUMO     │       │   RouteE   │
          │ Traffic sim│──────▶│ EV energy  │
          │(I-95, etc.)│       │ consumption│
          └──────┬─────┘       └──────┬─────┘
                 │                    │
                 ▼                    ▼
             Edge data XML       CSV energy data
                 │                    │
                 ▼                    ▼
         ┌────────────────────────────────────┐
         │       Apache Spark + MinIO         │
         │     (ETL + Delta Lake storage)     │
         └────────────────────────────────────┘
                        │
                        ▼
                 Visualization / BI
