## Databricks CLI Checks for `apd_mwang` Profile

Use the following commands to confirm that the `apd_mwang` Databricks CLI profile is configured correctly.
Get authorization:

```powershell id="5swyrv"
databricks auth login --host https://aimpt-prod.cloud.databricks.com/ --profile apd_mwang_prod
```

List available clusters:

```powershell id="5swyrv"
databricks clusters list --profile apd_mwang
```

List available SQL warehouses:

```powershell id="q9ejz3"
databricks warehouses list --profile apd_mwang
```

Confirm the currently authenticated Databricks user:

```powershell id="h8v2jo"
databricks bundle validate --output json
```
```powershell id="h8v2jo"
databricks bundle validate --output json --target prod --profile apd_mwang
```

Bundle Validation & Deployment:
```powershell id="h8v2jo"
databricks bundle validate --profile apd_mwang
```
```powershell id="h8v2jo"
databricks bundle deploy -t dev -p apd_mwang
```