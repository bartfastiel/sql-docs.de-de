---
title: "Voraussetzungen f&#252;r das Migrieren vom Protokollversand zu AlwaysOn-Verf&#252;gbarkeitsgruppen (SQL Server) | Microsoft Docs"
ms.custom: ""
ms.date: "03/14/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dbe-high-availability"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Protokollversand [SQL Server], AlwaysOn-Verfügbarkeitsgruppen"
  - "Verfügbarkeitsgruppen [SQL Server], Interoperabilität"
ms.assetid: 2738ce65-205e-4682-92d8-dc7e37c58b2b
caps.latest.revision: 24
ms.author: "mikeray"
manager: "jhubbard"
---
# Voraussetzungen f&#252;r das Migrieren vom Protokollversand zu AlwaysOn-Verf&#252;gbarkeitsgruppen (SQL Server)
[!INCLUDE[tsql-appliesto-ss2016-xxxx-xxxx-xxx_md](../../../includes/tsql-appliesto-ss2016-xxxx-xxxx-xxx-md.md)]

  In diesem Thema werden die erforderlichen Komponenten zum Konvertieren einer primären Datenbank für den Protokollversand zusammen mit einer oder mehreren sekundären Datenbanken in eine primäre AlwaysOn-Datenbank und sekundäre Datenbank(en) beschrieben.  
  
> [!NOTE]  
>  Sie können jede primäre oder sekundäre (ggf. lesbare) Datenbank in einer Verfügbarkeitsgruppe als primäre Datenbank für den Protokollversand konfigurieren.  
  
 **In diesem Thema:**  
  
