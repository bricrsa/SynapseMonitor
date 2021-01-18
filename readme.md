# Monitoring Synapse SQL Pools with Log Analytics

Synapse has powerful, simple to implement integration with Log Analytics

**Contents**
- Why is this useful
- What can be logged
- How do we display this information
    - Workbooks (portal)
    - Logs viewer (portal) - [list of queries](./Queries/readme.md)
    - PowerBI

## Why is this useful

Data Management Views (DMVs) in Synapse are very useful in understanding workload, however it many of the underlying datasets only retain the most recent 10k rows, which in busy systems means that current data will expire within hours or days. Log Analytics allows long term retention of this data and trend analysis

## What can be logged

There are two kinds of logs: audit and diagnostic logs.

Audit logs include simplified views of workload on the platform and includes user names, source IPs and executed commands. Typically this will manifest as a single row per query.

Diagnostic logs include details of all the DMVs as well as metrics about the database. These closely mimic the DMVs.

- logs
    - DmsWorkers
    - ExecRequests
    - RequestSteps
    - SqlRequests
    - Waits
 - metric
    - Basic
    - InstanceAndAppAdvanced
    - WorkloadManagement

## How do we display this information

Users can use various methods to consume this information
- Workbooks (portal)
- Logs viewer (portal) - [list of queries](./readme.md)
- PowerBI