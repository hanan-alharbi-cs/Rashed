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
```

### Frontend – React Web Application

The frontend provides the bilingual user interface and household water-management experience.

Its responsibilities include:

- User authentication interfaces.
- Water-bill and meter-image uploads.
- Household profile and meter management.
- Consumption analysis and visualizations.
- Baseline and forecast presentation.
- Leak detection and alert interfaces.
- Conservation plans and savings estimation.
- What-If simulation.
- AI assistant interaction.
- Reports and settings.

### Backend – Express REST API

The backend handles application requests and business logic through Express.

Its responsibilities include:

- Authentication and session management.
- User and household management.
- Water-bill image uploads.
- Gemini integration and structured extraction.
- Extracted data validation.
- Consumption analysis.
- Household baseline calculations.
- Anomaly and potential leak detection.
- Forecasting and savings calculations.
- Conservation recommendations and plans.
- AI assistant and function-calling operations.

### Database Layer

Rashed uses PostgreSQL as its relational database.

Drizzle ORM manages database queries and schema definitions.

The database stores:

- User and household information.
- Household members and property characteristics.
- Water bills and consumption records.
- Meters and meter readings.
- Consumption analyses.
- Alerts and anomaly records.
- Forecasts and recommendations.
- Savings estimates and tariff configurations.
- AI assistant conversations and messages.

### AI Integration

Google Gemini is integrated through the Google Gen AI SDK.

Gemini is used for:

- Multimodal water-bill information extraction.
- Producing structured JSON responses.
- Interpreting consumption-analysis results.
- Suggesting possible reasons for increased consumption.
- Generating personalized recommendations.
- Supporting the AI assistant through Function Calling.

The backend remains responsible for numerical calculations and validation.

---

## Technology Stack

### Frontend Development

| Component | Technologies |
|---|---|
| Programming Language | TypeScript 5.9 |
| UI Library | React 19 |
| Build Tool | Vite |
| Styling | Tailwind CSS 4 |
| UI Components | Radix UI |
| Data Fetching & State | TanStack Query |
| Charts & Visualization | Recharts |
| Routing | Wouter |
| Icons | Lucide React |
| Localization | Custom Arabic/English i18n |
| Form Handling | React Hook Form |
| Schema Validation | Zod |

### Backend Development

| Component | Technologies |
|---|---|
| Runtime | Node.js 24 |
| Programming Language | TypeScript |
| Backend Framework | Express 5 |
| API Architecture | REST APIs |
| File Upload | Multer |
| Authentication | JWT, bcrypt |
| Session Management | Express Session |
| Session Storage | PostgreSQL Session Store |
| Logging | Pino, Pino HTTP |
| Middleware | CORS, Cookie Parser |

### Artificial Intelligence & Gemini Integration

| Component | Technologies |
|---|---|
| AI Platform | Google Gemini |
| AI Model | Gemini 2.5 Flash |
| SDK | Google Gen AI SDK |
| Image Processing | Gemini Multimodal Input |
| Structured Output | JSON Responses |
| AI Assistant | Gemini Function Calling |
| AI Integration | Replit AI Integrations |

### Database & API Development

| Component | Technologies |
|---|---|
| Database | PostgreSQL |
| ORM | Drizzle ORM |
| Database Client | node-postgres (pg) |
| API Specification | OpenAPI |
| API Client Generation | Orval |
| Schema Validation | Zod |
| API Types | Generated TypeScript Types |
| Workspace Management | pnpm Workspaces |

---

## AI and Backend Design

One of the key design principles in Rashed is separating AI interpretation from deterministic calculations.

### Google Gemini Responsibilities

Gemini is responsible for AI-assisted tasks, including:

- Extracting visible information from water bills and meter images.
- Producing structured JSON responses.
- Interpreting consumption-analysis results.
- Suggesting possible reasons for increased consumption.
- Generating personalized water conservation recommendations.
- Supporting interactive conversations through Function Calling.

### Deterministic Backend Responsibilities

The backend is responsible for numerical calculations and validation, including:

- Validating extracted billing information.
- Calculating consumption changes.
- Estimating household consumption baselines.
- Detecting unusual consumption patterns.
- Calculating estimated costs and savings.
- Generating consumption forecasts.
- Applying configured tariff tiers.

This separation helps keep numerical and financial calculations consistent and independently verifiable.

---

## Important Implementation Details

### 1. Household Consumption Baseline

Rashed uses a GASTAT 2023 statistical reference of:

**102.1 liters per person per day.**

The household baseline calculation considers:

- Household member count.
- Property type.
- Garden availability.
- Swimming-pool availability.
- Historical consumption records.

When historical consumption is available, the system combines the household profile estimate with historical consumption information.

The baseline calculation uses a weighted approach that gives more weight to historical consumption when available.

The resulting baseline is an estimated household consumption range, not a strict consumption limit.

### 2. Potential Leak Detection

The system identifies unusual consumption when:

- Current consumption exceeds the household baseline maximum.
- Consumption increases by more than 20% compared with the previous bill.

These conditions generate potential leak and anomaly indicators.

The alerts are intended to help users investigate unusual water consumption and do not independently confirm a physical leak.

### 3. Consumption Forecasting

The current implementation uses a simple linear daily-rate calculation to estimate month-end consumption.

The forecast is based on observed consumption and elapsed billing-period information.

It is not currently generated by a trained forecasting machine-learning model.

### 4. Savings Estimation

The backend calculates estimated water and financial savings by comparing current consumption with a selected target consumption level.

The calculation uses configured tariff tiers.

Monetary results are estimates because the configured tariff is treated as unverified.

### 5. Gemini Function Calling

The AI assistant uses 11 backend tools to retrieve information and perform supported calculations.

The available tools include household profile retrieval, recent and historical consumption retrieval, latest bill and analysis retrieval, active alerts, forecasts, recommendations, verified water references, savings calculations, and What-If simulations.

The tools connect Gemini conversations with relevant household data and backend calculations.

### 6. Structured Bill Extraction and Validation

The Gemini integration extracts structured fields from uploaded bill or meter images.

The extraction response can contain:

- Document type.
- Current consumption.
- Previous consumption.
- Billing period.
- Bill amount.
- Meter reading.
- Reading date.
- Extraction confidence.

The backend validates extracted values before they are used in further calculations.

Gemini is instructed to extract only visible information and not to perform arithmetic or calculate costs.

Uploaded document content is treated as untrusted input, and embedded instructions are not followed.

---

## My Role & Contribution

**Role: Team Lead | AI Component & Research**

I served as the Team Lead of Rashed, helping guide the team's work and coordinate efforts toward achieving the project objectives.

In addition to my leadership responsibilities, I was responsible for the AI-focused part of the project, including research and gathering relevant information to support its development.

My contributions included:

- **Team Leadership:** Leading a team of five, coordinating tasks, and helping align our work with the project's objectives.
- **AI Component:** Taking responsibility for the AI-related component and researching how Google Gemini could support water-bill data extraction, consumption analysis, and personalized conservation recommendations.
- **Research & Information Gathering:** Researching household water consumption, water conservation, and relevant supporting information and references.
- **AI Use Cases:** Identifying opportunities to apply AI to make water-consumption data easier to understand and support informed household decisions.
- **Project Coordination:** Helping coordinate the team's work and maintain alignment between the proposed solution and its implementation.

Through this experience, I developed my skills in team leadership, AI-focused research, problem-solving, technical collaboration, and applying AI technologies to a real-world sustainability challenge.

---

## Data Sources & References

The project uses the following references to support its water-consumption analysis and recommendations.

### 1. GASTAT – Water Accounts Publication 2023

[Read the GASTAT Water Accounts Publication 2023](https://www.stats.gov.sa/documents/20117/2067030/Water%2BAccounts%2BPublication%2B2023%2BEN.pdf)

Used as a statistical reference for household water consumption, including the reported 102.1 liters per person per day benchmark.

### 2. National Water Company – Rasshid Initiative

[Read about the NWC Rasshid Initiative](https://www.nwc.com.sa/EN/HousingSector/Pages/RashedInitiative.aspx)

Included as a supporting reference for household water conservation and leak awareness.

### 3. Ministry of Environment, Water and Agriculture – National Water Strategy

[Read the National Water Strategy](https://www.mewa.gov.sa/en/Ministry/Agencies/TheWaterAgency/Topics/Pages/Strategy.aspx)

Provides broader context about water-demand management and water-sector objectives.

### 4. MEWA – Water Innovation Trends Report

[Read the Water Innovation Trends Report](https://www.mewa.gov.sa/en/Ministry/Agencies/AgencyForInnovation/Topics/Pages/slmReportIII.aspx)

Provides supporting context about smart leakage management and water monitoring.

### 5. National Water Company – Mobile Application

[Visit the NWC Mobile Application page](https://www.nwc.com.sa/EN/HowWeCanHelp/Pages/application.aspx)

Included as a reference to existing water and sanitation services. Rashed is an independent informational and decision-support platform and does not replace official NWC services.

---

## Repository Structure

```text
Rashed/
│
├── artifacts/
│   │
│   ├── rashed/
│   │   └── src/
│   │       ├── pages/
│   │       ├── components/
│   │       ├── hooks/
│   │       ├── lib/
│   │       └── locales/
│   │
│   ├── api-server/
│   │   └── src/
│   │       ├── routes/
│   │       ├── lib/
│   │       └── middlewares/
│   │
│   └── mockup-sandbox/
│
├── lib/
│   │
│   ├── db/
│   │   └── src/
│   │       ├── schema/
│   │       ├── index.ts
│   │       └── seed.ts
│   │
│   ├── api-spec/
│   │
│   ├── api-client-react/
│   │
│   ├── api-zod/
│   │
│   ├── integrations-gemini-ai/
│   │
│   └── integrations/
│
├── scripts/
│
├── package.json
├── pnpm-workspace.yaml
├── tsconfig.json
└── README.md
```

---

## Setup & Development

Rashed is organized as a pnpm workspace containing the frontend, API server, and shared libraries.

### Prerequisites

Make sure the following tools and services are available:

- Node.js 24
- pnpm
- PostgreSQL
- Google Gemini API integration credentials

### 1. Clone the Repository

```bash
git clone https://github.com/hanan-alharbi-cs/Rashed.git

