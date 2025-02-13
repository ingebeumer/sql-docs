---
description: "SQLStatistics (Access Driver)"
title: "SQLStatistics (Access Driver) | Microsoft Docs"
ms.custom: ""
ms.date: "01/19/2017"
ms.service: sql
ms.reviewer: ""
ms.subservice: connectivity
ms.topic: conceptual
helpviewer_keywords: 
  - "Access driver [ODBC], SQLStatistics"
  - "SQLStatistics function [ODBC], Access Driver"
ms.assetid: 6117ac77-1020-4f0c-8eed-e671c34c1f21
author: David-Engel
ms.author: v-davidengel
---
# SQLStatistics (Access Driver)
> [!NOTE]  
>  This topic provides Access Driver-specific information. For general information about this function, see the appropriate topic under [ODBC API Reference](../../odbc/reference/syntax/odbc-api-reference.md).  
  
|Column|Comments|  
|------------|--------------|  
|TABLE_QUALIFIER|The path to a database file is returned for Microsoft Access.<br /><br /> Pattern matching is not supported in the *szTableQualifier* argument.|  
|TABLE_OWNER|NULL is returned in this column, because owner name is not supported.|  
|TABLE_NAME|Undelimited table name.<br /><br /> Pattern matching is not supported in the *szTableName* argument.|  
|INDEX_QUALIFIER|NULL is always returned.|  
|INDEX_NAME|Index-dependent.|  
|TYPE|Only SQL_TABLE_STAT or SQL_INDEX_OTHER will be returned for TYPE.|  
|SEQ_IN_INDEX|Index-dependent.|  
|COLUMN_NAME|Index-dependent.|  
|COLLATION|Index-dependent.|  
|CARDINALITY|Returned for Microsoft Access only.|  
|PAGES|NULL is always returned.|  
  
 Filtering is based on uniqueness (the *fUnique* argument). The *fAccuracy* parameter is ignored.
