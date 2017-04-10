---
title: "Deaktivieren von Stretch-Datenbank und Zur&#252;ckholen von Remotedaten | Microsoft Docs"
ms.custom: 
  - "SQL2016_New_Updated"
ms.date: "08/05/2016"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.service: "sql-server-stretch-database"
ms.suite: ""
ms.technology: 
  - "dbe-stretch"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Stretch-Datenbank, Deaktivierung"
  - "Stretch-Datenbank deaktivieren"
ms.assetid: c1bbb24e-47e3-46aa-b786-fcadf9fb65ce
caps.latest.revision: 33
author: "douglaslMS"
ms.author: "douglasl"
manager: "jhubbard"
caps.handback.revision: 32
---
# Deaktivieren von Stretch-Datenbank und Zur&#252;ckholen von Remotedaten
[!INCLUDE[tsql-appliesto-ss2016-xxxx-xxxx-xxx_md](../../includes/tsql-appliesto-ss2016-xxxx-xxxx-xxx-md.md)]

  Wählen Sie **Stretch** für eine Tabelle in SQL Server Management Studio aus, um Stretch-Datenbank für eine Tabelle zu deaktivieren. Wählen Sie anschließend eine der folgenden Optionen aus:  
  
-   **Deaktivieren | Daten aus Azure zurückholen**. Kopieren Sie die Remotedaten für die Tabelle aus Azure zu SQL Server, und deaktivieren Sie anschließend Stretch-Datenbank für die Tabelle. Dieser Vorgang verursacht Datenübertragungskosten und kann nicht abgebrochen werden.  
  
