---
title: Aktivitätsmonitor | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
s.technology: performance
ms.topic: conceptual
helpviewer_keywords:
- Activity Monitor [SQL Server]
ms.assetid: 1e6c430d-3a2a-468e-a3d5-ef5459c36c15
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: 533838b933cbe41e868f921bee6eafe14df44def
ms.sourcegitcommit: ca038f1ef180e4e1b27910bbc5d87822cd1ed176
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 11/20/2018
ms.locfileid: "52158018"
---
# <a name="activity-monitor"></a>Aktivitätsmonitor
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  Im Aktivitätsmonitor werden Informationen zu [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Prozessen angezeigt sowie Informationen dazu, welche Auswirkungen diese Prozesse auf die aktuelle Instanz von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]haben.  
  
 Der Aktivitätsmonitor ist ein Dokumentfenster im Registerformat mit den folgenden erweiterbaren und reduzierbaren Bereichen: **Übersicht**, **Aktive Benutzertasks**, **Ressourcenwartevorgänge**, **Datendatei-E/A**und **Aktuelle wertvolle Abfragen**. Wenn ein Bereich erweitert wird, fragt der Aktivitätsmonitor die Instanz nach Informationen ab. Wenn ein Bereich reduziert wird, werden sämtliche Abfrageaktivitäten für diesen Bereich angehalten. Sie können einen oder mehrere Bereiche gleichzeitig erweitern, um unterschiedliche Aktivitätstypen für die Instanz anzuzeigen.  
 
 ## <a name="customize-columns"></a>Anpassen von Spalten 
 Für die Spalten in den Bereichen **Aktive Benutzertasks**, **Ressourcenwartevorgänge**, **Datendatei-E/A**und **Aktuelle wertvolle Abfragen** können Sie die Anzeige auf folgende Weise anpassen:  
  
1.  Um die Spaltenreihenfolge zu ändern, klicken Sie auf die Spaltenüberschrift, und ziehen Sie diese an eine andere Stelle des Menübands.  
  
2.  Um eine Spalte zu sortieren, klicken Sie auf den Spaltennamen.  
  
3.  Um eine oder mehrere Spalten zu filtern, klicken Sie in der Spaltenüberschrift auf den Dropdownpfeil, und wählen Sie anschließend einen Wert aus.  
  
## <a name="more-information"></a>Weitere Informationen  
   
|||  
|-|-|  
|Beschreibt das Öffnen des Aktivitätsmonitors und das Festlegen des Aktualisierungsintervalls für den Aktivitätsmonitor.|[Öffnen des Aktivitätsmonitors &#40;SQL Server Management Studio&#41;](../../relational-databases/performance-monitor/open-activity-monitor-sql-server-management-studio.md)|  
|Stellt Links zu Themen zum Überwachen der Serverleistung und -aktivität bereit.|[Überwachen der Serverleistung und -aktivität](../../relational-databases/performance/server-performance-and-activity-monitoring.md)|  
  
  
