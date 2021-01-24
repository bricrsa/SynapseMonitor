# Notes about what is stored in Log Analytics
*for dedicated SQL Pools in Jaunary 2021*

Not all data is transferred as-is from the Synapse DMVs to Log Analytics. There is some obfuscation applied that masks data in the DMVs. Generally speaking numbers are masked as -1 and text as #.

For example in Exec Requests

Synapse DMV | Log Analytics
------------------------ | --------------------------
select top 50 * from [dbo].[AggregateSales] | select top -1 * from [dbo].[AggregateSales]
select top 20 * from [dbo].[Trip] where DropoffGeographyID = 219423 | select top -1 * from [dbo].[Trip] where DropoffGeographyID = -1
select top 20 * from [dbo].[Trip] where PaymentType = 'CSH' | select top -1 * from [dbo].[Trip] where PaymentType = '#'
SELECT clmns.name AS [Name], 'Server[@Name=' + quotename(CAST(          serverproperty(N'Servername')         AS sysname),'''') + ']' + '/Database[@Name=' + quotename(db_name(),'''') + ']' + '/Table[@Name=' + quotename(tbl.name,'''') + ' and @Schema=' + quotename(SCHEMA_NAME(tbl.schema_id),'''') + ']' + '/Column[@Name=' + quotename(clmns.name,'''') + ']' AS [Urn], CAST(ISNULL(cik.index_column_id, 0) AS bit) AS [InPrimaryKey], CAST(ISNULL((select TOP 1 1 from sys.foreign_key_columns | SELECT clmns.name AS [Name], '#' + quotename(CAST(          serverproperty(N'#')         AS sysname),'#') + '#' + '#' + quotename(db_name(),'#') + '#' + '#' + quotename(tbl.name,'#') + '#' + quotename(SCHEMA_NAME(tbl.schema_id),'#') + '#' + '#' + quotename(clmns.name,'#') + '#' AS [Urn], CAST(ISNULL(cik.index_column_id, -1) AS bit) AS [InPrimaryKey], CAST(ISNULL((select TOP -1 -1 from sys.foreign_key_columns
select top 30 * from [dbo].[Trip] OPTION (LABEL = 'Test Query 2') | select top -1 * from [dbo].[Trip] OPTION (LABEL = 'Test Query 2')


>This masking can be quite annoying when trying to understand actual workload. It is not configurable as currently understood.
>It is possible to use labels to mark queries, however these cannot use variables.