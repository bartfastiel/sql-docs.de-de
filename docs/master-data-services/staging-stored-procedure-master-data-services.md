---
title: "Gespeicherte Stagingprozedur (Master Data Services) | Microsoft Docs"
ms.custom: ""
ms.date: "04/01/2016"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "master-data-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 6a613106-9f87-4caf-a23a-a726fc6561c5
caps.latest.revision: 15
author: "sabotta"
ms.author: "carlasab"
manager: "jhubbard"
caps.handback.revision: 15
---
# Gespeicherte Stagingprozedur (Master Data Services)
  Wenn Sie den Stagingprozess von [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)]initiieren, verwenden Sie eine von drei gespeicherten Prozeduren.  
  
-   stg.udp_\<Name>_Leaf  
  
-   stg.udp_\<Name>_Consolidated  
  
-   stg.udp_\<Name>_Relationship  
  
 "name" steht für den Namen der Stagingtabelle, die beim Erstellen der Entität angegeben wurde.  
  
## Parameter der gespeicherten Prozeduren für den Stagingprozess  
 In der folgenden Tabelle sind die Parameter dieser gespeicherten Prozeduren aufgeführt.  
  
|Parameter|Description|  
|---------------|-----------------|  
|**VersionName**<br /><br /> Required|Der Name der Version. Dabei wird ggf. abhängig von der [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]-Sortiereinstellung die Groß-/Kleinschreibung beachtet.|  
|**LogFlag**<br /><br /> Required|Bestimmt, ob Transaktionen während des Stagingprozesses protokolliert werden. Folgende Werte sind möglich:<br /><br /> **0**: Transaktionen nicht protokollieren.<br /><br /> **1**: Transaktionen protokollieren.<br /><br /> <br /><br /> Weitere Informationen über Transaktionen finden Sie unter [Transaktionen &#40;Master Data Services&#41;](../master-data-services/transactions-master-data-services.md).|  
|**BatchTag**<br /><br /> Erforderlich, außer vom Webdienst|Der **BatchTag** -Wert wie in der Stagingtabelle angegeben.|  
|**Batch_ID**<br /><br /> Wird nur vom Webdienst benötigt|Der Wert der **Batch_ID** wie in der Stagingtabelle angegeben.|  
|**Benutzername**|Optionaler Parameter:|  
|**Benutzer-ID**|Optionaler Parameter:|  
  
### Beispiel einer gespeicherten Prozedur für den Stagingprozess  
 Im folgenden Beispiel wird gezeigt, wie der Stagingprozess mit der entsprechenden gespeicherten Prozedur gestartet wird.  
  
```  
USE [DATABASE_NAME]  
GO  
  
EXEC[stg].[udp_name_Leaf]  
      @VersionName = N'VERSION_1',  
@LogFlag = 1,  
@BatchTag = N'batch1'  
      @UserName=N’domain\user’  
  
GO  
  
```  
  
## Siehe auch  
 [Gespeicherte Überprüfungsprozedur &#40;Master Data Services&#41;](../master-data-services/validation-stored-procedure-master-data-services.md)   
 [Anzeigen von Fehlern, die während des Stagings auftreten &#40;Master Data Services&#41;](../master-data-services/view-errors-that-occur-during-staging-master-data-services.md)  
  
  