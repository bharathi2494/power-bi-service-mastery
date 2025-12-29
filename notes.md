# DAY 1 – Tenant, Workspaces & Governance (Power BI Service)
## Power BI Service Architecture (Enterprise View)
Power BI Service is a cloud-based SaaS layer hosted in Azure that manages:
- Report hosting
- Dataset refresh & security
- Collaboration & sharing
- Governance & auditing

**High-level Flow**
```python
Data Sources → Power BI Desktop → Power BI Service
                    |
            Datasets / Reports
                    |
         Workspaces → Apps → End Users
```
## Tenant vs Capacity vs Workspace
## Tenant
- Organization-wide boundary
- Controlled by Power BI Admin Portal
- Defines:
    - Who can publish
    - Who can create workspaces
    - Sharing, export, embed rules
      
👉 One tenant per organization

 ## Capacity
 Compute & memory resources  
 **Types:**  
 - Shared Capacity (Free / Pro)
 - Dedicated Capacity (Premium P / Fabric F)

| Feature              | Shared | Dedicated  |
| -------------------- | ------ | ---------- |
| Performance          | Shared | Guaranteed |
| Large models         | ❌     | ✅          |
| XMLA Write           | ❌     | ✅          |
| Deployment pipelines | ❌     | ✅          |  

👉 Production workloads should always run on Dedicated Capacity

## Workspace
- Collaboration boundary
- Holds:
    - Datasets
    - Reports
    - Dashboards
- Security managed via roles

👉 Workspaces map to business domains (Sales, Finance, HR)

## Workspace Roles & Best Practices
| Role        | Permissions     | Best Practice  |
| ----------- | --------------- | -------------- |
| Admin       | Full control    | 1–2 users only |
| Member      | Build & publish | Developers     |
| Contributor | Publish content | Analysts       |
| Viewer      | Read-only       | Business users |


