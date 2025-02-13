---
title: "Using the sql:identity and sql:guid Annotations"
description: "Learn how to use the sql:identity and sql:guid annotations in an XSD schema to define the behavior of an XML updategram."
author: MikeRayMSFT
ms.author: mikeray
ms.date: "03/16/2017"
ms.service: sql
ms.subservice: xml
ms.topic: "reference"
ms.assetid: 7661dfd0-6573-4692-a8f1-3597adcd33c4
monikerRange: "=azuresqldb-current||>=sql-server-2016||>=sql-server-linux-2017||=azuresqldb-mi-current"
---
# Using the sql:identity and sql:guid Annotations
[!INCLUDE [SQL Server Azure SQL Database](../../includes/applies-to-version/sql-asdb.md)]
  You can specify the **sql:identity** and **sql:guid** annotations in an XSD schema on any node that maps to a database column in [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Whereas the updategram format supports the **updg:at-identity** and **updg:guid** attributes, the DiffGram format does not. The **updg:at-identity** attribute defines the behavior in updating an IDENTITY-type column. The **updg:guid** attribute allows you to obtain a GUID value from [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] and use it in the updategram. For more information and working samples, see [Inserting Data Using XML Updategrams &#40;SQLXML 4.0&#41;](../../relational-databases/sqlxml-annotated-xsd-schemas-xpath-queries/updategrams/inserting-data-using-xml-updategrams-sqlxml-4-0.md).  
  
 The **sql:identity** and **sql:guid** annotations extend this functionality to DiffGrams.  
  
 When you execute a DiffGram, it is first converted to an updategram, and then the updategram is executed. By specifying the **sql:identity** and **sql:guid** annotations in the XSD schema, you are in fact defining the behavior of an updategram. Therefore, all the annotations are described in the context of an updategram. The annotations can be used both for DiffGrams and updategrams; however, updategrams already provide a more powerful way of handling identity and GUID values.  
  
 The **sql:identity** and **sql:guid** annotations can be defined on a complex content element.  
  
## sql:identity Annotation  
 You can specify the **sql:identity** annotation in the XSD schema on any node that maps to an IDENTITY-type database column. The value specified for this annotation defines how the IDENTITY-type column is updated (either by using the value provided in the updategram to modify the column or by ignoring the value, in which case a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-generated value is used for this column).  
  
 The **sql:identity** annotation can be assigned two values:  
  
 ignore  
 Directs the updategram to ignore any value that is provided in the updategram for that column and to rely on [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] to generate the identity value.  
  
 useValue  
 Directs the updategram to use the value that is provided in the updategram to update the IDENTITY-type column. An updategram does not check whether the column is an identity value or not.  
  
 If the updategram specifies a value for the IDENTITY-type column, the **sql:identity="useValue"** must be specified in the schema.  
  
## sql:guid Annotation  
 An updategram can have [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] generate a GUID value and then use this value in the updategram. In the context of DiffGrams, you can use the **sql:guid** annotation to specify whether to use a GUID value that is generated by SQL Server or use the value that is provided in the updategram for that column.  
  
 The **sql:guid** annotation can be assigned two values:  
  
 generate  
 Specifies that the GUID generated by [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] be used for that column in the update operation.  
  
 useValue  
 Specifies that the value specified in the updategram be used for the column. This is the default value.  
  
  