-   **Deaktivieren | Daten in Azure belassen**. Deaktivieren Sie Stretch-Datenbank für die Tabelle.  Verwerfen Sie die Remotedaten für die Tabelle in Azure.  
  
 Sie können alternativ Transact-SQL verwenden, um Stretch-Datenbank für eine Tabelle oder Datenbank zu deaktivieren.  
  
 Nachdem Sie Stretch-Datenbank für eine Tabelle deaktiviert haben, wird die Datenmigration beendet und die Abfrageergebnisse enthalten keine Ergebnisse aus der Remotetabelle mehr.  
  
 Wenn Sie die Datenmigration einfach anhalten möchten, finden Sie Informationen dazu unter [Anhalten und Fortsetzen der Datenmigration &#40;Stretch-Datenbank&#41;](../../sql-server/stretch-database/pause-and-resume-data-migration-stretch-database.md).  
  
> [!NOTE] Durch die Deaktivierung von Stretch-Datenbank für eine Tabelle oder Datenbank wird das Remoteobjekt nicht gelöscht. Wenn Sie die Remotetabelle oder Remotedatenbank löschen möchten, müssen Sie sie mithilfe des Azure-Verwaltungsportals löschen. Die Remoteobjekte erzeugen weiterhin Azure-Kosten, bis Sie die Objekte löschen. Weitere Informationen finden Sie unter [SQL Server Stretch-Datenbank – Preise](https://azure.microsoft.com/pricing/details/sql-server-stretch-database/).  
  
## Deaktivieren von Stretch-Datenbank für eine Tabelle  
  
### Verwenden Sie SQL Server Management Studio, um Stretch-Datenbank für eine Tabelle zu deaktivieren.  
  
1.  Wählen Sie in SQL Server Management Studio im Objekt-Explorer die Tabelle aus, für die Sie Stretch-Datenbank deaktivieren möchten.  
  
2.  Klicken Sie mit der rechten Maustaste auf **Stretch**, und wählen Sie eine der folgenden Optionen aus.  
  
    -   **Deaktivieren | Daten aus Azure zurückholen**. Kopieren Sie die Remotedaten für die Tabelle aus Azure zu SQL Server, und deaktivieren Sie anschließend Stretch-Datenbank für die Tabelle. Dieser Befehl kann nicht abgebrochen werden.  
  
        > [!NOTE] Das Kopieren der Remotedaten der Tabelle von Azure zurück zu SQL Server generiert Datenübertragungskosten. Weitere Informationen finden Sie unter [Datenübertragungen – Preisdetails](https://azure.microsoft.com/pricing/details/data-transfers/).  
  
         Nachdem die Remotedaten von Azure zurück zu SQL Server kopiert wurden, wird Stretch für die Tabelle deaktiviert.  
  
    -   **Deaktivieren | Daten in Azure belassen**. Deaktivieren Sie Stretch-Datenbank für die Tabelle.  Verwerfen Sie die Remotedaten für die Tabelle in Azure.  
  
    > [!NOTE] Durch die Deaktivierung von Stretch-Datenbank für eine Tabelle werden die Remotedaten oder die Remotetabelle nicht gelöscht. Wenn Sie die Remotetabelle löschen möchten, müssen Sie sie mithilfe des Azure-Verwaltungsportals löschen. Die Remotetabelle erzeugt weiterhin Kosten in Azure, bis Sie sie löschen. Weitere Informationen finden Sie unter [SQL Server Stretch-Datenbank – Preise](https://azure.microsoft.com/pricing/details/sql-server-stretch-database/).  
  
### Verwenden von Transact-SQL zum Deaktivieren von Stretch-Datenbank für eine Tabelle  
  
-   Führen Sie den folgenden Befehl aus, um Stretch für eine Tabelle zu deaktivieren und die Remotedaten einer Tabelle aus Azure zurück zu SQL Server zu kopieren. Nachdem die Remotedaten von Azure zurück zu SQL Server kopiert wurden, wird Stretch für die Tabelle deaktiviert.

    Dieser Befehl kann nicht abgebrochen werden.  
  
    ```tsql  
    USE <Stretch-enabled database name>;
    GO
    ALTER TABLE <Stretch-enabled table name>  
       SET ( REMOTE_DATA_ARCHIVE ( MIGRATION_STATE = INBOUND ) ) ; 
    GO 
    ```  
  
    > [!NOTE] Das Kopieren der Remotedaten der Tabelle von Azure zurück zu SQL Server generiert Datenübertragungskosten. Weitere Informationen finden Sie unter [Datenübertragungen – Preisdetails](https://azure.microsoft.com/pricing/details/data-transfers/).    
  
-   Führen Sie den folgenden Befehl aus, um Stretch für eine Tabelle zu deaktivieren und die Remotedaten zu verwerfen.  
  
    ```tsql  
    USE <Stretch-enabled database name>;
    GO
    ALTER TABLE <Stretch-enabled table name>  
       SET ( REMOTE_DATA_ARCHIVE = OFF_WITHOUT_DATA_RECOVERY ( MIGRATION_STATE = PAUSED ) ) ; 
    GO
    ```  
  
> [!NOTE] Durch die Deaktivierung von Stretch-Datenbank für eine Tabelle werden die Remotedaten oder die Remotetabelle nicht gelöscht. Wenn Sie die Remotetabelle löschen möchten, müssen Sie sie mithilfe des Azure-Verwaltungsportals löschen. Die Remotetabelle erzeugt weiterhin Kosten in Azure, bis Sie sie löschen. Weitere Informationen finden Sie unter [SQL Server Stretch-Datenbank – Preise](https://azure.microsoft.com/pricing/details/sql-server-stretch-database/).  
  
## Deaktivieren von Stretch-Datenbank für eine Datenbank  
 Bevor Sie Stretch-Datenbank für eine Datenbank deaktivieren können, müssen Sie Stretch-Datenbank in den einzelnen, für Stretch aktivierten Tabellen in der Datenbank deaktivieren.  
  
### Verwenden von SQL Server Management Studio zum Deaktivieren von Stretch-Datenbank für eine Datenbank  
  
1.  Wählen Sie in SQL Server Management Studio im Objekt-Explorer die Datenbank aus, für die Sie Stretch-Datenbank deaktivieren möchten.  
  
2.  Klicken Sie mit der rechten Maustaste auf **Aufgaben**, **Stretch** und anschließend auf **Deaktivieren**.  
  
> [!NOTE] Durch die Deaktivierung von Stretch-Datenbank für eine Datenbank wird die Remotedatenbank nicht gelöscht. Wenn Sie die Remotedatenbank löschen möchten, müssen Sie sie mithilfe des Azure-Verwaltungsportals löschen. Die Remotedatenbank erzeugt weiterhin Kosten in Azure, bis Sie sie löschen. Weitere Informationen finden Sie unter [SQL Server Stretch-Datenbank – Preise](https://azure.microsoft.com/pricing/details/sql-server-stretch-database/).  
  
### Verwenden von Transact-SQL zum Deaktivieren von Stretch-Datenbank für eine Datenbank  
 Führen Sie den folgenden Befehl aus.  
  
```tsql  
ALTER DATABASE <Stretch-enabled database name>  
    SET REMOTE_DATA_ARCHIVE = OFF ;  
GO 
```  
  
> [!NOTE] Durch die Deaktivierung von Stretch-Datenbank für eine Datenbank wird die Remotedatenbank nicht gelöscht. Wenn Sie die Remotedatenbank löschen möchten, müssen Sie sie mithilfe des Azure-Verwaltungsportals löschen. Die Remotedatenbank erzeugt weiterhin Kosten in Azure, bis Sie sie löschen. Weitere Informationen finden Sie unter [SQL Server Stretch-Datenbank – Preise](https://azure.microsoft.com/pricing/details/sql-server-stretch-database/).  
  
## Siehe auch  
 [ALTER DATABASE SET-Optionen &#40;Transact-SQL&#41;](../Topic/ALTER%20DATABASE%20SET%20Options%20\(Transact-SQL\).md)   
 [Anhalten und Fortsetzen der Datenmigration &#40;Stretch Database&#41;](../../sql-server/stretch-database/pause-and-resume-data-migration-stretch-database.md)  
  
  