# Python LangGraph Migration (OpenAI)

This folder contains a Python LangGraph migration of the Ballerina travel planner agent.

## Features Parity
- Tool-calling agent for hotel search, booking, and policy queries
- Pinecone policy retrieval with OpenAI embeddings
- `/travelPlanner/chat` endpoint for the React frontend
- CORS settings mirroring the Ballerina service

## Setup

```bash
cd Lab-02-building-travel-planner/ai_backends/agent/python_migration
python -m venv .venv
source .venv/bin/activate
pip install -r requirements.txt
cp .env.example .env
```

Update `.env` with real values.

## Run

```bash
uvicorn app:app --host 0.0.0.0 --port 9090
```

## Notes
- `query_hotel_policy_tool` expects Pinecone metadata with a `content` field and `hotelId` filter, matching the ingest pipeline in `ai_backends/ingest/python/ingest.py`.
- The weather tool is a placeholder. Provide `WEATHER_MCP_URL` if you expose an HTTP wrapper for the MCP server.
