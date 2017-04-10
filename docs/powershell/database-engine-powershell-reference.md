---
title: "PowerShell-Referenz (Datenbankmodul) | Microsoft Docs"
ms.custom: ""
ms.date: "03/14/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "database-engine"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 3c379a43-c497-47dd-8e7d-2b015c068bb7
caps.latest.revision: 8
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 8
---
# PowerShell-Referenz (Datenbankmodul)
  [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] beinhaltet eine Reihe von Windows PowerShell-Cmdlets zur Durchführung allgemeiner Aufgaben im [!INCLUDE[ssDE](../includes/ssde-md.md)]. Zudem können Abfrageausdrücke und Uniform Resource Names (URNs) in SQL Server PowerShell-Pfade konvertiert oder zum Angaben eines oder mehrerer Objekte im [!INCLUDE[ssDE](../includes/ssde-md.md)] verwendet werden.  
  
## Datenbankmodul-Cmdlets  
 [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)] beinhaltet relativ wenige Cmdlets für das [!INCLUDE[ssDE](../includes/ssde-md.md)]. Die meisten PowerShell-Skripts, die mit dem [!INCLUDE[ssDE](../includes/ssde-md.md)] verwendet werden, nutzen den SQL Server PowerShell-Anbieter und die Verwaltbarkeitsobjektmodelle. Weitere Informationen finden Sie unter [SQL Server PowerShell Provider](../relational-databases/scripting/sql-server-powershell-provider.md).  
  
 Informationen zum Anfordern von Hilfe zu den SQL Server-Cmdlets in einer Windows PowerShell-Umgebung finden Sie unter [Get Help SQL Server PowerShell](../relational-databases/scripting/get-help-sql-server-powershell.md).  
  
### In diesem Abschnitt  
 Dieser Abschnitt enthält Informationen zu den folgenden Cmdlets.  
  
|Beschreibung|Cmdlet|  
|-----------------|------------|  
|Führt Transact-SQL- und XQuery-Skripte aus, z.B. Skripts, die mit dem Hilfsprogramm **sqlcmd** ausgeführt werden können.|[Invoke-Sqlcmd-Cmdlet](../powershell/invoke-sqlcmd-cmdlet.md)|  
|Ermittelt, ob ein Datenbankmodulobjekt einer Richtlinie für die richtlinienbasierte Verwaltung entspricht.|[Invoke-PolicyEvaluation-Cmdlet](../powershell/invoke-policyevaluation-cmdlet.md)|  
  
### Informationen zu anderen Cmdlets  
 Das **Encode-Sqlname**-Cmdlet und das **Decode-Sqlname**-Cmdlet helfen Ihnen, SQL Server-Bezeichner mit Zeichen anzugeben, die in PowerShell-Pfaden nicht unterstützt werden. Weitere Informationen finden Sie unter [SQL Server Identifiers in PowerShell](../relational-databases/scripting/sql-server-identifiers-in-powershell.md).  
  
 Mit dem **Convert-UrnToPath**-Cmdlet können Sie einen eindeutigen Ressourcennamen (Unique Resource Name, URN) für ein [!INCLUDE[ssDE](../includes/ssde-md.md)]-Objekt einen Pfad für den SQL Server PowerShell-Anbieter konvertieren. Weitere Informationen finden Sie unter [Convert URNs to SQL Server Provider Paths](../relational-databases/scripting/convert-urns-to-sql-server-provider-paths.md).  
  
## Abfrageausdrücke und eindeutige Ressourcennamen  
 Bei Abfrageausdrücken handelt es sich um Zeichenfolgen, die eine ähnliche Syntax wie XPath nutzen, um eine Gruppe von Kriterien angeben, mit der ein oder mehrere Objekte in einer Objektmodellhierarchie aufgezählt werden. Ein eindeutiger Ressourcenname (Unique Resource Name, URN) ist ein spezieller Typ einer Abfrageausdrucks-Zeichenfolge, der ein einzelnes Objekt eindeutig kennzeichnet. Weitere Informationen finden Sie unter [Query Expressions and Uniform Resource Names](../powershell/query-expressions-and-uniform-resource-names.md).  
  
## Siehe auch  
 [SQL Server-PowerShell](../relational-databases/scripting/sql-server-powershell.md)  
  
  