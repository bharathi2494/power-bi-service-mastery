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

## Dev / Test / Prod workspace strategy
The Dev / Test / Prod workspace strategy is a best practice in Power BI Service used to separate development, validation, and production environments.  
This approach ensures stable deployments, better governance, controlled access, and minimal risk when releasing reports to business users.

## Why Dev / Test / Prod Strategy is Important
- Prevents unfinished or incorrect reports from reaching users
- Enables proper testing and business validation
- Supports CI/CD and controlled releases
- Improves security and governance
- Aligns with enterprise BI and SDLC standards

## Development Workspace (Dev)
**Purpose:**
- Build reports and dashboards
- Develop data models and DAX
- Perform initial data validation
- Experiment with visuals and calculations
**Key Characteristics**
- Frequent changes
- Developers have full access
- Uses development or sample data sources
- Manual or limited refresh
**Access:**
- Admin / Member: Power BI Developers
- Viewer: Not recommended

## Testing Workspace (Test / UAT)
- Validate data accuracy
- Test business logic and KPIs
- Verify Row-Level Security (RLS)
- Perform performance and refresh testing
**Key Characteristics**
- Limited and controlled changes
- Near-production data
- Business users involved for UAT
**Access:**
- Admin / Member: Developers
- Viewer: Testers, Business stakeholders
  
## Production Workspace (Prod)
- Deliver final, trusted reports to end users
- Support business decision-making
**Key Characteristics**
- Highly stable
- Scheduled refresh enabled
- Certified or promoted datasets
- Reports shared via Power BI Apps
**Access**
- Admin: BI Team
- Viewer: Business users (via App only)

## Deployment Flow
```python
Power BI Desktop
   ↓
Dev Workspace
   ↓
Test Workspace
   ↓
Prod Workspace
```
## Deployment Pipelines (Recommended)

**Available with:**
- Power BI Premium
- Microsoft Fabric capacity

**Benefits**
- Automated promotion from Dev → Test → Prod
- Parameter and data source switching
- Reduced manual deployment errors
- Supports enterprise CI/CD practices
