# Lab 02: Building a Travel Planner with Generative AI

This repository contains the codebase for the WSO2Con Asia 2nd lab on building generative AI applications. The use case demonstrates creating an intelligent agent that provides personalized trip planning capabilities.

## Overview

This project showcases a complete travel planning system where an AI agent acts as both the intelligent backend and Backend-for-Frontend (BFF), coordinating with multiple business APIs to provide personalized travel recommendations.

### Architecture

- **Python Agent** (`ai_backends/agent/python_migration/`): FastAPI/LangGraph version of the main agent (BFF)
- **Frontend** (`frontend/`): React-based web application for user interaction
- **O2 Business APIs (Python)** (`o2-business-apis-python/`): FastAPI versions of the booking and search services
- **Agent as BFF**: The agent serves as the single point of entry, orchestrating calls to business APIs

## Project Structure

```
Lab-02-building-travel-planner/
├── ai_backends/                    # AI agent implementations
│   └── agent/
│       └── python_migration/        # FastAPI + LangGraph agent
├── frontend/                      # React frontend application
├── o2-business-apis-python/        # Python versions of booking/search services
└── resources/                     # API specifications and prompts
```

## Prerequisites

- **Python**: 3.10+ (for the agent/APIs)
- **Node.js**: Version 22+ ([Download](https://nodejs.org/))
- **npm**: Comes with Node.js
- **PostgreSQL**: Required for personalization data (see `resources/create_tables.sql`)

## Getting Started

### 0. (Optional) Initialize PostgreSQL

Personalization uses PostgreSQL. Create the `user_activities` table once:

```bash
psql -d travel_planner -f resources/create_tables.sql
```

### 1. Start the Business APIs

Each business API runs on a different port. Start them in separate terminals:

```bash
cd o2-business-apis-python/booking-api
python -m venv .venv
source .venv/bin/activate
pip install -r requirements.txt
uvicorn app:app --host 0.0.0.0 --port 9081
```

```bash
cd o2-business-apis-python/search-api
python -m venv .venv
source .venv/bin/activate
pip install -r requirements.txt
uvicorn app:app --host 0.0.0.0 --port 9083
```

### 2. Start the AI Agent (BFF)

The main agent acts as the Backend-for-Frontend and coordinates with all business APIs:

Setup the configurables required for the agent. Instructions can be found in `ai_backends/agent/python_migration/README.md`.

```bash
cd ai_backends/agent/python_migration
python -m venv .venv
source .venv/bin/activate
pip install -r requirements.txt
uvicorn app:app --host 0.0.0.0 --port 9090
```

The agent will be available at: `http://localhost:9090`.

### 3. Start the Frontend

Prerequisite: 

1. Asgradeo public client application should be created (https://wso2.com/asgardeo/docs/references/app-settings/oidc-settings-for-app/)

2. Update the `.env` file in the `frontend` directory with the values as needed.

```bash
cd frontend
npm install
npm start
```

The frontend will be available at: `http://localhost:3001`
