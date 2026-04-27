# LLM Relational Data Evaluation Project
This project was developed for the assignment of the course Models and Practice of Neural Table Representations". 
The goal is to compare two different paradigms for querying relational data using Large Language Models (LLMs):
1. **Text-to-SQL Pipeline**: the LLM generates a SQL query that is executed against a local SQLite database;
2. **Direct Table-QA Pipeline**: the LLM reads serialized table content and directly generates the answer.

## Repository Structure
- `spider_evaluation_pipeline.ipynb`: main notebook containing the pipelines and evaluation logic;
- `requirements.txt`: list of required Python libraries;
- `merged_queries.json`: a curated subset of questions from the Spider benchmark;
- `concert_singer.sqlite` & `student_1.sqlite`: SQLite databases used for testing.

## Technical Details
The project is implemented in Google Colab using the Llama-3.3-70b model via the Groq API. This model was chosen for its high performance in logical reasoning and SQL code generation.

## Installation
To install the necessary dependencies, run:
```bash
pip install -r requirements.txt
```

## Configuration
To run the notebook:
1. Upload the `.sqlite` database files and the `.json` query file to your Colab environment.
2. Insert your Groq API Key in the client configuration cell.

## Evaluation Methodology
Following the Qatch philosophy, the evaluation measures data output accuracy using:
- Cell Precision
- Cell Recall
- Tuple Cardinality

The system implements the Oracle Relevant Tables technique: for each question, the LLM is provided only with the specific tables and columns required, dynamically extracted by parsing the Ground Truth SQL (using the `sqlparse` library).
