---
title: "&#220;bersicht &#252;ber PowerShell-Cmdlets f&#252;r Always On-Verf&#252;gbarkeitsgruppen (SQL Server) | Microsoft Docs"
ms.custom: ""
ms.date: "05/17/2016"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dbe-high-availability"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Verfügbarkeitsgruppen [SQL Server], PowerShell-Cmdlets"
  - "Verfügbarkeitsgruppen [SQL Server], Informationen"
  - "PowerShell [SQL Server], Cmdlets"
ms.assetid: b3fef0d5-b6d7-4386-a0f0-d06c165ad4de
caps.latest.revision: 36
author: "MikeRayMSFT"
ms.author: "mikeray"
manager: "jhubbard"
caps.handback.revision: 36
---
# &#220;bersicht &#252;ber PowerShell-Cmdlets f&#252;r Always On-Verf&#252;gbarkeitsgruppen (SQL Server)
[!INCLUDE[tsql-appliesto-ss2016-xxxx-xxxx-xxx_md](../../../includes/tsql-appliesto-ss2016-xxxx-xxxx-xxx-md.md)]

  [!INCLUDE[msCoName](../../../includes/msconame-md.md)] PowerShell ist eine speziell für die Systemverwaltung entwickelte taskbasierte Befehlszeilenshell und Skriptsprache. [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] stellt in [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] einen Satz von PowerShell-Cmdlets bereit, mit denen Sie Verfügbarkeitsgruppen, Verfügbarkeitsreplikate und Verfügbarkeitsdatenbanken bereitstellen, verwalten und überwachen können.  
  
> [!NOTE]  
>  Ein PowerShell-Cmdlet kann ausgeführt werden, indem eine Aktion erfolgreich initiiert wird. Dies zeigt nicht an, dass die vorgesehene Arbeit, z. B. das Failover einer Verfügbarkeitsgruppe, ausgeführt wurde. Wenn Sie Skripts für eine Aktionsfolge erstellen, müssen Sie möglicherweise den Status von Aktionen überprüfen und auf deren Ausführung warten.  
  
 Dieses Thema bietet eine Einführung in die Cmdlets für die folgenden Aufgaben:  
  
