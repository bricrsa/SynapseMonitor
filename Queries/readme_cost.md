## General approach

In the version of SQL Dedicated pools current in June 2021, costs for a SQL Pool are per hour. This is well understood and can be modified with a reservation, for significant savings.

Many users would like to understand the specific cost of a query for cross charging and optimisation purposes. 

Various factors affect a query's cost
- Scale of dedicated pool (DWU)
- duration of query
- resource allocation for the executing user

The possibility of extended durations due to factors such as queuing for resource, locking or other scenarios is not considered.

The calculation can be described as follows:

    > (Duration of query) x (cost of pool per second) x (percentage of pool allocated)


- based on Audit
    - [query cost - audit](./audit_query_cost_estimate.txt)
    - [query cost summary - audit](./audit_query_cost_estimate_summary.txt)


- based on Exec requests
    - [query cost - exec requests](./exec_requests_query_cost_estimate.txt)

*Technical note:*

Costs are based on North Europe. Replace these with your target region.

Resource groups: include the mapping for your workload management groups in the resource mapping section.

---
**NOTE:** This methodology is for guidance only, to highlight a method for apportioning cost. 
Unless the environment is 100% utilised in the billing hour, these calculations will not cover the full hour cost. 
A more generalised apportionment based on percentage of total workload may be more appropriate for general cross-charging.

---