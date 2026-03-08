# Dementia Care Hospital Site Selection using PCA & TOPSIS

## Project Overview

This project aims to identify the optimal location for establishing a Dementia Care Hospital using public data and multi-criteria decision-making methods.

With the rapid aging of the population, the number of dementia patients in Korea is steadily increasing. However, only a limited number of dementia care hospitals currently operate nationwide. This project proposes a data-driven framework to identify regions that require additional dementia care hospitals and determine the most suitable hospital location.

The analysis combines Principal Component Analysis (PCA) and the MCDM-TOPSIS method to support evidence-based policy decision-making.

---

## Background

South Korea is rapidly entering a super-aged society. As the elderly population grows, dementia-related healthcare demand is increasing significantly.

Dementia care hospitals provide specialized treatment and management for patients experiencing Behavioral and Psychological Symptoms of Dementia (BPSD). However, only around 20 dementia care hospitals exist nationwide, creating a shortage of specialized medical infrastructure.

This project aims to support policy decision-making by identifying optimal locations for additional dementia care hospitals based on data analysis.

---

## Data

The analysis integrates multiple public datasets related to elderly population and healthcare infrastructure.

Main variables include:

- Elderly population statistics
- Dementia prevalence rate
- Number of dementia patients
- Welfare facility distribution
- Long-term care facility resources
- Elderly population distribution by administrative district
- Public transportation accessibility
- Green space distribution
- Welfare facility locations

Data sources include:

- Korean public data portals
- Health and welfare statistics
- Regional administrative datasets

Due to licensing restrictions, the original datasets are not included in this repository.

--- 


## Analysis Pipeline

Data Collection → Data Preprocessing → PCA (Region Selection) → Hospital Filtering (Ministry of Health Criteria) → TOPSIS (Hospital Ranking) → Final Hospital Selection

---

## Methodology

Two major analytical steps were conducted.

### Step 1: Region Selection using PCA

1. Standardize regional indicators using StandardScaler
2. Perform PCA on regions with existing dementia care hospitals
3. Select principal components based on cumulative explained variance (>90%)
4. Compute weighted composite scores using explained variance ratios

The final regional score was calculated as:

score = 0.66 * PC1 + 0.13 * PC2 + 0.09 * PC3 + 0.06 * PC4

The region with the highest score was selected as the priority region for establishing a dementia care hospital.

---

### Step 2: Hospital Candidate Evaluation using TOPSIS

Hospital candidates were evaluated through two stages.

1. Filtering hospitals based on official dementia care hospital designation criteria (Ministry of Health and Welfare)

2. Multi-criteria evaluation using TOPSIS based on:

- Accessibility (distance to subway stations and bus stops)
- Demand (elderly population distribution)
- Green environment
- Welfare infrastructure

Distances were calculated using:

- Manhattan distance
- Geodesic distance

TOPSIS ranks hospitals based on their distance from the ideal solution and the worst solution.

---

## Analysis Process

Step 1  
Select the most suitable administrative region using PCA.

Step 2  
Identify hospital candidates in the selected region and evaluate them using multi-criteria decision-making methods.

---

## Results

### Region Selection

PCA-based analysis identified **Suwon-si (Gyeonggi Province)** as the most suitable region for establishing an additional dementia care hospital.

### Hospital Ranking (TOPSIS)

Top 3 hospital candidates:

1. Withers Nursing Hospital — Score: 0.79  
2. Major Nursing Hospital  
3. Suwon Samsung Nursing Hospital

These hospitals demonstrated high accessibility, strong demand potential, and favorable surrounding infrastructure.
This framework demonstrates how public healthcare data can be integrated with statistical methods to support location-based policy decision making.

---

## Expected Impact

- Provides a data-driven framework for healthcare policy decision-making
- Supports efficient allocation of medical resources
- Suggests practical directions for expanding dementia care hospital infrastructure

---

## Limitations

- Variable weights were not determined through expert-based methods such as AHP
- Some public datasets had limitations in availability
- Comparative analysis across multiple candidate regions was not conducted

---

## Tech Stack

**Languages & Libraries**

- Python
- Pandas
- Scikit-learn
- Geopy
- Folium
- GeoJSON

**Methods**

- Principal Component Analysis (PCA)
- Multi-Criteria Decision Making (MCDM)
- TOPSIS
- Spatial Data Analysis

---

## Project Structure
dementia-hospital-location-selection
```text
dementia-hospital-location-selection

data
├── raw_data
└── processed_data

notebooks
├── 01_data_collection_and_merge.ipynb
├── 02_data_preprocessing.ipynb
├── 03_pca_region_selection.ipynb
└── 04_topsis_hospital_ranking.ipynb

report
└── final_report.pdf
```
