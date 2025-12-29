# DAY 1 – Tenant, Workspaces & Governance (Power BI Service)
## Power BI Service Architecture (Enterprise View)
Power BI Service is a cloud-based SaaS layer hosted in Azure that manages:
- Report hosting
- Dataset refresh & security
- Collaboration & sharing
- Governance & auditing

**High-level Flow**
```pyton
Data Sources → Power BI Desktop → Power BI Service
                    |
            Datasets / Reports
                    |
         Workspaces → Apps → End Users
```
