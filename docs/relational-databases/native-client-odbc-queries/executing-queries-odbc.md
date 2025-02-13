---
title: "Executing Queries (ODBC) | Microsoft Docs"
description: An ODBC application can run statements on an SQL Server instance by initializing a connection handle and connecting to a data source.
ms.custom: ""
ms.date: "03/14/2017"
ms.service: sql
ms.reviewer: ""
ms.subservice: native-client
ms.topic: "reference"
helpviewer_keywords: 
  - "ODBC applications, executing queries"
  - "SQL Server Native Client ODBC driver, statements"
  - "ODBC applications, statements"
  - "SQL Server Native Client ODBC driver, queries"
  - "queries [ODBC]"
ms.assetid: d935bcba-8ce6-4159-8395-6c86431602ad
author: markingmyname
ms.author: maghan
monikerRange: ">=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||>=sql-server-linux-2017||=azuresqldb-mi-current"
---
# Executing Queries (ODBC)
[!INCLUDE[SQL Server Azure SQL Database Synapse Analytics PDW ](../../includes/applies-to-version/sql-asdb-asdbmi-asa-pdw.md)]

  After an ODBC application initializes a connection handle and connects with a data source, it allocates one or more statement handles on the connection handle. The application can then execute [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] statements on the statement handle. The general sequence of events in executing an SQL statement is:  
  
1.  Set any required statement attributes.  
  
2.  Construct the statement.  
  
3.  Execute the statement.  
  
4.  Retrieve any result sets.  
  
 After an application retrieves all the rows in all of the result sets returned by the SQL statement, it can execute another query on the same statement handle. If an application determines that it is not required to retrieve all the rows in a particular result set, it can cancel the rest of the result set by calling either [SQLMoreResults](../../relational-databases/native-client-odbc-api/sqlmoreresults.md) or [SQLCloseCursor](../../relational-databases/native-client-odbc-api/sqlclosecursor.md).  
  
 If, in an ODBC application, you must execute the same SQL statement multiple times with different data, use a parameter marker denoted by a question mark (?) in the construction of an SQL statement:  
  
```  
INSERT INTO MyTable VALUES (?, ?, ?)  
```  
  
 Each parameter marker can then be bound to a program variable by calling [SQLBindParameter](../../relational-databases/native-client-odbc-api/sqlbindparameter.md).  
  
 After all SQL statements execute and their result sets process, the application frees the statement handle.  
  
 The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client ODBC driver supports multiple statement handles per connection handle. Transactions are managed at the connection level, so that all work performed on all statement handles on a single connection handle are managed as part of the same transaction.  
  
## In This Section  
  
-   [Allocating a Statement Handle](../../relational-databases/native-client-odbc-queries/allocating-a-statement-handle.md)  
  
-   [Constructing an SQL Statement &#40;ODBC&#41;](../../relational-databases/native-client-odbc-queries/constructing-an-sql-statement-odbc.md)  
  
-   [Constructing SQL Statements for Cursors](../../relational-databases/native-client-odbc-queries/constructing-sql-statements-for-cursors.md)  
  
-   [Using Statement Parameters](../../relational-databases/native-client-odbc-queries/using-statement-parameters.md)  
  
-   [Executing Statements &#40;ODBC&#41;](../../relational-databases/native-client-odbc-queries/executing-statements/executing-statements-odbc.md)  
  
-   [Freeing a Statement Handle](../../relational-databases/native-client-odbc-queries/freeing-a-statement-handle.md)  
  
## See Also  
 [SQL Server Native Client &#40;ODBC&#41;](../../relational-databases/native-client/odbc/sql-server-native-client-odbc.md)  
  
  
