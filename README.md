# Rashed | AI-Assisted Water Conservation

**Rashed (رشد)** is a bilingual AI-assisted water conservation platform designed to help Saudi households understand their water consumption, analyze water bills, identify unusual consumption patterns, and explore practical water-saving strategies.

The platform combines deterministic backend calculations with Google Gemini AI to extract information from water bills, interpret consumption patterns, and generate personalized conservation recommendations.

**My Role:** Team Lead | AI Component & Research | Team of 5

**Live Demo:** [Rashed Web Application](https://rashed-water.replit.app)

**GitHub Repository:** [hanan-alharbi-cs/Rashed](https://github.com/hanan-alharbi-cs/Rashed)

---

## Project Overview

Household water consumption can be difficult to monitor without clear insights into billing information, historical usage, and expected consumption levels.

Rashed addresses this challenge through an integrated platform that brings together water-bill extraction, household consumption analysis, anomaly detection, forecasting, savings estimation, and AI-assisted recommendations.

The application is designed to help households understand their water usage, recognize unusual consumption patterns, and make more informed decisions about water conservation.

## Problem Statement

Households may struggle to:

- Understand the information displayed on water bills.
- Track and compare monthly water consumption.
- Identify unusual increases in water usage.
- Recognize consumption patterns that may indicate potential leaks.
- Estimate the impact of water-saving actions.
- Translate consumption data into practical conservation decisions.

## Proposed Solution

Rashed provides a bilingual web application that processes water-bill information and combines it with household characteristics and historical consumption records.

The platform uses Google Gemini for image-based bill extraction and AI-generated interpretations, while deterministic backend calculations handle numerical analysis, consumption baselines, anomaly indicators, forecasts, and savings estimates.

This separation helps maintain consistency in numerical calculations while using AI to make the results easier to understand.

---

## Key Features

### 1. AI-Powered Water Bill Extraction

- Upload water-bill images or meter images.
- Extract structured information using Google Gemini multimodal capabilities.
- Identify available consumption and billing information.
- Return structured JSON data for backend processing.
- Validate extracted values before using them in analysis.

### 2. Household Consumption Baseline

- Estimate expected household consumption.
- Consider household size and property type.
- Account for garden and swimming-pool characteristics.
- Incorporate historical consumption when available.
- Compare actual consumption against an estimated household range.

### 3. Water Consumption Analysis

- Analyze current and previous consumption.
- Calculate percentage changes between bills.
- Compare household consumption against its estimated baseline.
- Classify consumption as above, below, or within the expected range.

### 4. Potential Leak and Anomaly Detection

- Identify consumption above the household baseline.
- Detect increases exceeding 20% compared with the previous bill.
- Generate potential leak alerts.
- Display risk indicators to help households investigate unusual usage.

These alerts indicate unusual consumption patterns and do not confirm that a physical water leak exists.

### 5. Consumption Forecasting

- Estimate month-end water consumption.
- Use a linear daily-rate calculation.
- Present projected consumption through visual charts.

### 6. AI-Powered Recommendations

- Generate personalized water conservation recommendations.
- Suggest possible explanations for increased consumption.
- Provide practical household water-saving guidance.
- Organize recommendations by category and priority.

### 7. Water Conservation Plans

- Generate practical conservation actions.
- Support household-specific recommendations.
- Organize suggested actions into manageable steps.
- Support tracking of recommendation completion.

### 8. Savings Estimation

- Estimate potential water savings.
- Calculate estimated financial savings.
- Compare current consumption with a target reduction level.
- Apply configured water tariff tiers.

### 9. What-If Simulation

- Explore alternative consumption scenarios.
- Simulate target monthly consumption levels.
- Compare current and target consumption.
- Estimate potential water and financial savings.

### 10. AI Water Assistant

- Provide an interactive bilingual assistant.
- Answer questions using available household consumption information.
- Retrieve recent and historical consumption records.
- Explain current analysis results and alerts.
- Provide conservation recommendations.
- Support savings calculations and What-If simulations.
- Use Gemini Function Calling to access specific backend tools.

The assistant is connected to 11 function-calling tools:

1. `get_household_profile` – Retrieve household profile information.
2. `get_recent_consumption` – Retrieve recent consumption records.
3. `get_consumption_history` – Retrieve historical consumption data.
4. `get_latest_bill` – Retrieve the latest water bill.
5. `get_latest_analysis` – Retrieve the latest consumption analysis.
6. `get_active_alerts` – Retrieve active alerts.
7. `get_forecast` – Retrieve consumption forecasts.
8. `get_recommendations` – Retrieve conservation recommendations.
9. `get_verified_water_reference` – Retrieve verified water-related references.
10. `calculate_savings` – Calculate estimated savings.
11. `run_what_if_simulation` – Run alternative consumption scenarios.

### 11. Interactive Dashboard and Reports

- Display household consumption summaries.
- Visualize consumption trends.
- Present analysis results and alerts.
- Show forecasts and savings estimates.
- Provide access to different consumption-analysis modules.

### 12. Bilingual Interface

- Arabic and English language support.
- Right-to-left (RTL) layout for Arabic.
- Left-to-right (LTR) layout for English.
- Language preference stored locally.

---

## Application Screenshots

The following screenshots showcase the main interfaces and features of Rashed.

### 1. Home Page

![Rashed Home Page](images/Home%20Page.png)

### 2. Bill Upload

![Bill Upload](images/Bill%20Upload.png)

### 3. Consumption Reports

![Consumption Reports](images/Reports.png)

### 4. Additional Analysis Tools

![Additional Analysis Tools](images/Reports1.png)

### 5. Conservation Plan

![Conservation Plan](images/Conservation%20Plan.png)

### 6. AI Assistant

![AI Assistant](images/AI%20Assistant.png)

---

## How It Works

Rashed follows a workflow that combines image extraction, backend validation, deterministic consumption analysis, and AI-assisted interpretation.

1. **Bill Upload:** The user uploads a water-bill image or selects the demo mode.
2. **AI Extraction:** The backend sends the image to Google Gemini to extract structured billing information.
3. **Structured Data Validation:** The extracted fields are validated using deterministic backend rules.
4. **Household Data Retrieval:** The system retrieves household characteristics and historical consumption records.
5. **Consumption Analysis:** Backend calculations determine household baselines, consumption changes, and anomaly indicators.
6. **AI Interpretation:** Gemini interprets the available analysis results and generates possible explanations and recommendations.
7. **Data Storage:** The system stores the bill information, analysis results, and related records in PostgreSQL.
8. **Dashboard Presentation:** The application presents the results through its dashboard, charts, reports, alerts, and recommendations.

---

## System Architecture

Rashed follows a client-server architecture consisting of a React web application, an Express REST API, a PostgreSQL database, and Google Gemini AI integration.

```mermaid
flowchart TD
    A[User] --> B[React Web Application]

    B --> C[Express REST API]

    C --> D[Authentication]
    C --> E[Bill Upload]

    E --> F[Google Gemini]
    F --> G[Structured Bill Data]

    G --> H[Deterministic Validation]

    H --> I[Consumption Analysis]

    I --> J[Household Baseline]
    I --> K[Anomaly Detection]
    I --> L[Consumption Forecast]
    I --> M[Savings Estimation]

    J --> N[(PostgreSQL Database)]
    K --> N
    L --> N
    M --> N

    N --> O[Dashboard and Reports]

    C --> P[AI Water Assistant]
    P --> Q[Gemini Function Calling]
    Q --> N
