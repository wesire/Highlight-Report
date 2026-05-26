# Highlight Report — Programme Highlight Report Replacement

Replacement for a macro-enabled Excel highlight report workbook with a robust
Microsoft 365 solution:

- **SharePoint Lists** — database
- **Power Apps** — user input layer
- **Power BI** — reporting / dashboard layer
- **Power Automate** — workflow, reminders, period locking, snapshots
- **Excel** — optional export only (never the live database)

Designed for a UK local authority / public sector programme reporting process.
UK date formatting (dd/MM/yyyy), £ GBP, en-GB locale (LCID 2057).

## Hierarchy

```
Scheme  (Capital / Revenue / Mixed)
  └── Project
        └── Programme
              └── Programme Update  (one per Reporting Period)
```

Updates, Risks, Issues, Milestones and Change Requests are stored against a
**Reporting Period**, so monthly history is preserved and never overwritten.

## Repository structure

```
/docs
  DATA_MODEL.md
  POWER_APP_SPEC.md
  POWER_BI_SPEC.md
  POWER_AUTOMATE_SPEC.md
  MIGRATION_PLAN.md
  MVP_DELIVERY_PLAN.md
  TEST_PLAN.md
/scripts
  provision-sharepoint-lists.ps1
  seed-reference-data.ps1
  import-sample-data.ps1
/powerbi
  power-query-m-scripts.md
  dax-measures.md
/powerapps
  power-fx-snippets.md
  app-screen-specification.md
/sample-data
  *.csv
```

## Build phases

| Phase | Output | Status |
|---|---|---|
| 1 | SharePoint provisioning script | ✅ |
| 2 | Data model docs | ✅ |
| 3 | Power Apps spec | ✅ |
| 4 | Power Fx snippets | pending |
| 5 | Power BI model + DAX + M | pending |
| 6 | Power Automate flows | pending |
| 7 | Migration plan | pending |
| 8 | MVP delivery plan | pending |
| 9 | Test plan | pending |
| 10 | Sample data & final scaffolding | pending |

## Quick start

```powershell
Install-Module PnP.PowerShell -Scope CurrentUser

New-PnPSite -Type CommunicationSite `
            -Title "Programme Highlight Report" `
            -Url   "https://<tenant>.sharepoint.com/sites/ProgrammeHighlightReport" `
            -Lcid  2057

./scripts/provision-sharepoint-lists.ps1 `
   -SiteUrl "https://<tenant>.sharepoint.com/sites/ProgrammeHighlightReport"
```
