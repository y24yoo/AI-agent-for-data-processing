# AI-Powered Data Cleaning Pipeline

## Project Overview

This project is an AI-powered automated data cleaning pipeline built using:

- Python
- FastAPI
- Streamlit
- OpenAI
- LangGraph
- PostgreSQL
- Pandas

The system supports cleaning data from multiple sources including:

- CSV files
- Excel files
- PostgreSQL databases
- APIs

The pipeline combines:

1. Rule-based preprocessing
2. AI-powered intelligent cleaning

to automate data preparation tasks.

---

# Features

- Upload CSV and Excel files
- Connect to PostgreSQL databases
- Fetch data from APIs
- Handle missing values
- Remove duplicates
- Fix data types
- AI-based data cleaning using OpenAI
- Interactive UI with Streamlit
- REST API using FastAPI

---

# Project Architecture

```text
                ┌──────────────────┐
                │   Data Sources   │
                │------------------│
                │ CSV / Excel      │
                │ PostgreSQL       │
                │ APIs             │
                └────────┬─────────┘
                         │
                         ▼
              ┌────────────────────┐
              │  Data Ingestion    │
              │ data_ingestions.py │
              └────────┬───────────┘
                       │
                       ▼
             ┌─────────────────────┐
             │ Rule-Based Cleaning │
             │ data_cleaning.py    │
             └────────┬────────────┘
                      │
                      ▼
             ┌─────────────────────┐
             │ AI Cleaning Agent   │
             │ ai_agent.py         │
             └────────┬────────────┘
                      │
          ┌───────────┴────────────┐
          ▼                        ▼
 ┌────────────────┐      ┌────────────────┐
 │ FastAPI Backend│      │ Streamlit UI   │
 │ backend.py     │      │ app.py         │
 └────────────────┘      └────────────────┘
```

---

# Folder Structure

```text
project/
│
├── app.py
├── requirements.txt
├── .env
│
├── data/
│   ├── sample_data.csv
│   └── sample_data.xlsx
│
├── scripts/
│   ├── ai_agent.py
│   ├── backend.py
│   ├── data_cleaning.py
│   ├── data_ingestions.py
│   ├── main.py
│   └── test_postgres_connection.py
│
└── README.md
```

---

# Installation

## 1. Clone the Repository

```bash
git clone <repository_url>
cd project
```

---

## 2. Create Virtual Environment

### Using venv

```bash
python -m venv ai_data_cleaning_env
```

### Activate Environment

#### Windows

```bash
ai_data_cleaning_env\Scripts\activate
```

#### Linux/Mac

```bash
source ai_data_cleaning_env/bin/activate
```

---

# 3. Install Dependencies

```bash
pip install -r requirements.txt
```

Additional installations:

```bash
pip install langchain-openai
pip install aiohttp
pip install python-dotenv
pip install langgraph
pip install python-multipart
pip install psycopg2
```

---

# Environment Variables

Create a `.env` file:

```env
OPENAI_API_KEY=your_openai_api_key
```

---

# PostgreSQL Setup

Install:

- PostgreSQL
- PGAdmin

Create:

- Database
- Table
- Sample records

Example:

```sql
CREATE DATABASE demo_db;

CREATE TABLE my_table (
    id INT,
    name VARCHAR(50),
    age INT,
    city VARCHAR(50),
    salary FLOAT
);
```

Insert sample data:

```sql
INSERT INTO my_table VALUES
(1, 'John', 25, 'New York', 50000),
(2, 'Alice', NULL, 'Chicago', 60000),
(3, 'Bob', 30, NULL, 70000);
```

---

# File Explanations

## `data_ingestions.py`

Responsible for loading data from:

- CSV
- Excel
- PostgreSQL
- APIs

### Main Functions

```python
load_csv()
load_excel()
connect_database()
load_from_database()
fetch_from_api()
```

---

## `data_cleaning.py`

Performs rule-based preprocessing.

### Cleaning Tasks

- Handle missing values
- Remove duplicates
- Fix data types

### Main Functions

```python
handle_missing_values()
remove_duplicates()
fix_data_types()
clean_data()
```

---

## `ai_agent.py`

Implements AI-powered cleaning using:

- OpenAI
- LangChain
- LangGraph

### Responsibilities

- Create AI workflow
- Process data batches
- Generate AI-cleaned output

### Components

```python
CleaningState
AIAgent
create_graph()
process_data()
```

---

## `backend.py`

FastAPI backend server.

### API Endpoints

| Endpoint | Purpose |
|---|---|
| `/clean-data` | Clean CSV/Excel |
| `/clean-db` | Clean database query results |
| `/clean-api` | Clean API data |

---

## `main.py`

Standalone script for testing the full pipeline.

### Tests

- CSV cleaning
- Excel cleaning
- Database cleaning
- API cleaning

---

## `test_postgres_connection.py`

Used to verify PostgreSQL connectivity.

---

## `app.py`

Streamlit frontend UI.

### Features

- Upload files
- Enter DB credentials
- Provide API URLs
- View cleaned output

---

# Running the Project

## Step 1: Start FastAPI Backend

```bash
uvicorn scripts.backend:app --reload
```

Backend URL:

```text
http://127.0.0.1:8000/docs
```

---

## Step 2: Start Streamlit Frontend

```bash
streamlit run app.py
```

Frontend URL:

```text
http://localhost:8501
```

---

# Testing the APIs

## Clean CSV/Excel

### Endpoint

```text
POST /clean-data
```

Upload file and execute.

---

## Clean Database Data

### Endpoint

```text
POST /clean-db
```

Example request:

```json
{
  "db_url": "postgresql://postgres:admin@localhost:5432/demo_db",
  "query": "SELECT * FROM my_table"
}
```

---

## Clean API Data

### Endpoint

```text
POST /clean-api
```

Example request:

```json
{
  "api_url": "https://jsonplaceholder.typicode.com/posts"
}
```

---

# Pipeline Flow

```text
User Input
    ↓
Data Ingestion
    ↓
Pandas DataFrame
    ↓
Rule-Based Cleaning
    ↓
AI-Powered Cleaning
    ↓
FastAPI Response
    ↓
Streamlit Display
```

---

# Technologies Used

| Technology | Purpose |
|---|---|
| Python | Core language |
| Pandas | Data processing |
| NumPy | Numerical operations |
| FastAPI | Backend APIs |
| Streamlit | Frontend UI |
| PostgreSQL | Database |
| SQLAlchemy | DB connection |
| OpenAI | AI cleaning |
| LangChain | LLM orchestration |
| LangGraph | AI workflow |

---

# Future Improvements

- Support multiple databases
- Add authentication
- Add batch processing
- Export cleaned data
- Add data profiling dashboard
- Add anomaly detection
- Add Docker deployment
- Add cloud deployment

---

# Common Errors

## Missing OpenAI Key

```text
ValueError: OPENAI_API_KEY missing
```

### Solution

Add `.env` file correctly.

---

## psycopg2 Error

```text
ModuleNotFoundError: No module named psycopg2
```

### Solution

```bash
pip install psycopg2
```

---

## File Upload Error

Ensure uploaded file is:

- `.csv`
- `.xlsx`

---

# Example Output

```json
[
  {
    "id": 1,
    "name": "John",
    "age": 25,
    "city": "New York",
    "salary": 50000
  }
]
```

---

# Conclusion

This project demonstrates how AI agents can automate data cleaning workflows by combining:

- Traditional preprocessing
- AI reasoning
- Backend APIs
- Interactive UI

It provides a scalable foundation for building intelligent data engineering pipelines.
