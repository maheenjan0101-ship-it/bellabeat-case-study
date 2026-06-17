# Bellabeat Consumer Behavior Case Study
**An End-to-End Data Analytics Portfolio Project**

## Executive Summary
This case study analyzes public smart-tracker data to uncover distinct consumer physical activity, sedentary, and sleep habits. Utilizing **Python (Pandas, NumPy, Matplotlib, Seaborn)** for algorithmic data cleaning and exploratory data analysis, and **Power BI Desktop** for semantic modeling and interactive visualization, the project maps a detailed 7-day lifestyle cycle. The ultimate insights are translated into tactical, high-yield product and digital marketing recommendations to drive Bellabeat's subscription ecosystem and global brand equity.

---

## Phase 1: Ask (Defining the Business Task)

### 1. The Core Business Objective
The objective is to analyze non-Bellabeat smart device data (Fitbit) to uncover distinct consumer behavioral trends across activity, sedentary behavior, and sleep patterns. These insights are strategically applied to Bellabeat's dual-tier business model:
**Hardware Layer:** Positioning the screenless, fashion-forward Bellabeat Leaf as the primary physical data-collection gateway.
**Software Layer:** Positioning the subscription-based Bellabeat Membership as the essential digital ecosystem for personalized health and wellness guidance.

### 2. Stakeholder Requirements
**Urška Sršen (Co-founder & Chief Creative Officer):** Requires high-level consumer behavior trends and data-driven marketing narratives on when and how to target digital ads.
**Sando Mur (Co-founder & Mathematician):** Demands structurally sound, mathematically backed analytical evidence that explicitly accounts for data limitations and integrity audits.
**Bellabeat Analytics Team:** Requires clean, well-documented, and reproducible code structures.

---

## Phase 2: Prepare (Data Sourcing & Quality Audit)

### 1. Data Metadata & Architecture
**Source:** Public domain dataset via Möbius on Kaggle (FitBit Fitness Tracker Data).
**Origin:** Distributed user tracking survey hosted via Amazon Mechanical Turk.
**Temporal Scope:** April 12, 2016 – May 12, 2016 (31-day tracking window).
**Monitored Tables:** Relational tables loaded include `dailyActivity_merged.csv`, `sleepDay_merged.csv`, and `hourlySteps_merged.csv`.
**Key Mapping:** `Id` acts as the Primary Key across all tables, while `ActivityDate` / `Date` serves as the Composite Key to link daily movement intensity directly to corresponding sleep windows.

### 2. The ROCCC Data Audit
**Reliable (POOR):** Contains data for only 33 unique users for activity, dropping to 24 for sleep, introducing potential selection bias.
**Original (LOW):** Third-party crowdsourced data rather than direct primary telemetry.
**Comprehensive (MEDIUM):** Features rich intraday and hourly distributions, but completely lacks demographic parameters (age, gender, location).
**Current (POOR):** Collected in 2016; functions as a proxy baseline rather than a reflection of modern wearable engagement.
**Cited (GOOD):** Clearly documented, publicly dedicated domain data (CC0).

### 3. Portfolio Strategic Pivots
**The Gender Blindness Pivot:** Because data is gender-anonymous, we treat it as a general proxy for adult movement but filter creative solutions through a female-first lifestyle lens.
**The Drop-off Friction Pivot:** 9 out of 33 users failed to track sleep data. This tracking drop-off is isolated as a key behavioral metric to market the Bellabeat Leaf's extended 6-month battery life and zero-friction jewelry design.

---

## Phase 3: Process (Data Cleansing Pipeline in Python)

Python 3 within a Google Colab environment was leveraged to ensure reproducible cleaning, prevent spreadsheet manual errors, and handle long intraday tracking arrays smoothly.

### Code Execution Ledger:

#### Cell 1: Import Libraries & Load Raw Datasets
```python
import pandas as pd
import numpy as np

# Load all three raw datasets
activity_df = pd.read_csv('dailyActivity_merged.csv')
sleep_df = pd.read_csv('sleepDay_merged.csv')
hourly_steps = pd.read_csv('hourlySteps_merged.csv')

print("All 3 datasets successfully loaded into the workspace!")
