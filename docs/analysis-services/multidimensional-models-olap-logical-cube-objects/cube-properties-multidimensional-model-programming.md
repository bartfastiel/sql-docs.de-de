---
title: Cubeeigenschaften - mehrdimensionalen Modell Programmierung | Microsoft Docs
ms.custom: 
ms.date: 03/17/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
applies_to:
- SQL Server 2016 Preview
helpviewer_keywords:
- Collation property
- ID property
- ErrorConfiguration property
- cubes [Analysis Services], properties
- Description property
- DefaultMeasure property
- ProcessingMode property
- AggregationPrefix property
- EstimatedRows property
- Visible property
- StorageLocation property
- StorageMode property
- ScriptErrorHandlingMode property
- Source property
- ScriptCacheProcessingMode property
- Language property
- Name property
- properties [Analysis Services], cubes
- ProcessingPriority property
- ProactiveCaching property
ms.assetid: 72ca3387-620d-4473-8e23-7fe1f2b3d5bf
caps.latest.revision: 40
author: Minewiskan
ms.author: owend
manager: erikre
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 3b86278422fc1e3ec91845c223adc56640602739
ms.contentlocale: de-de
ms.lasthandoff: 09/01/2017

---
# <a name="cube-properties---multidimensional-model-programming"></a>Cubeeigenschaften - mehrdimensionalen Modell Programmierung
  Cubes verfügen über eine Reihe von Eigenschaften, die Sie festlegen können und die sich auf das cubeweite Verhalten auswirken. Diese Eigenschaften sind in der folgenden Tabelle zusammengefasst.  
  
> [!NOTE]  
>  Manche Eigenschaften werden beim Erstellen des Cubes automatisch festgelegt und können nicht geändert werden.  
  
 Weitere Informationen zum Festlegen von Cubeeigenschaften finden Sie unter [Cube-Designer &#40; Analysis Services – mehrdimensionale Daten &#41; ](http://msdn.microsoft.com/library/a6692467-da88-4312-8b03-d812f2ae5a96).  
  
|Eigenschaft|Description|  
|--------------|-----------------|  
|**AggregationPrefix**|Gibt das für Aggregationsnamen verwendete gemeinsame Präfix an.|  
|**Sortierung**|Gibt den Gebietsschemabezeichner (LCID) und das Vergleichsflag, durch einen Unterstrich voneinander getrennt, an, wie z. B. Latin1_General_C1_AS.|  
|**DefaultMeasure**|Enthält einen mehrdimensionalen Ausdruck (Multidimensional Expression, MDX), der das Standardmeasure für den Cube definiert.|  
|**Description**|Stellt eine Beschreibung des Cubes bereit, die in Clientanwendungen verwendet werden kann.|  
|**ErrorConfiguration**|Enthält konfigurierbare Fehlerbehandlungseinstellungen für die Bearbeitung doppelter Schlüssel, unbekannter Schlüssel, für Fehlergrenzen, Aktionen bei Erkennung von Fehlern, Fehlerprotokolldateien und die Bearbeitung von NULL-Schlüsseln.|  
|**EstimatedRows**|Gibt die Anzahl der geschätzten Zeilen im Cube an.|  
|**ID**|Enthält den eindeutigen Bezeichner (ID) des Cubes.|  
|**Sprache**|Gibt den Standardsprachbezeichner für den Cube an.|  
|**Name**|Gibt den benutzerfreundlichen Namen des Attributs an.|  
|**ProactiveCaching**|Definiert die Einstellungen für den Cube für die proaktive Zwischenspeicherung.|  
|**ProcessingMode**|Gibt an, ob während oder nach der Verarbeitung indiziert und aggregiert werden soll. Optionen sind **reguläre** oder **lazy**.|  
|**ProcessingPriority**|Legt die Verarbeitungspriorität des Cubes bei Hintergrundvorgängen wie z. B. verzögerte Aggregationen und Indizierungen fest. Der Standardwert ist **0**.|  
|**ScriptCacheProcessingMode**|Gibt an, ob der Skriptcache während oder nach der Verarbeitung erstellt werden soll. Optionen sind **reguläre** und **lazy**.|  
|**ScriptErrorHandlingMode**|Bestimmt die Fehlerbehandlung. Optionen sind **' ignorenone '** oder **' ignoreall '**|  
|**Quelle**|Zeigt die für den Cube verwendete Datenquellensicht.|  
|**StorageLocation**|Gibt den Speicherort des Dateisystems für den Cube an. Wenn kein Speicherort angegeben ist, wird er von der Datenbank geerbt, die das Cubeobjekt enthält.|  
|**StorageMode**|Gibt den Speichermodus für den Cube an. Werte sind **MOLAP**, **ROLAP**, oder **HOLAP ***.**|  
|**Visible**|Bestimmt die Sichtbarkeit des Cubes.|  
  
> [!NOTE]  
>  Weitere Informationen zum Festlegen von Werten für die ErrorConfiguration-Eigenschaft, bei der Arbeit mit null-Werte und anderen Problemen mit der Datenintegrität finden Sie unter [Handling Data Integrity Issues in Analysis Services 2005](http://go.microsoft.com/fwlink/?LinkId=81891).  
  
## <a name="see-also"></a>Siehe auch  
 [Proaktives Zwischenspeichern &#40; Partitionen &#41;](../../analysis-services/multidimensional-models-olap-logical-cube-objects/partitions-proactive-caching.md)  
  
  