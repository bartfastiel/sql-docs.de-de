---
title: KeepExisting-Element (DTA) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: tools-other
ms.topic: conceptual
dev_langs:
- XML
helpviewer_keywords:
- KeepExisting element
ms.assetid: e67aae61-d06d-4a03-85ba-6516c3502dce
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: fc3ae8c7e11a3f5a4aa71e91463cbe80ab70c7e3
ms.sourcegitcommit: ceb7e1b9e29e02bb0c6ca400a36e0fa9cf010fca
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/03/2018
ms.locfileid: "52751552"
---
# <a name="keepexisting-element-dta"></a>KeepExisting-Element (DTA)
  Gibt die physischen Entwurfsstrukturen (Indizes, indizierte Sichten oder Partitionierung) an, die der Datenbankoptimierungsratgeber beim Generieren der Empfehlung beibehalten muss.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
<DTAInput>  
...code removed...  
    <TuningOptions>  
      <KeepExisting>...</KeepExisting>  
```  
  
## <a name="element-characteristics"></a>Elementmerkmale  
  
|Merkmal|Description|  
|--------------------|-----------------|  
|**Datentyp und -länge**|`string`, Grenzwert für die Länge wird vom Server erzwungen.|  
|**Zulässige Werte**|**NONE**<br /> Keine vorhandenen Strukturen.<br /><br /> **ALL**<br /> Alle vorhandenen Strukturen.<br /><br /> **ALIGNED**<br /> Alle Strukturen mit ausgerichteten Partitionen.<br /><br /> **CL_IDX**<br /> Alle gruppierten Indizes für Tabellen.<br /><br /> **IDX**<br /> Alle gruppierten und nicht gruppierten Indizes für Tabellen.<br /><br /> Verwenden Sie nur einen dieser Werte mit diesem Element.|  
|**Standardwert**|Keine.|  
|**Vorkommen**|Dies ist optional. Nur einmalige Verwendung pro `TuningOptions`-Element möglich.|  
  
## <a name="element-relationships"></a>Elementbeziehungen  
  
|Beziehung|Elemente|  
|------------------|--------------|  
|**Übergeordnetes Element**|[TuningOptions-Element &#40;DTA&#41;](tuningoptions-element-dta.md)|  
|**Untergeordnete Elemente**|Keine.|  
  
## <a name="example"></a>Beispiel  
 Ein Beispiel für die Verwendung dieses Elements finden Sie unter [Beispiel für eine einfache XML-Eingabedatei &#40;DTA&#41;](simple-xml-input-file-sample-dta.md).  
  
## <a name="see-also"></a>Siehe auch  
 [XML-Eingabedateireferenz &amp;#40;Datenbankoptimierungsratgeber&amp;#41;](xml-input-file-reference-database-engine-tuning-advisor.md)  
  
  
