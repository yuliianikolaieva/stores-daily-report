# Stores Daily — ENT & SMB

Private daily performance report for active UA Stores partners in Enterprise and SMB AM segments.

## Metrics

- GMV and orders
- Availability (`active minutes / working minutes`)
- Bad and failed order rates
- Day vs the same day last week
- Week-to-date vs the corresponding prior week
- Month-to-date vs the same number of days in the prior month

## Automation

The workflow refreshes the data every day at 09:00 Kyiv time. Configure these GitHub Actions secrets:

- `DATABRICKS_HOST`
- `DATABRICKS_TOKEN`
- `DATABRICKS_WAREHOUSE_ID`
- `DATABRICKS_HTTP_PATH` (optional when warehouse ID is supplied)

The report excludes Mid-market and inactive providers by design.
