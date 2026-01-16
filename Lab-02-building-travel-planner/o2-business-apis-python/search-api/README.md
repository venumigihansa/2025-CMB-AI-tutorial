# Python Search API

FastAPI version of the hotel search service. It loads the same mock data from the Ballerina `data_mappings.bal` file.

## Setup

```bash
cd Lab-02-building-travel-planner/o2-business-apis-python/search-api
python -m venv .venv
source .venv/bin/activate
pip install -r requirements.txt
```

## Run

```bash
cd Lab-02-building-travel-planner/o2-business-apis-python/search-api
uvicorn app:app --host 0.0.0.0 --port 9083
```

## Notes
- Data is read from `Lab-02-building-travel-planner/o2-business-apis/search-api/data_mappings.bal`.
- CORS is configured for `http://localhost:3001`.
