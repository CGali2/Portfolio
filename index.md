# About Me

Data Analyst and Business Intelligence specialist focused on **dimensional data modeling, analytics engineering, and advanced DAX solutions in Power BI**. I specialize in bridging robust data architectures (backend governance, star schemas, and query optimization) with intuitive, decision-oriented dashboards.

---

## Featured Projects

### 1. Workforce & Talent Attrition Analytics
*Root-cause exploration of voluntary turnover, compensation equity, and employee risk drivers.*

* **Business Challenge:** Identify operational attrition patterns across departments, tenures, and compensation levels to proactively curb turnover costs and identify high-risk talent segments.
* **Key Architecture & Data Modeling:**
  * Designed an optimized **Star Schema** linking normalized employee dimensions (`dimEmployee`) to transactional performance review logs (`FactReviews`).
  * Implemented an interactive **Decomposition Tree** to isolate key drivers (overtime requirements, tenure brackets, and compensation tiers).
  * Enforced row-level logic and dynamic ranking calculations while preserving clean subtotals and grand totals across table visuals.
* **Core DAX Logic:**
  ```dax
  -- Safe calculation of employee turnover percentage across review cycles
  attritionRate = 
  DIVIDE (
      CALCULATE (
          COUNTROWS ( 'FactReviews' ),
          'dimEmployee'[Attrition] = "Yes"
      ),
      COUNTROWS ( 'FactReviews' ),
      0
  )
