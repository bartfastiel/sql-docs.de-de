---
title: Namespaceunterstützung im PATH-Modus | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: xml
ms.topic: conceptual
helpviewer_keywords:
- PATH FOR XML mode, namespace support
- namespaces [XML in SQL Server]
ms.assetid: 5f128ea2-0ceb-4b23-bce7-c8b3fd615466
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 19c932a3927e71208e4b1c82c8c3bce4cbadfd8b
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/01/2018
ms.locfileid: "47747038"
---
# <a name="namespace-support-in-path-mode"></a>Namespaceunterstützung im PATH-Modus
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]
  Die Unterstützung von Namespaces im PATH-Modus wird durch den Einsatz von WITH NAMESPACES bereitgestellt. Beispielsweise zeigt die folgende Abfrage die Syntax von WITH NAMESPACES, um einen Namespace ("a:") zu deklarieren, der in der nachfolgenden SELECT-Anweisung verwendet werden kann:  
  
```  
WITH XMLNAMESPACES('a' as a)  
SELECT 1 as 'a:b'  
FOR XML PATH  
```  
  
## <a name="examples"></a>Beispiele  
 Diese Beispiele veranschaulichen die Verwendung des PATH-Modus beim Generieren von XML-Code aus einer SELECT-Abfrage. Viele dieser Abfragen beziehen sich auf die XML-Dokumente mit den Fahrradfertigungsanweisungen, die in der Instructions-Spalte der ProductModel-Tabelle gespeichert sind.  
  
## <a name="see-also"></a>Weitere Informationen finden Sie unter  
 [Verwenden des PATH-Modus mit FOR XML](../../relational-databases/xml/use-path-mode-with-for-xml.md)  
  
  
