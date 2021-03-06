---
title: Zuordnen von XSD-Datentypen zu XPath-Datentypen (SQLXML 4.0) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: reference
helpviewer_keywords:
- mapping data types [SQLXML]
- data types [SQLXML], converting
- annotated XSD schemas, mapping data types
- XPath queries [SQLXML], mapping data types
- converting data types [SQLXML]
- data types [SQLXML], mapping data types
- XPath data types [SQLXML]
- XSD schemas [SQLXML], mapping data types
ms.assetid: ced1a95e-18d4-4a5a-8da8-dbb6d58bbd45
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: e1e74f5d2cfdd80e3d8a348808d9ecd6d8f38219
ms.sourcegitcommit: ceb7e1b9e29e02bb0c6ca400a36e0fa9cf010fca
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/03/2018
ms.locfileid: "52793512"
---
# <a name="mapping-xsd-data-types-to-xpath-data-types-sqlxml-40"></a>Zuordnen von XSD-Datentypen zu XPath-Datentypen (SQLXML 4.0)
  Wenn eine XPath-Abfrage für ein XSD-Schema ausgeführt wird und der XSD-Typ im `xsd:type`-Attribut angegeben ist, verwendet XPath den Datentyp, der bei der Verarbeitung der Abfrage angegeben wird.  
  
 Der XPath-Datentyp eines Knotens wird vom XSD-Datentyp in dem Schema abgeleitet, wie in der folgenden Tabelle dargestellt. (Der Knoten "EmployeeID" dient zur Veranschaulichung.)  
  
|XSD-Datentyp|XDR-Datentyp|Entsprechung<br /><br /> XPath-Datentyp|SQL Server<br /><br /> verwendete Konvertierung|  
|-------------------|-------------------|------------------------------------|--------------------------------------------|  
|`Base64Binary`<br /><br /> `HexBinary`|`None`<br /><br /> `bin.base64bin.hex`|`Not applicable`|None<br /><br /> EmployeeID|  
|`Boolean`|`boolean`|`boolean`|CONVERT(bit, EmployeeID)|  
|`Decimal, integer, float, byte, short, int, long, float, double, unsignedByte, unsignedShort, unsignedInt, unsignedLong`|`number, int, float,i1, i2, i4, i8,r4, r8ui1, ui2, ui4, ui8`|`number`|CONVERT(float(53), EmployeeID)|  
|`id, idref, idrefsentity, entities, notation, nmtoken, nmtokens, DateTime, string, AnyURI`|`id, idref, idrefsentity, entities, enumeration, notation, nmtoken, nmtokens, char, dateTime, dateTime.tz, string, uri, uuid`|`string`|CONVERT(nvarchar(4000), EmployeeID, 126)|  
|`decimal`|`fixed14.4`|`Not applicable (There is no data type in XPath that is equivalent to the fixed14.4 XDR data type.)`|CONVERT(money, EmployeeID)|  
|`date`|`date`|`string`|LEFT(CONVERT(nvarchar(4000), EmployeeID, 126), 10)|  
|`time`|`time`<br /><br /> `time.tz`|`string`|SUBSTRING(CONVERT(nvarchar(4000), EmployeeID, 126), 1 + CHARINDEX(N'T', CONVERT(nvarchar(4000), EmployeeID, 126)), 24)|  
  
  
