# Copilot Instructions for AI Coding Agents# Copilot Instructions for AI Coding Agents



Welcome to the Fundamentals of Data Transformation codebase! This guide is for AI coding agents to quickly become productive and follow project-specific conventions.Welcome to the `Fundamentals of Data Transformation` codebase! This guide is for AI coding agents to maximize productivity and maintain project conventions.



## Project Overview## Big Picture Architecture

- This repo supports a LinkedIn Learning course focused on hands-on data transformation using SQL (DuckDB) and Python (Pandas).- The project is a hands-on data transformation course using Jupyter Notebooks, SQL (DuckDB), and Python (Pandas).

- All course content is organized in Jupyter Notebooks under `course/`, split into `exercises` (video code) and `lessons` (editable for practice).- All course content is organized under `course/` by topic: `01-intro`, `02-sql`, `03-pandas`, `04-appendix`.

- The main dataset is US National Parks Service data, loaded from Parquet files in `course/data/nps/`.- Each topic contains `exercises/` (video code) and `lessons/` (editable for practice).

- Data is stored in `course/data/`, primarily as Parquet files and SQL scripts.

## Architecture & Data Flow

- Notebooks are the primary unit of work. Each section (`01-intro`, `02-sql`, `03-pandas`, `04-appendix`) contains both exercises and lessons.## Developer Workflows

- SQL workflows use DuckDB via JupySQL (`%load_ext sql`, `%%sql` cells). The DuckDB database is initialized and loaded from Parquet files at notebook startup.- **Primary workflow:** Edit and run Jupyter Notebooks in VS Code or GitHub Codespaces. No local setup required.

- Pandas workflows load data directly from Parquet files using `pd.read_parquet()`.- **SQL workflow:** Use DuckDB via JupySQL extension. Always initialize with:

- No standalone application or web service; all logic is in notebooks and supporting scripts.  ```python

  import duckdb

## Developer Workflows  %load_ext sql

- **Run code:** Use Jupyter Notebook cells in VS Code or GitHub Codespaces. No manual setup required in Codespaces.  conn = duckdb.connect()

- **SQL in notebooks:** Always initialize DuckDB with:  %sql conn --alias duckdb

  ```python  %sql IMPORT DATABASE '../../data/nps';

  import duckdb  ```

  %load_ext sql- **Pandas workflow:** Load dataframes from Parquet files:

  conn = duckdb.connect()  ```python

  %sql conn --alias duckdb  df = pd.read_parquet('../../data/nps/nps_public_data_[TABLE].parquet')

  %sql IMPORT DATABASE '../../data/nps';  ```

  ```- **Testing:** No automated tests; validation is manual via notebook cell execution.

  Use `%%sql` for multi-line queries, `%sql` for single-line.- **Builds:** No build process; notebooks are run interactively.

- **Pandas in notebooks:** Load tables with:

  ```python## Project-Specific Conventions

  df = pd.read_parquet('../../data/nps/nps_public_data_[TABLE].parquet')- SQL queries in notebooks use `%%sql` for multi-line and `%sql` for single-line.

  ```- SQL and Python code should be readable and well-formatted; follow examples in `lessons/`.

- **Testing:** No automated test suite; validation is manual via notebook cell output.- Data paths are always relative to the notebook location (e.g., `../../data/nps/`).

- **Builds:** No build process; notebooks are run interactively.- Notebooks are the source of truth for exercises and lessons; do not add scripts outside this structure.

- **Dependencies:** Managed via `requirements.txt` and `pyproject.toml`. Use Codespaces or a local Python virtual environment.- No support for local development issues—focus on Codespaces or VS Code remote environments.



## Conventions & Patterns## Integration Points & Dependencies

- SQL queries are formatted for readability (indented, clear aliases, CTEs encouraged).- **DuckDB**: Used for all SQL queries; loaded in notebooks via JupySQL.

- Notebooks start with environment setup cells (see above for DuckDB/Pandas).- **Pandas**: Used for data manipulation in Python lessons.

- Data paths are always relative to the notebook location (e.g., `../../data/nps/`).- **JupySQL**: Required for SQL magic commands in notebooks.

- All code and data for exercises is included in the repo; no external API calls required.- **Dataset**: US National Parks Service data, preloaded as Parquet and SQL files in `course/data/nps/`.

- Prefer hands-on, exploratory coding— encourage new cells for experimentation.

## Key Files & Directories

## Key Files & Directories- `course/02-sql/lessons/01-duckdb-basics.ipynb`: Example of DuckDB setup and SQL queries.

- `course/01-intro/`, `course/02-sql/`, `course/03-pandas/`, `course/04-appendix/`: Main course content.- `course/03-pandas/lessons/01-dataframe-basics.ipynb`: Example of Pandas data loading and manipulation.

- `course/data/nps/`: Parquet files for National Parks dataset.- `course/data/nps/`: Contains all datasets used in the course.

- `requirements.txt`, `pyproject.toml`: Python dependencies.- `requirements.txt`/`pyproject.toml`: List required Python packages (for local setup only).

- `.github/copilot-instructions.md`: This file.

- `README.md`: Course overview and setup instructions.## Example Patterns

- To run a SQL query:

## Integration Points  ```python

- No external services or APIs required for exercises; all data is local.  %%sql

- DuckDB and Pandas are the only major dependencies; ensure they are installed and imported as shown above.  SELECT * FROM nps_public_data.parks LIMIT 1

  ```

---- To load a Parquet file with Pandas:

  ```python

If any conventions or workflows are unclear, please ask for clarification or request examples from the codebase. Update this file as new patterns or requirements emerge.  import pandas as pd
  df = pd.read_parquet('../../data/nps/nps_public_data_parks.parquet')
  ```

---

If any conventions or workflows are unclear, please ask for clarification or request examples from specific files or directories.
