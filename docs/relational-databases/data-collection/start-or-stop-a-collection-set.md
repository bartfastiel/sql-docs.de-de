---
title: Starten oder Beenden eines Sammlungssatzes | Microsoft Dokumentation
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- collection sets [SQL Server], stopping
- collection sets [SQL Server], starting
ms.assetid: 48a7b2fe-6bc3-4278-a7ec-1babc1290345
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 5669af5105e8d46f346d279b3be8027b7c22088d
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/01/2018
ms.locfileid: "47700098"
---
# <a name="start-or-stop-a-collection-set"></a>Starten oder Beenden eines Sammlungssatzes
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  In diesem Thema wird beschrieben, wie ein Sammlungssatz in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] mithilfe von [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] oder [!INCLUDE[tsql](../../includes/tsql-md.md)]gestartet oder angehalten wird.  
  
 **In diesem Thema**  
  
-   **Vorbereitungen:**  
  
     [Einschränkungen](#Restrictions)  
  
     [Erforderliche Komponenten](#Prerequisites)  
  
     [Empfehlungen](#Recommendations)  
  
     [Security](#Security)  
  
-   **So starten oder halten Sie einen Sammlungssatz an, und zwar mit**  
  
     [SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
##  <a name="BeforeYouBegin"></a> Vorbereitungsmaßnahmen  
  
###  <a name="Restrictions"></a> Einschränkungen  
  
-   Gespeicherte Prozeduren für den Datensammler und Katalogsichten werden in der **msdb** -Datenbank gespeichert.  
  
-   Im Gegensatz zu regulären gespeicherten Prozeduren werden die Parameter für die gespeicherten Prozeduren des Datensammlers genau eingegeben und unterstützen die automatische Datentypkonvertierung nicht. Wenn diese Parameter nicht mit den richtigen Datentypen für Eingabeparameter aufgerufen werden, wie in der Argumentbeschreibung angegeben, gibt die gespeicherte Prozedur einen Fehler zurück.  
  
###  <a name="Prerequisites"></a> Erforderliche Komponenten  
  
-   Der SQL Server-Agent muss gestartet werden.  
  
###  <a name="Recommendations"></a> Empfehlungen  
  
-   Fragen Sie die [syscollector_collection_sets](../../relational-databases/system-catalog-views/syscollector-collection-sets-transact-sql.md) -Katalogsicht ab, um Informationen zu Sammlungssätzen abzurufen.  
  
###  <a name="Security"></a> Sicherheit  
  
####  <a name="Permissions"></a> Berechtigungen  
 Erfordert die Mitgliedschaft in der festen Datenbankrolle **dc_operator** . Wenn der Sammlungssatz über kein Proxykonto verfügt, ist die Mitgliedschaft in der festen Serverrolle **sysadmin** erforderlich. Beispiele  
  
##  <a name="SSMSProcedure"></a> Verwenden von SQL Server Management Studio  
  
#### <a name="to-start-a-collection-set"></a>So starten Sie einen Sammlungssatz  
  
1.  Erweitern Sie im Objekt-Explorer nacheinander die Knoten **Verwaltung** , **Datensammlung**und dann **Systemdaten-Sammlungssätze**.  
  
2.  Klicken Sie mit der rechten Maustaste auf den Sammlungssatz, den Sie starten möchten, und klicken Sie anschließend auf **Datenauflistsatz starten**.  
  
     Ein Meldungsfeld mit dem Ergebnis des Vorgangs wird angezeigt, und ein grüner Pfeil auf dem Symbol für den Sammlungssatz weist darauf hin, dass der Sammlungssatz gestartet wurde.  
  
#### <a name="to-stop-a-collection-set"></a>So beenden Sie einen Sammlungssatz  
  
1.  Erweitern Sie im Objekt-Explorer nacheinander die Knoten **Verwaltung** , **Datensammlung**und dann **Systemdaten-Sammlungssätze**.  
  
2.  Klicken Sie mit der rechten Maustaste auf den Sammlungssatz, den Sie beenden möchten, und klicken Sie anschließend auf **Datensammlungssatz beenden**.  
  
     Ein Meldungsfeld mit den Ergebnissen dieses Vorgangs wird angezeigt, und ein roter Kreis auf dem Symbol für den Sammlungssatz weist darauf hin, dass der Sammlungssatz beendet wurde.  
  
##  <a name="TsqlProcedure"></a> Verwenden von Transact-SQL  
  
#### <a name="to-start-a-collection-set"></a>So starten Sie einen Sammlungssatz  
  
1.  Stellen Sie eine Verbindung mit dem [!INCLUDE[ssDE](../../includes/ssde-md.md)]her.  
  
2.  Klicken Sie in der Standardleiste auf **Neue Abfrage**.  
  
3.  Kopieren Sie das folgende Beispiel, fügen Sie es in das Abfragefenster ein, und klicken Sie auf **Ausführen**. In diesem Beispiel wird [sp_syscollector_start_collection_set](../../relational-databases/system-stored-procedures/sp-syscollector-start-collection-set-transact-sql.md) verwendet, um den Sammlungssatz zu starten, der über die ID von `1`verfügt.  
  
```sql  
USE msdb;  
GO  
EXEC sp_syscollector_start_collection_set @collection_set_id = 1;  
```  
  
#### <a name="to-stop-a-collection-set"></a>So beenden Sie einen Sammlungssatz  
  
1.  Stellen Sie eine Verbindung mit dem [!INCLUDE[ssDE](../../includes/ssde-md.md)]her.  
  
2.  Klicken Sie in der Standardleiste auf **Neue Abfrage**.  
  
3.  Kopieren Sie das folgende Beispiel, fügen Sie es in das Abfragefenster ein, und klicken Sie auf **Ausführen**. In diesem Beispiel wird [sp_syscollector_stop_collection_set](../../relational-databases/system-stored-procedures/sp-syscollector-stop-collection-set-transact-sql.md) verwendet, um den Sammlungssatz anzuhalten, der über die ID von `1`verfügt.  
  
```sql  
USE msdb;  
GO  
EXEC sp_syscollector_stop_collection_set @collection_set_id = 1;  
```  
  
## <a name="see-also"></a>Weitere Informationen finden Sie unter  
 [Sichten des Datensammlers &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/data-collector-views-transact-sql.md)   
 [Datensammlung](../../relational-databases/data-collection/data-collection.md)  
  
  
