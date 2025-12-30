# Power BI Service Mastery
This repository demonstrates enterprise-level Power BI Service implementation, focusing on governance, security, deployment, performance, and administration.  

## Key Topics Covered
- Power BI Service architecture
- Workspace strategy (Dev / Test / Prod)
- Dataset management & refresh
- On-Premises Data Gateway
- Row-Level Security (RLS) & Object-Level Security (OLS)
- Power BI Apps & content distribution
- Deployment Pipelines (CI/CD)
- Performance & capacity management
- Admin portal & tenant governance
- Power BI + Microsoft Fabric overview

## Workspace Architecture
- Development → Test → Production

**Each workspace follows:**
- Controlled access
- Certified datasets
- App-based distribution
- Governance via tenant settings

## Security Implementation
- Dynamic RLS using USERPRINCIPALNAME()
- Dataset-level security enforcement
- App-based read-only access
- Object-level security for sensitive columns

## Data Refresh & Gateway
- Scheduled refresh (Import mode)
- Incremental refresh for large datasets
- Standard On-Premises Data Gateway
- Credential & privacy level management

## Deployment Pipelines
- Seamless promotion across environments
- Parameter rules for data sources
- Reduced manual deployment errors
- Enterprise CI/CD best practices

## Performance & Monitoring
- VertiPaq optimization
- Capacity Metrics App
- XMLA endpoint usage
- Refresh & query performance analysis

# Governance & Administration
- Power BI Admin Portal
- Tenant-level settings control
- Sensitivity labels & lineage view
- Impact analysis for changes

## Tools & Technologies
- Power BI Desktop
- Power BI Service
- DAX
- Power Query
- Azure SQL / SQL Server
- Microsoft Fabric (conceptual)