-   [Erforderliche Komponenten für Verfügbarkeitsgruppen](#AGPrereqsRealAddress)  
  
-   [Erforderliche Komponenten für den Protokollversand](#LogShipPrereqs)  
  
-   [Verwandte Aufgaben](#RelatedTasks)  
  
-   [Verwandte Inhalte](#RelatedContent)  
  
##  <a name="AGPrereqsRealAddress"></a> Erforderliche Komponenten für Verfügbarkeitsgruppen  
 Damit Sicherungsaufträge auf dem primären Replikat der Verfügbarkeitsgruppe ausgeführt werden können, verwenden Sie die folgenden Sicherungseinstellungen für AlwaysOn-Verfügbarkeitsgruppen:  
  
|Eigenschaft|Einstellung|  
|--------------|-------------|  
|Die Voreinstellung für die automatisierte Sicherung der Verfügbarkeitsgruppe.|Nur auf dem primären Replikat|  
|Sicherungspriorität des primären Replikats.|>0|  
  
 **Weitere Informationen:  **  
  
 [Anzeigen von Verfügbarkeitsgruppeneigenschaften &#40;SQL Server&#41;](../../../database-engine/availability-groups/windows/view-availability-group-properties-sql-server.md)  
  
 [Konfigurieren der Sicherung auf Verfügbarkeitsreplikaten &#40;SQL Server&#41;](../../../database-engine/availability-groups/windows/configure-backup-on-availability-replicas-sql-server.md)  
  
##  <a name="LogShipPrereqs"></a> Erforderliche Komponenten für den Protokollversand  
  
-   Die primäre Datenbank für den Protokollversand muss sich auf der Instanz von [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] befinden, auf der das anfängliche/aktuelle primäre Replikat der Verfügbarkeitsgruppe gehostet wird.  
  
-   Damit eine angegebene sekundäre Datenbank für den Protokollversand in eine sekundäre AlwaysOn-Datenbank konvertiert werden kann, muss Folgendes erfüllt sein:  
  
    -   Sie muss den gleichen Namen wie die primäre Datenbank verwenden.  
  
    -   Sie muss auf einer Serverinstanz befinden, auf der ein sekundäres Replikat für die Verfügbarkeitsgruppe gehostet wird.  
  
 Sobald der Sicherungsauftrag auf der primären Datenbank ausgeführt wurde, deaktivieren Sie den Sicherungsauftrag, und sobald der Wiederherstellungsauftrag auf einer angegebenen sekundären Datenbank ausgeführt wurde, deaktivieren Sie den Wiederherstellungsauftrag.  
  
 Nachdem Sie alle sekundären Datenbanken für die Verfügbarkeitsgruppe erstellt haben, sofern Sie Sicherungen auf sekundären Replikaten ausführen möchten, müssen Sie die Voreinstellung zur automatisierten Sicherung der Verfügbarkeitsgruppe neu konfigurieren.  
  
 **Weitere Informationen:  **  
  
 [Konvertieren einer Protokollversandkonfiguration in eine Verfügbarkeitsgruppe](http://blogs.msdn.com/b/sqlAlways%20On/archive/2012/01/09/converting-a-logshipping-configuration-to-availability-group.aspx) (ein SQL Server-Blog)  
  
##  <a name="RelatedTasks"></a> Verwandte Aufgaben  
 **Protokollversand**  
  
-   [Aktualisieren des Protokollversands auf SQL Server 2016 &#40;Transact-SQL&#41;](../../../database-engine/log-shipping/upgrading-log-shipping-to-sql-server-2016-transact-sql.md)  
  
-   [Entfernen des Protokollversands &#40;SQL Server&#41;](../../../database-engine/log-shipping/remove-log-shipping-sql-server.md)  
  
 **AlwaysOn-Verfügbarkeitsgruppen**  
  
-   [Verwenden des Assistenten für Verfügbarkeitsgruppen &#40;SQL Server Management Studio&#41;](../../../database-engine/availability-groups/windows/use-the-availability-group-wizard-sql-server-management-studio.md)  
  
-   [Verwenden des Dialogfelds „Neue Verfügbarkeitsgruppe“ &#40;SQL Server Management Studio&#41;](../../../database-engine/availability-groups/windows/use-the-new-availability-group-dialog-box-sql-server-management-studio.md)  
  
-   [Erstellen einer Verfügbarkeitsgruppe &#40;Transact-SQL&#41;](../../../database-engine/availability-groups/windows/create-an-availability-group-transact-sql.md)  
  
-   [Erstellen einer Verfügbarkeitsgruppe &#40;SQL Server PowerShell&#41;](../../../database-engine/availability-groups/windows/create-an-availability-group-sql-server-powershell.md)  
  
-   [Verknüpfen einer sekundären Datenbank mit einer Verfügbarkeitsgruppe &#40;SQL Server&#41;](../../../database-engine/availability-groups/windows/join-a-secondary-database-to-an-availability-group-sql-server.md)  
  
-   [Konfigurieren der Sicherung auf Verfügbarkeitsreplikaten &#40;SQL Server&#41;](../../../database-engine/availability-groups/windows/configure-backup-on-availability-replicas-sql-server.md)  
  
##  <a name="RelatedContent"></a> Verwandte Inhalte  
  
-   **Blogs:**  
  
     [Konvertieren einer Protokollversandkonfiguration in eine Verfügbarkeitsgruppe](http://blogs.msdn.com/b/sqlAlways%20On/archive/2012/01/09/converting-a-logshipping-configuration-to-availability-group.aspx)  
  
     [Hinzufügen einer primären Datenbank für den Protokollversand und mindestens einer sekundären Datenbank zu einer vorhandenen Verfügbarkeitsgruppe](http://blogs.msdn.com/b/sqlAlways%20On/archive/2012/02/01/use-log-shipping-to-prepare-secondary-databases-for-an-existing-availability-group.aspx)  
  
     [SQL Server AlwaysOn-Teamblogs: Der offizielle SQL Server AlwaysOn-Teamblog](http://blogs.msdn.com/b/sqlAlways%20On/)  
  
     [CSS SQL Server-Technikblogs](http://blogs.msdn.com/b/psssql/)  
  
-   **Whitepaper:**  
  
     [Migrationshandbuch: Migrieren zu AlwaysOn-Verfügbarkeitsgruppen von vorherigen Bereitstellungen, in denen Datenbankspiegelung und Protokollversand kombiniert sind](http://msdn.microsoft.com/library/jj635217)  
  
     [Microsoft-Whitepapers für SQL Server 2012](http://msdn.microsoft.com/library/hh403491.aspx)  
  
     [Whitepapers des SQL Server-Kundenberatungsteams](http://sqlcat.com/)  
  
## Siehe auch  
 [Informationen zum Protokollversand &#40;SQL Server&#41;](../../../database-engine/log-shipping/about-log-shipping-sql-server.md)   
 [Übersicht über AlwaysOn-Verfügbarkeitsgruppen &#40;SQL Server&#41;](../../../database-engine/availability-groups/windows/overview-of-always-on-availability-groups-sql-server.md)   
 [Überwachen von Verfügbarkeitsgruppen &#40;SQL Server&#41;](../../../database-engine/availability-groups/windows/monitoring-of-availability-groups-sql-server.md)  
  
  