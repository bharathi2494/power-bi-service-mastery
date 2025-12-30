# DAY 2 – Datasets, Refresh & Gateways (Power BI Service)
Understand how data enters Power BI Service, how it stays updated, and how secure connections work between Power BI and on-premises data sources.

## Datasets in Power BI Service
**What is a Dataset?** 
A dataset is the semantic layer in Power BI that contains:  
- Data model (tables & relationships)
- Power Query transformations
- DAX measures
- Refresh logic
In Power BI Service, reports are built on top of datasets.

## 2.Import vs DirectQuery vs Composite Models
## 🔹 Import Mode
- How it works
- Data is copied into Power BI.
- Stored in VertiPaq (in-memory) engine.
**Pros**
✅ Very fast performance
✅ Full DAX & modeling features
✅ Works offline after refresh
**Cons**
❌ Data is not real-time
❌ Requires scheduled refresh

**Best Use Cases:**  
- Sales reports
- Financial dashboards
- Daily or hourly refresh data

## 🔹 DirectQuery Mode
- How it works
- Power BI sends queries directly to the source.
- No data stored in Power BI.
**Pros**
✅ Near real-time data
✅ No dataset size limits
**Cons**
❌ Slower performance
❌ Limited DAX & transformations
❌ Heavy load on source system

**Best Use Cases**  
- Real-time dashboards
- Large enterprise databases
- Operational monitoring

## 🔹 Composite Model
**How it works**  
Mix of Import + DirectQuery tables in one model.
**Pros**  
✅ Best of both worlds
✅ High performance for historical data
✅ Live data for critical tables
**Cons**  
❌ More complex architecture

**Best Use Cases**  
- Large enterprise models
- Historical + real-time reporting

## 3. Dataset Ownership
**What is Dataset Owner?**  
The user who publishes the dataset becomes the owner.  
Refresh and credentials run under this identity.
**Why Ownership Matters**  
If owner leaves organization → refresh fails
Permissions & credentials depend on owner

**Best Practices**  
✔ Use service accounts for production
✔ Transfer ownership before employee exits
✔ Centralized dataset management

## 4. Scheduled Refresh
What is Scheduled Refresh?  
Automatic update of dataset data at fixed intervals.

**License	Refresh Limit**
Pro	- 8 times/day
Premium	- 48 times/day

**Refresh Steps**
- Go to Power BI Service
- Open Dataset → Settings
Configure:
- Data source credentials
- Privacy levels
- Refresh schedule

**Common Refresh Failures** 
❌ Credential expired
❌ Gateway offline
❌ Source system unavailable
❌ Schema changes

## 5. Credentials & Privacy Levels
**Credentials**  
Power BI must authenticate with the data source.

**Examples:**  
- SQL Authentication
- Windows Authentication
- OAuth (SharePoint, Azure)

**Privacy Levels**  
Used to prevent data leakage.

## 6. On-Premises Data Gateway
**What is a Gateway?**  
A secure bridge between:  
- Power BI Service (cloud)
- On-premises data sources (SQL Server, Oracle, File Server)
Power BI never directly connects to your local network.

## 🔹 Gateway Types
## 1️⃣ Standard (Enterprise) Gateway
**Features:**
- Multiple users
- Multiple datasets
- Centralized management
- Supports clustering

**Recommended for**
✔ Dev / Test / Prod environments
✔ Enterprise deployments

## 2️⃣ Personal Gateway
**Features**
- Single user only
- No sharing
- Limited management

**Recommended for:**
❌ Learning only
❌ Personal experiments

❗ Never use Personal Gateway in Production

## 8. Gateway Clustering (Theory)
**What is Gateway Cluster?**  
Multiple gateway machines grouped together for:
- High availability
- Load balancing
- Failover

**Why Clusters Matter**
- If one gateway fails → others continue
- No refresh downtime
- Enterprise-grade reliability

**Best Practice**  
✔ Minimum 2 gateways per cluster
✔ Install on different servers

## 9. Incremental Refresh Architecture
**What is Incremental Refresh?**  
Refresh only new or changed data, not full dataset.

**How it Works**  
- Define date parameters in Power Query
- Partition data by date
- Refresh:
    - Recent data frequently
    - Historical data rarely

**Benefits**  
✅ Faster refresh
✅ Lower gateway load
✅ Supports large datasets

**Best Use Cases**  
- Fact tables (sales, transactions)
- Large historical data
