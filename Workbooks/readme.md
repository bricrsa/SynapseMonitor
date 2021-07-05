# Workbooks 

Workbooks are in ARM template and workbook formats.

**SQL Pool Analytics**

The user can specify a time range and database name.

Contains 5 tabs
- Workload Over Time
- User Query Activity
- Query Details
- Query Summary
- User Logins

This workbook requires Audit and Basic Metrics data
 - [SQL Pool Analytics ARM Template](./SQL_Pool_Analytics.json)
 - [SQL Pool Analytics workbook template](./SQL_Pool_Analytics.workbook)
 ![Tab 1: Workload Over Time](/media/WorkloadOverTime_obs.png)
 ![Tab 2: User Query Activity](/media/UserQueryActivity_obs.png)


**Synapse Workload Understanding**

The user can specify a time range, a trend time range, database name and user name.

Contains 2 tabs
- Query Details
- User Query Activity

This workbook requires Audit data
 - [Synapse Workload Understanding ARM template](./Synapse_Workload_Understanding.json)
 - [Synapse Workload Understanding workbook template](./Synapse_Workload_Understanding.workbook)
 ![Tab 1: Workload Over Time](/media/WorkloadUn_QueryDetails_obs.png)
 ![Tab 2: User Query Activity](/media/WorkloadUn_Activity_obs.png)


**Synapse Query Cost Understanding**

Note that this is experimental and should be used for guidance purposes only.

More detailed explanations [here](/Queries/readme_cost.md)