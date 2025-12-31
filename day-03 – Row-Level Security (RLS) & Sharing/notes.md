# DAY 3 – Row-Level Security (RLS) & Sharing
## What is Row-Level Security (RLS)?
RLS controls which rows of data a user can see in a Power BI report.
- Same report
- Same dataset
- Different users see different data
**Example:**
- Manager sees all regions
- Salesperson sees only their region

## 1️⃣ Static RLS (Beginner)

## 🔹 What is Static RLS?
- Rules are hard-coded
- Each role is manually mapped to specific values
**🔹 Example:**
**Sales table:**
| SalesPerson | Region | Sales |
|------------|--------|-------|
| Ravi       | South  | 10000 |
| Anita      | North  | 12000 |

**Create role:**  
```python
[Region] = "South"
```
**🔹 Who sees what?**
Users in this role → only South data

**✅ Pros**  
- ✔ Easy to understand
- ✔ Good for demos & small teams

**❌ Cons**
- ❌ Not scalable
- ❌ Need multiple roles for many users

**Use when:** Few users, fixed rules

## 2️⃣ Dynamic RLS using USERPRINCIPALNAME()
## 🔹 What is Dynamic RLS?
- Security rules are data-driven
- Uses logged-in user’s email
- One role can handle hundreds of users

**🔹 Key Function: USERPRINCIPALNAME()** 
➡ Returns logged-in user email

## 🔹 Required Tables
**1️⃣ Sales Table**  
| Sales | Region |
|-------|--------|
| 10000 |	South  |

**2️⃣ Security Table**
|     Email       | Region |
|-----------------|-------|
|ravi@company.com | South |
|anita@company.com | North |

**➡ Relationship:**  
```python
Security[Region] → Sales[Region]
```
**🔹 Role Filter (DAX)**
```python
Security[Email] = USERPRINCIPALNAME()
```
## 🔹 How it works
- Power BI checks logged-in email
- Filters Security table
- Automatically filters Sales table

## ✅ Pros
- ✔ Scalable
- ✔ Enterprise-ready
- ✔ Best practice

## ❌ Cons
- ❌ Needs correct relationships
- ❌ Email IDs must match exactly

**Use when:** Real projects, production environments

## 3️⃣ Object-Level Security (OLS) 
## 🔹 What is OLS?
- Controls which tables or columns users can access
- Unlike RLS → not row based
**Examples:**
  - Hide Salary column
  - Hide Cost table
  - Show only Aggregated data
