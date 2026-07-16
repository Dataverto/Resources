# Naveda Dataset

A sample **DuckDB** database used in the video:

> **Claude Code + Your Data: A Practical Guide to Agentic Analytics**

This dataset is designed to help you explore how AI agents can investigate real business problems using SQL, iterative reasoning, and data validation.

## Contents

```
naveda.duckdb
```

The database contains a fictional eCommerce scenario that can be used to investigate questions such as:

- Why did sales drop?
- Which channel caused the decline?
- Is marketing responsible?
- Is there a checkout issue?
- Which hypotheses are actually supported by the data?

---

# Requirements

No PostgreSQL, MySQL, or database server is required.

All you need is **DuckDB**.

## DuckDB CLI

Install DuckDB from:

https://duckdb.org/docs/installation/

Then open the database:

```bash
duckdb naveda.duckdb
```

## Python

Install DuckDB:

```bash
pip install duckdb
```

Example:

```python
import duckdb

con = duckdb.connect("naveda.duckdb")

con.sql("SHOW TABLES")
```

---

# Using with Claude Code

Once you've opened the project in Claude Code, you can start with a prompt like:

```text
Analyze the structure of naveda.duckdb.

Show me:

- all tables
- columns
- relationships
- the main business metrics available

Do not draw any business conclusions yet.
```

Then move on to business questions:

```text
Sales have dropped compared to last month.

Investigate what happened.

Do not accept the first hypothesis.

Validate every conclusion using SQL queries and explain your reasoning step by step.
```

---

# Purpose

This dataset is intended for practicing **Agentic Analytics**—using AI agents to investigate business problems through an iterative workflow:

- formulate hypotheses
- query the data
- validate findings
- reject incorrect explanations
- reach evidence-based conclusions

The goal is not simply to generate SQL, but to demonstrate how an AI agent can reason through a real analytical investigation.

---

# Video

📺 **Claude Code + Your Data: A Practical Guide to Agentic Analytics**
https://youtu.be/tn3o8coPsC8

---

# License

This dataset is provided for educational and demonstration purposes only.