cd Rashed
```

### 2. Install Dependencies

Install the workspace dependencies:

```bash
pnpm install
```

### 3. Configure Environment Variables

The backend requires environment variables for database connectivity, session management, server configuration, and Gemini integration.

Configure the following variables in the API server environment:

```env
DATABASE_URL=your_postgresql_connection_string

SESSION_SECRET=your_session_secret

PORT=8080

AI_INTEGRATIONS_GEMINI_API_KEY=your_gemini_api_key

AI_INTEGRATIONS_GEMINI_BASE_URL=your_gemini_base_url
```

**Environment variable notes:**

- `DATABASE_URL` is required for the PostgreSQL connection.
- `SESSION_SECRET` is required for Express session management.
- `PORT` is required by the API server.
- `AI_INTEGRATIONS_GEMINI_API_KEY` is required for Gemini integration.
- `AI_INTEGRATIONS_GEMINI_BASE_URL` is used when the Gemini integration requires a configured API base URL or proxy.

Do not commit private credentials, API keys, or production secrets to the repository.

### 4. Prepare the Database

Make sure PostgreSQL is running and `DATABASE_URL` is configured.

Push the Drizzle schema to the database:

```bash
pnpm --filter @workspace/db run push
```

This command uses Drizzle Kit to apply the database schema.

### 5. Seed the Database

To populate the database with reference records and sample household data, run:

```bash
pnpm --filter @workspace/db run seed
```

The seed script prepares:

- Water-related reference sources.
- An unverified tariff configuration.
- A demo user and household.
- Demo meter information.
- Synthetic meter readings.
- Synthetic consumption history.
- Sample AI analysis results.
- Potential leak alerts and anomaly records.
- A sample forecast.
- Water conservation recommendations.
- Savings estimates.
- A sample conservation plan.

The seeded demo account is:

```text
Email: demo@rashed.app
Password: demo1234
```

**Note:** The demo account and seeded household records are intended for demonstration and testing. They are not real customer records.

### 6. Start the Backend API

The API server requires its environment variables, including `DATABASE_URL`, `SESSION_SECRET`, `PORT`, and `AI_INTEGRATIONS_GEMINI_API_KEY`.

To build and start the API server:

```bash
pnpm --filter @workspace/api-server run dev
```

The API server uses the configured `PORT` value.

The `dev` script builds the API server before starting it.

### 7. Start the Frontend

In a separate terminal, start the React development server:

```bash
pnpm --filter @workspace/rashed run dev
```

The Vite development server uses port `3000` by default. A different available port can be configured using `PORT`.

### 8. Build the Project

To run the workspace build:

```bash
pnpm run build
```

The root build script runs type checking before building the workspace packages.

### 9. Run Type Checking

To check the workspace TypeScript projects:

```bash
pnpm run typecheck
```

**Local development note:** The frontend and backend run as separate services. A local development setup must route frontend `/api` requests to the API server. Configure an appropriate development proxy or routing layer when running them on separate local ports.

**Session storage note:** The API session configuration expects a PostgreSQL `user_sessions` table and has `createTableIfMissing` disabled. Ensure that this table has been created through the appropriate database setup before running the API server.

---

## Important Notes & Limitations

- Gemini-generated explanations and recommendations are possible interpretations, not confirmed facts.
- Potential leak alerts are based on consumption patterns and predefined thresholds.
- A potential leak alert does not confirm the existence of a physical leak.
- Forecasting currently uses a simple linear method rather than a trained forecasting model.
- Financial calculations are estimates based on the configured tariff.
- The configured tariff is treated as unverified and should not be interpreted as an official confirmed billing amount.
- Demo data is synthetic and should not be confused with actual household consumption.
- The GASTAT consumption reference is a statistical benchmark and not a strict household consumption limit.
- Rashed is a decision-support and awareness platform and does not replace official water-provider services.

---

## Future Improvements

- Expand the availability of verified household consumption data.
- Improve consumption forecasting methods.
- Enhance anomaly detection and household-specific analysis.
- Expand AI assistant capabilities.
- Improve explainability of AI-generated recommendations.
- Strengthen application security and data validation.
- Expand reporting and household water-management features.
- Improve integration with reliable water-consumption data sources.

---

## Project Links

- **Live Application:** [Rashed Web Application](https://rashed-water.replit.app)
- **GitHub Repository:** [hanan-alharbi-cs/Rashed](https://github.com/hanan-alharbi-cs/Rashed)

---

**Rashed — Turning Water Consumption Data into Actionable Insights.**