-   [Konfigurieren einer Serverinstanz für Always On-Verfügbarkeitsgruppen](#ConfiguringServerInstance)  
  
-   [Sichern und Wiederherstellen von Datenbanken und Transaktionsprotokollen](#BnRcmdlets)  
  
-   [Erstellen und Verwalten von Verfügbarkeitsgruppen](#DeployManageAGs)  
  
-   [Erstellen und Verwalten von Verfügbarkeitsgruppenlistenern](#AGlisteners)  
  
-   [Erstellen und Verwalten von Verfügbarkeitsreplikaten](#DeployManageARs)  
  
-   [Hinzufügen und Verwalten von Verfügbarkeitsdatenbanken](#DeployManageDbs)  
  
-   [Überwachen der Integrität von Verfügbarkeitsgruppen](#MonitorTblshtAGs)  
  
> [!NOTE]  
>  Eine Liste von Themen in der [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)]-Onlinedokumentation, die beschreiben, wie Cmdlets zum Ausführen von [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)]-Aufgaben verwendet werden, finden Sie im Abschnitt "Verwandte Aufgaben" von [Übersicht über Always On-Verfügbarkeitsgruppen &#40;SQL Server&#41;](../../../database-engine/availability-groups/windows/overview-of-always-on-availability-groups-sql-server.md).  
  
##  <a name="ConfiguringServerInstance"></a> Konfigurieren einer Serverinstanz für Always On-Verfügbarkeitsgruppen  
  
|Cmdlets|Beschreibung|Unterstützt auf|  
|-------------|-----------------|------------------|  
|**Disable-SqlAlways On**|Deaktiviert die [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)]-Funktion auf einer Serverinstanz.|Die Serverinstanz, die vom Parameter **Path**, **InputObject**oder **Name** angegeben wird. (Muss eine Edition von [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] sein, die [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] unterstützt.)|  
|**Enable-SqlAlways On**|Aktiviert [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] auf einer Instanz von [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)], die die [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)]-Funktion unterstützt. Informationen zur Unterstützung für [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] finden Sie unter [Voraussetzungen, Einschränkungen und Empfehlungen für Always On-Verfügbarkeitsgruppen &#40;SQL Server&#41;](../../../database-engine/availability-groups/windows/prereqs, restrictions, recommendations - always on availability.md).|Eine beliebige Edition von [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], die [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] unterstützt.|  
|**New-SqlHadrEndPoint**|Erstellt einen neuen Datenbankspiegelungs-Endpunkt auf einer Serverinstanz. Dieser Endpunkt ist zur Datenverschiebung zwischen primären und sekundären Datenbanken erforderlich.|Eine beliebige Instanz von [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]|  
|**Set-SqlHadrEndpoint**|Ändert die Eigenschaften eines vorhandenen Datenbankspiegelungs-Endpunkts, z. B. Namens-, Status- oder Authentifizierungseigenschaften.|Eine Serverinstanz, die [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] unterstützt und keinen Datenbankspiegelungs-Endpunkt aufweist|  
  
##  <a name="BnRcmdlets"></a> Sichern und Wiederherstellen von Datenbanken und Transaktionsprotokollen  
  
|Cmdlets|Beschreibung|Unterstützt auf|  
|-------------|-----------------|------------------|  
|**Backup-SqlDatabase**|Erstellt eine Daten- oder Protokollsicherung.|Eine beliebige Onlinedatenbank (für [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] eine Datenbank auf der Serverinstanz, die das primäre Replikat hostet)|  
|**Restore-SqlDatabase**|Stellt eine Sicherung wieder her.|Eine beliebige Instanz von [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] (für [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] eine Serverinstanz, die ein sekundäres Replikat hostet)<br /><br /> **\*\* Wichtig \*\*** Beim Vorbereiten einer sekundären Datenbank müssen Sie den **-NoRecovery**-Parameter in jedem **Restore-SqlDatabase**-Befehl verwenden.|  
  
 Informationen zur Verwendung dieser Cmdlets zum Vorbereiten einer sekundären Datenbank finden Sie unter [Manuelles Vorbereiten einer sekundären Datenbank auf eine Verfügbarkeitsgruppe &#40;SQL Server&#41;](../../../database-engine/availability-groups/windows/manually-prepare-a-secondary-database-for-an-availability-group-sql-server.md).  
  
##  <a name="DeployManageAGs"></a> Erstellen und Verwalten von Verfügbarkeitsgruppen  
  
|Cmdlets|Beschreibung|Unterstützt auf|  
|-------------|-----------------|------------------|  
|**New-SqlAvailabilityGroup**|Erstellt eine neue Verfügbarkeitsgruppe.|Serverinstanz zum Hosten des primären Replikats|  
|**Remove-SqlAvailabilityGroup**|Löscht eine Verfügbarkeitsgruppe.|HADR-fähige Serverinstanz|  
|**Set-SqlAvailabilityGroup**|Legt die Eigenschaften einer Verfügbarkeitsgruppe fest; schaltet eine Verfügbarkeitsgruppe online/offline|Serverinstanz, die das primäre Replikat hostet|  
|**Switch-SqlAvailabilityGroup**|Initiiert einen der folgenden Failovertypen:<br /><br /> Ein erzwungenes Failover einer Verfügbarkeitsgruppe (mit möglichem Datenverlust).<br /><br /> Ein manuelles Failover einer Verfügbarkeitsgruppe.|Serverinstanz, die das sekundäre Zielreplikat hostet|  
  
##  <a name="AGlisteners"></a> Erstellen und Verwalten von Verfügbarkeitsgruppenlistenern  
  
|Cmdlet|Beschreibung|Unterstützt auf|  
|------------|-----------------|------------------|  
|**New-SqlAvailabilityGroupListener**|Erstellt einen neuen Verfügbarkeitsgruppenlistener und fügt ihn einer vorhandenen Verfügbarkeitsgruppe hinzu.|Serverinstanz, die das primäre Replikat hostet|  
|**Set-SqlAvailabilityGroupListener**|Ändert die Porteinstellung eines vorhandenen Verfügbarkeitsgruppenlisteners.|Serverinstanz, die das primäre Replikat hostet|  
|**Add-SqlAvailabilityGroupListenerStaticIp**|Fügt der vorhandenen Konfiguration eines Verfügbarkeitsgruppenlisteners eine statische IP-Adresse hinzu. Die IP-Adresse kann eine IPv4-Adresse mit Subnetz oder eine IPv6-Adresse sein.|Serverinstanz, die das primäre Replikat hostet|  
  
##  <a name="DeployManageARs"></a> Erstellen und Verwalten von Verfügbarkeitsreplikaten  
  
|Cmdlets|Beschreibung|Unterstützt auf|  
|-------------|-----------------|------------------|  
|**New-SqlAvailabilityReplica**|Erstellt eine neue Verfügbarkeitsgruppe. Sie können mithilfe des **-AsTemplate**-Parameters für jedes neue Verfügbarkeitsreplikat ein Verfügbarkeitsreplikatobjekt im Arbeitsspeicher erstellen.|Serverinstanz, die das primäre Replikat hostet|  
|**Join-SqlAvailabilityGroup**|Verknüpft ein sekundäres Replikat mit der Verfügbarkeitsgruppe.|Serverinstanz, die ein sekundäres Replikat hostet|  
|**Remove-SqlAvailabilityReplica**|Lösch Sie ein Verfügbarkeitsreplikat.|Serverinstanz, die das primäre Replikat hostet|  
|**Set-SqlAvailabilityReplica**|Legt die Eigenschaften eines Verfügbarkeitsreplikats fest.|Serverinstanz, die das primäre Replikat hostet|  
  
##  <a name="DeployManageDbs"></a> Hinzufügen und Verwalten von Verfügbarkeitsdatenbanken  
  
|Cmdlets|Beschreibung|Unterstützt auf|  
|-------------|-----------------|------------------|  
|**Add-SqlAvailabilityDatabase**|Fügt auf dem primären Replikat einer Verfügbarkeitsgruppe eine Datenbank hinzu.<br /><br /> Verknüpft auf einem sekundären Replikat eine sekundäre Datenbank mit einer Verfügbarkeitsgruppe.|Eine beliebige Serverinstanz, die ein Verfügbarkeitsreplikat hostet (Verhalten unterscheidet sich für primäre und sekundäre Replikate)|  
|**Remove-SqlAvailabilityDatabase**|Entfernt auf dem primären Replikat die Datenbank aus der Verfügbarkeitsgruppe.<br /><br /> Entfernt auf einem sekundären Replikat die lokale sekundäre Datenbank aus dem lokalen sekundären Replikat.|Eine beliebige Serverinstanz, die ein Verfügbarkeitsreplikat hostet (Verhalten unterscheidet sich für primäre und sekundäre Replikate)|  
|**Resume-SqlAvailabilityDatabase**|Setzt die Datenverschiebung für eine angehaltene Verfügbarkeitsdatenbank fort.|Die Serverinstanz, auf der die Datenbank angehalten wurde.|  
|**Suspend-SqlAvailabilityDatabase**|Hält die Datenverschiebung für eine Verfügbarkeitsdatenbank an.|Eine beliebige Serverinstanz, die ein Verfügbarkeitsreplikat hostet.|  
  
##  <a name="MonitorTblshtAGs"></a> Überwachen der Integrität der Verfügbarkeitsgruppe  
 Mit den folgenden [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]-Cmdlets können Sie die Integrität einer Verfügbarkeitsgruppe und ihrer Replikate und Datenbanken überwachen.  
  
> [!IMPORTANT]  
>  Sie müssen über CONNECT-, VIEW SERVER STATE- und VIEW ANY DEFINITION-Berechtigungen verfügen, um diese Cmdlets auszuführen.  
  
|Cmdlet|Beschreibung|Unterstützt auf|  
|------------|-----------------|------------------|  
|**Test-SqlAvailabilityGroup**|Bewertet die Integrität einer Verfügbarkeitsgruppe durch die Auswertung der Richtlinien der richtlinienbasierten SQL Server-Verwaltung.|Eine beliebige Serverinstanz, die ein Verfügbarkeitsreplikat hostet.*|  
|**Test-SqlAvailabilityReplica**|Bewertet die Integrität von Verfügbarkeitsreplikaten durch die Auswertung der Richtlinien der richtlinienbasierten SQL Server-Verwaltung.|Eine beliebige Serverinstanz, die ein Verfügbarkeitsreplikat hostet.*|  
|**Test-SqlDatabaseReplicaState**|Bewertet die Integrität einer Verfügbarkeitsdatenbank für alle hinzugefügten Verfügbarkeitsreplikate durch die Auswertung der Richtlinien der richtlinienbasierten SQL Server-Verwaltung.|Eine beliebige Serverinstanz, die ein Verfügbarkeitsreplikat hostet.*|  
  
 *Verwenden Sie zum Anzeigen von Informationen zu allen Verfügbarkeitsreplikaten in einer Verfügbarkeitsgruppe die Serverinstanz, die das primäre Replikat hostet.  
  
 Weitere Informationen finden Sie unter [Verwenden von Always On-Richtlinien zum Anzeigen des Zustands einer Verfügbarkeitsgruppe &#40;SQL Server&#41;](../../../database-engine/availability-groups/windows/use-always-on-policies-to-view-the-health-of-an-availability-group-sql-server.md).  
  
## Siehe auch  
 [Übersicht über Always On-Verfügbarkeitsgruppen &#40;SQL Server&#41;](../../../database-engine/availability-groups/windows/overview-of-always-on-availability-groups-sql-server.md)   
 [Aufrufen der SQL Server PowerShell-Hilfe](../../../relational-databases/scripting/get-help-sql-server-powershell.md)  
  
  