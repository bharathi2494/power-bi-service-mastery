# DAY 5 – Deployment Pipelines (CI/CD)
## 1️⃣ What is a Deployment Pipeline? (Foundation)
A Deployment Pipeline in Power BI is a controlled way to move content across environments without re-publishing PBIX files manually.  
It supports CI/CD (Continuous Integration / Continuous Deployment).  
### Typical Lifecycle
Build once → Deploy many times

## 2️⃣ Deployment Pipeline Stages (PL-300 CORE ⭐⭐⭐)

Power BI Deployment Pipelines have 3 fixed stages:

| Stage |	Purpose|
|---------|--------|
| Development	|Build & modify reports|
|Test	 |Validate & UAT|
|Production |	Business consumption|

⚠️ You cannot add or rename stages.

## 🔹 Development Stage
### Developers:
- Create datasets
- Build reports
- Make frequent changes
- Connected to: Dev data sources
- Refreshes:Frequent

## 🔹 Test Stage
- Used by: QA team, Business testers
- Purpose:
    - Validate numbers
    - Performance testing
    - RLS validation
- Uses: Test data sources

## 🔹 Production Stage
- Used by: End users
- Content: Read-only
- Highly governed
- Uses: Production data sources

> “Deployment pipelines separate development, validation, and consumption to ensure stable production reporting.”

## 3️⃣ How Deployment Pipelines Work (Conceptual Flow)
1. Create a Deployment Pipeline
2. Assign workspaces to each stage
3. Build content in Dev workspace
4. Deploy:
   - Dev → Test
   - Test → Prod
5. Apply:
    - Parameter rules
    - Data source bindings
6. Validate & monitor

## 4️⃣ Parameter Rules
### 🔹 What are Parameter Rules?
Parameter rules allow you to:  
- Change parameter values automatically
- When deploying between stages
Without editing PBIX.

### 🔹 Common Parameters
- Server name
- Database name
- File path
- Environment flag (Dev/Test/Prod)

### 🔹 Example
- Stage	Server
- Dev	DEV-SQL
- Test	TEST-SQL
- Prod	PROD-SQL

**Parameter rule:**  
- If deploying to Test → use TEST-SQL
- If deploying to Prod → use PROD-SQL

> Parameter rules work only if parameters exist in the dataset.

## 5️⃣ Data Source Binding (VERY IMPORTANT ⭐⭐⭐)
### 🔹 What is Data Source Binding?
Data source binding allows you to:  
- Map datasets to different data sources
- Per pipeline stage

## 🔹 When is Binding Used?
When:  
- Dev/Test/Prod have different servers
- Same schema, different environments

### 🔹 Example
|Stage	| SQL Server |
|------|--------|
|Dev	|dev-db.company.com|
|Test	|test-db.company.com|
|Prod	|prod-db.company.com|

**Binding maps:**
- Dataset → Correct server
Without editing PBIX

## 🔹 Parameter Rules vs Data Source Binding
| Feature            | Parameter Rules | Data Source Binding |
| ------------------ | --------------- | ------------------- |
| Requires parameter | Yes             | No                  |
| Used for           | Any value       | Data sources only   |
| Flexibility        | High            | Medium              |
| Exam focus         | HIGH            | HIGH                |


###  Best Practice:
- Use data source binding for databases
- Use parameter rules for logic/configuration

## 6️⃣ What Gets Deployed?
- ✔ Datasets
- ✔ Reports
- ✔ Dashboards
- ✔ Dataflows

### ⚠️ NOT deployed:
- ❌ Workspace users
- ❌ App permissions
- ❌ Gateway settings

## 7️⃣ Limitations of Deployment Pipelines (PL-300 ⚠️)
### 🔹 Technical Limitations
Only works with:  
   - Premium capacity
   - PPU (Premium Per User)
Does not support:
   - My Workspace
   - Personal workspaces

> “Production workspaces should be deployment targets, not development environments.”

## 9️⃣ Deployment Pipelines vs Manual Publish 
| Feature            | Manual Publish | Deployment Pipeline |
| ------------------ | -------------- | ------------------- |
| Error risk         | High           | Low                 |
| Reusability        | Low            | High                |
| Parameter handling | Manual         | Automated           |
| Enterprise ready   | ❌              | ✅                   |


## 🔟 End-to-End Enterprise Scenario (EXAM STYLE)
1. Developer builds report in Sales-Dev
2. Uses Dev SQL database
3. Deploys to Sales-Test
4. Parameter rule switches to Test DB
5. Business validates numbers
6. Deploys to Sales-Prod
7. Data source binding points to Prod DB
8. App published for users

# Common Interview Questions & Answers
### Q1. What license is required for deployment pipelines?
Answer: Power BI Premium or Premium Per User (PPU).

### Q2. Can I deploy only a single report?
Answer: No, deployment happens at workspace level.

### Q3. Can pipelines replace Git?
Answer: No. Pipelines manage Power BI artifacts, not source control.

### Q4. What is the difference between parameter rules and binding?
Answer: Parameter rules update parameters; binding maps datasets to data sources.

### One-Line Summary (Perfect Notes Line)
> ***Deployment pipelines enable automated, governed promotion of Power BI content across Dev, Test, and Production environments using parameter rules and data source binding.***
