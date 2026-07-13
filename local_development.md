# Local Development Setup

Use the following steps to set up a local development environment.

## Run on Databricks

1. Go to the Databricks connection.
2. Click **Select a Cluster**, then select your cluster.
3. Click **Run on Databricks** to fire up the run.

> This runs the file as a job run, but not very useful for quick debugging.

## Databricks Connect Setup

1. Create a virtual environment:
   ```bash
   python -m venv .venv_dbc
   ```

2. Activate the virtual environment:
   ```powershell
   .venv_dbc\Scripts\Activate.ps1
   ```

3. Install `databricks-connect`:
   ```
   pip install databricks-connect
   ```
   - **Classic clusters:** must match the Databricks Runtime version (e.g., `databricks-connect==14.3.*` for DBR 14.3)
   - **Serverless:** Databricks manages the runtime — just install `databricks-connect>=13.3` (latest works fine)

4. Register the kernel for Jupyter:
   ```bash
   pip install ipykernel
   python -m ipykernel install --user --name=.venv_dbc --display-name "Python (.venv_dbc)"
   ```

5. Add this cell to the top of your notebook to initialize the Spark session:
   ```python
   from databricks.connect import DatabricksSession
   spark = (
       DatabricksSession.builder
       .profile("apd_mwang")
       .serverless(True)
       .getOrCreate()
   )
   ```

6. Make sure that databricks connect is set up correctly. 

7. df.show(truncate=False) use this command to make sure that column is not truncated