---
title: "Beispiel: Schrittweise Wiederherstellung nur bestimmter Dateigruppen (einfaches Wiederherstellungsmodell) | Microsoft Docs"
ms.custom: ""
ms.date: "03/14/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dbe-backup-restore"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Schrittweise Wiederherstellung [SQL Server], einfaches Wiederherstellungsmodell"
  - "Wiederherstellungssequenzen [SQL Server], schrittweise"
  - "Einfaches Wiederherstellungsmodell [SQL Server], Beispiele für RESTORE"
ms.assetid: d7ad026c-5355-4308-9560-0dc843940d4f
caps.latest.revision: 28
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 28
---
# Beispiel: Schrittweise Wiederherstellung nur bestimmter Dateigruppen (einfaches Wiederherstellungsmodell)
[!INCLUDE[tsql-appliesto-ss2016-xxxx-xxxx-xxx_md](../../includes/tsql-appliesto-ss2016-xxxx-xxxx-xxx-md.md)]

  Dieses Thema ist nur für [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Datenbanken relevant, für die ein einfaches Wiederherstellungsmodell mit einer schreibgeschützten Dateigruppe verwendet wird.  
  
 Mit einer schrittweisen Wiederherstellungssequenz wird eine Datenbank phasenweise auf Dateigruppenebene wiederhergestellt, beginnend mit der primären Dateigruppe und allen sekundären Dateigruppen mit Lese-/Schreibzugriff.  
  
 In diesem Beispiel sind in der Datenbank `adb`, für die das einfache Wiederherstellungsmodell verwendet wird, drei Dateigruppen enthalten. Die Dateigruppe `A` weist Lese-/Schreibzugriff auf, die Dateigruppen `B` und `C` sind schreibgeschützt. Zu Beginn sind alle Dateigruppen online.  
  
 Die primäre Dateigruppe und die Dateigruppe `B` der `adb`-Datenbank scheinen beschädigt zu sein. Der Datenbankadministrator beschließt, sie mithilfe einer schrittweisen Wiederherstellungssequenz wiederherzustellen. Beim einfachen Wiederherstellungsmodell müssen alle Dateigruppen mit Lese-/Schreibzugriff von derselben Teilsicherung wiederhergestellt werden. Obwohl die Dateigruppe `A` intakt ist, muss sie mit der primären Dateigruppe wiederhergestellt werden, um sicherzustellen, dass beide konsistent sind (die Datenbank wird bis zu dem Zeitpunkt wiederhergestellt, der zum Ende der letzten Teilsicherung definiert wurde). Die Dateigruppe `C` ist intakt, muss jedoch wiederhergestellt werden, damit sie online geschaltet werden kann. Die Dateigruppe `B`ist zwar beschädigt, es sind darin jedoch keine so wichtigen Daten wie in Dateigruppe `C`enthalten. Deshalb wird die Dateigruppe `B` zuletzt wiederhergestellt.  
  
## Wiederherstellen von Sequenzen  
  
> [!NOTE]  
>  Die Syntax für eine Onlinewiederherstellungssequenz ist dieselbe wie bei einer Offlinewiederherstellungssequenz.  
  
1.  Teilwiederherstellung der primären Dateigruppe und der Dateigruppe `A` von einer Teilsicherung.  
  
    ```  
    RESTORE DATABASE adb READ_WRITE_FILEGROUPS FROM partial_backup   
    WITH PARTIAL, RECOVERY  
    ```  
  
     Die primäre Dateigruppe und die Dateigruppe `A` sind zu diesem Zeitpunkt online. Für Dateien in den Dateigruppen `B` und `C` steht die Wiederherstellung aus, und die Dateigruppen sind offline.  
  
2.  Onlinewiederherstellung der Dateigruppe `C`.  
  
     Dateigruppe `C` ist konsistent, weil die Teilsicherung, die weiter oben wiederhergestellt wurde, nach dem Kennzeichnen der Dateigruppe `C` als schreibgeschützt erstellt wurde, obwohl für die Datenbank ein früherer Status wiederhergestellt wurde. Der Datenbankadministrator stellt die Dateigruppe `C` wieder her, ohne die Sicherung wiederherzustellen, um sie online zu schalten.  
  
    ```  
    RESTORE DATABASE adb FILEGROUP='C' WITH RECOVERY  
    ```  
  
     Die primäre Dateigruppe und die Dateigruppen `A` und `C` sind zu diesem Zeitpunkt online. Für die Dateien in der Dateigruppe B steht weiterhin die Wiederherstellung aus, wobei die Dateigruppe offline ist.  
  
3.  Onlinewiederherstellung der Dateigruppe `B.`  
  
     Dateien in der Dateigruppe `B` müssen wiederhergestellt werden. Der Datenbankadministrator stellt die Sicherung von Dateigruppe `B` wieder her, die erstellt wurde, nachdem die Dateigruppe `B` als schreibgeschützt gekennzeichnet und bevor die Teilsicherung erstellt wurde.  
  
    ```  
    RESTORE DATABASE adb FILEGROUP='B' FROM backup   
    WITH RECOVERY  
    ```  
  
     Alle Dateigruppen sind nun online.  
  
## Zusätzliche Beispiele  
  
-   [Beispiel: Schrittweise Wiederherstellung einer Datenbank &#40;einfaches Wiederherstellungsmodell&#41;](../../relational-databases/backup-restore/example-piecemeal-restore-of-database-simple-recovery-model.md)  
  
-   [Beispiel: Onlinewiederherstellung einer schreibgeschützten Datei &#40;einfaches Wiederherstellungsmodell&#41;](../../relational-databases/backup-restore/example-online-restore-of-a-read-only-file-simple-recovery-model.md)  
  
-   [Beispiel: Schrittweise Wiederherstellung einer Datenbank &#40;Vollständiges Wiederherstellungsmodell&#41;](../../relational-databases/backup-restore/example-piecemeal-restore-of-database-full-recovery-model.md)  
  
-   [Beispiel: Schrittweise Wiederherstellung nur bestimmter Dateigruppen &#40;Vollständiges Wiederherstellungsmodell&#41;](../../relational-databases/backup-restore/example-piecemeal-restore-of-only-some-filegroups-full-recovery-model.md)  
  
-   [Beispiel: Onlinewiederherstellung einer Datei mit Lese-/Schreibzugriff &#40;vollständiges Wiederherstellungsmodell&#41;](../../relational-databases/backup-restore/example-online-restore-of-a-read-write-file-full-recovery-model.md)  
  
-   [Beispiel: Onlinewiederherstellung einer schreibgeschützten Datei &#40;vollständiges Wiederherstellungsmodell&#41;](../../relational-databases/backup-restore/example-online-restore-of-a-read-only-file-full-recovery-model.md)  
  
## Siehe auch  
 [Onlinewiederherstellungen &#40;SQL Server&#41;](../../relational-databases/backup-restore/online-restore-sql-server.md)   
 [BACKUP &#40;Transact-SQL&#41;](../../t-sql/statements/backup-transact-sql.md)   
 [RESTORE &#40;Transact-SQL&#41;](../Topic/RESTORE%20\(Transact-SQL\).md)   
 [Schrittweise Wiederherstellungen &#40;SQL Server&#41;](../../relational-databases/backup-restore/piecemeal-restores-sql-server.md)  
  
  