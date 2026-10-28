# 🏢 Residential Property Market Analytics & Data Governance Audit
### Multi-City Exploratory Data Analysis (EDA), Data Quality Engineering, and Rp 25 Billion Investment Allocation Strategy for RPPI

[![Python](https://img.shields.io/badge/Python-3776AB?logo=python&logoColor=white)](https://www.python.org/)
[![Jupyter Notebook](https://img.shields.io/badge/Notebook-Jupyter-orange?logo=jupyter&logoColor=white)](Study_Case_01_Kelompok_E_DatMin_DS2.ipynb)
[![Pandas](https://img.shields.io/badge/Pandas-150458?logo=pandas&logoColor=white)](https://pandas.pydata.org/)
[![Seaborn](https://img.shields.io/badge/Seaborn-4C72B0?logo=seaborn&logoColor=white)](https://seaborn.pydata.org/)
[![Domain](https://img.shields.io/badge/Domain-Property%20Analytics-brightgreen)]()

---

## 📌 Project Overview & Business Understanding

**Real Property Prima Indonesia (RPPI)** is a residential property brokerage operating across the Greater Jakarta metropolitan agglomeration—**Jabodetabek (*Jakarta, Bogor, Depok, Tangerang, and Bekasi*)**. To maintain market leadership and accelerate its transformation into a *data-driven enterprise*, RPPI's executive management requires empirical intelligence regarding regional property pricing, buyer preferences, and internal data quality across local branches.

This project addresses five critical business objectives:
1. **Data Governance & Hygiene Audit:** Identifying schema anomalies, non-standardized units, and missing values to formulate architectural recommendations for the **Data Engineering (DE) & Database Administration (DBA)** teams.
2. **Cross-Regional Price Disparity Analysis:** Evaluating property valuation dynamics across 5 cities to explain premium price concentrations in metropolitan business centers.
3. **Strategic Branch Expansion:** Recommending optimal city locations for RPPI's next branch office based on listing volume and transaction liquidity.
4. **Best-Selling Residential Archetypes:** Profiling high-demand property specifications (land/building area, bedroom/bathroom configurations, electricity capacity, and cardinal orientation).
5. **Rp 25 Billion Investment Portfolio Strategy:** Designing an optimal capital allocation framework to acquire high-yield properties while mitigating legal title risks.

---

## 🔬 Methodology & Data Preprocessing Pipeline

The dataset integrates raw property listings from 5 distinct regional markets (Jakarta, Bogor, Depok, Tangerang, and Bekasi), processed through a systematic data hygiene pipeline:

1. **Unit Standardization & Schema Alignment:** Resolved ambiguous unit scales in raw listings (notably price values and building/land dimensions in Depok and Tangerang), standardizing all currency to Indonesian Rupiah (`IDR`) and spatial metrics to square meters (`m²`).
2. **Noise & Uninformative Column Stripping:** Removed artifact index columns (such as `Unnamed`), deduplicated scraped records, and regularized categorical labels (property titles and cardinal orientation).
3. **Missing Value Imputation & Outlier Segregation:** Handled incomplete property specifications and isolated large-scale land outliers (*lahan luas > 3,000 m²*) for targeted investment banking analysis.
4. **Unified Multi-City Integration (`dataGab`):** Merged cleaned regional sub-tables into a master dataset (`dataGab`) for comparative cross-city exploratory analysis using statistical distributions (*Catplot, Barplot, Histplot, Swarmplot, Scatterplot*).

---

## 📊 Key Findings

### 1. Cross-Regional Property Market Comparison

| City / Region | Price Distribution Characteristics | Listing Volume | Market Dynamics & Strategic Persona |
| :--- | :--- | :---: | :--- |
| **Jakarta** | Broadest dispersion; highest concentration of ultra-luxury properties | Moderate | National economic and financial hub; driven by extreme land scarcity and continuous urban migration |
| **Bogor** | Concentrated in budget-friendly brackets (< Rp 2 Billion) | **Highest** | Most liquid residential volume; strong preference for tranquil, family-oriented suburban living |
| **Tangerang** | Upper-middle price distribution with high variance | High | Rapid commercial development; premier suburban commuter belt with fast transit access to Central Jakarta |
| **Depok** | Strongly clustered in affordable entry-level tiers (< Rp 2 Billion) | Moderate | Vital educational and commuter corridor with robust demand from first-time home buyers |
| **Bekasi** | Highly affordable, competitive baseline pricing | Moderate-Low | Major industrial and manufacturing support hub offering stable, economical family housing |

---

### 2. High-Demand Property Archetype (Best-Selling Profiles)

Empirical distribution analysis across the unified dataset identifies the highest-velocity residential properties:

| Physical Parameter | Highest-Demand Characteristic | Business & Market Interpretation |
| :--- | :--- | :--- |
| **Building Area (*Luas Bangunan / LB*)** | `< 100 m²` | Compact, minimalist floor plans dominate; minimizes maintenance and upfront purchase barriers |
| **Land Area (*Luas Tanah / LT*)** | `< 500 m²` (predominantly < 150 m²) | Strong consumer preference for compact modern landed houses (*rumah tapak*) in suburban clusters |
| **Bedrooms (*Kamar Tidur / KT*)** | 2 to 3 Bedrooms | Ideal layout for nuclear families, the largest demographic segment in the housing market |
| **Bathrooms (*Kamar Mandi / KM*)** | 2 to 4 Bathrooms | Standard residential convenience accommodating daily family routines |
| **Carport Capacity** | 1 Vehicle | Standardized off-street parking for private family cars |
| **Electrical Capacity** | `2,200 VA` to `4,400 VA` | Optimal utility threshold for middle-class household electronic appliances and air conditioning |
| **Cardinal Facing (*Arah Hadap*)** | **East-Facing (*Menghadap Timur*)** | Maximizes natural morning sunlight while avoiding intense afternoon heat |

---

## 💡 Strategic Recommendations for Management & Data Engineering

### 1. Data Governance for Data Engineering (DE) & Database Administration (DBA)
* **Strict Input Validation Schemas:** Implement mandatory input validation at data ingestion points with explicit units (e.g., Price in Millions of IDR, Land/Building Area in $\text{m}^2$, Electricity in VA).
* **Elimination of Schema Drift:** Deprecate unindexed artifact fields (`Unnamed`), enforce *regex* constraints on categorical fields (orientation and certificate types), and automate ETL pipelines across regional branch databases.
* **Hierarchical Spatial Normalization:** Normalize geographic entities into a structured relational hierarchy (*Province > Regency/City > District / Kecamatan > Sub-district / Kelurahan*) to unlock micro-spatial geospatial analytics.

### 2. Strategic Branch Expansion: Prioritize Bogor
* **Data Justification:** Bogor accounts for the largest aggregate listing volume across the metropolitan area, signaling high transaction velocity and market depth.
* **Commercial Impact:** Establishing RPPI's next branch office in Bogor positions the firm closest to high-volume residential sellers and family buyers, maximizing transaction commission revenues.

### 3. Rp 25 Billion Investment Allocation Strategy
* **High-Liquidity Multi-Unit Portfolio (< Rp 2 Billion):** Allocate the majority of capital to acquire residential units priced under Rp 2 Billion within the **Depok, Bogor, and Bekasi** corridors. This segment commands the broadest buyer base, ensuring rapid liquidity and minimal holding period risk during resale.
* **Priority on Secure Land Titling:** Focus acquisitions strictly on freehold property titles—**SHM (*Sertifikat Hak Milik*)** or complete bundles (**SHM + IMB/PBG + PBB**)—to guarantee legal safety and facilitate mortgage financing (KPR) for subsequent buyers.
* **Strategic Land Subdivision (*Kavling / Land Banking*):** Selectively allocate capital to discounted, oversized land plots (outliers $> 3,000 \text{ m}^2$) to subdivide (*pecah sertifikat*) into ready-to-build residential parcels, unlocking exponential capital gain margins.
