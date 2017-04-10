---
title: "Konfigurieren der flexiblen Failoverrichtlinie zum Steuern der Bedingungen f&#252;r ein automatisches Failover (AlwaysOn-Verf&#252;gbarkeitsgruppen) | Microsoft Docs"
ms.custom: ""
ms.date: "03/29/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dbe-high-availability"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Verfügbarkeitsgruppen [SQL Server], flexible Failoverrichtlinie"
  - "Verfügbarkeitsgruppen [SQL Server], Failover"
  - "Failover [SQL Server], AlwaysOn-Verfügbarkeitsgruppen"
ms.assetid: 1ed564b4-9835-4245-ae35-9ba67419a4ce
caps.latest.revision: 24
ms.author: "mikeray"
manager: "jhubbard"
---
# Konfigurieren der flexiblen Failoverrichtlinie zum Steuern der Bedingungen f&#252;r ein automatisches Failover (AlwaysOn-Verf&#252;gbarkeitsgruppen)
[!INCLUDE[tsql-appliesto-ss2016-xxxx-xxxx-xxx_md](../../../includes/tsql-appliesto-ss2016-xxxx-xxxx-xxx-md.md)]

  In diesem Thema wird beschrieben, wie die flexible Failoverrichtlinie für eine AlwaysOn-Verfügbarkeitsgruppe mithilfe von [!INCLUDE[tsql](../../../includes/tsql-md.md)] oder PowerShell in [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] konfiguriert wird. Eine flexible Failoverrichtlinie ermöglicht eine präzise Kontrolle über die Bedingungen, die ein automatisches Failover für eine Verfügbarkeitsgruppe verursachen. Durch eine Änderung der Fehlerbedingungen, die ein automatisches Failover und die Häufigkeit von Integritätsprüfungen auslösen, können Sie die Wahrscheinlichkeit für ein automatisches Failover erhöhen oder verringern, um das SLA für hohe Verfügbarkeit zu unterstützen.  
  
-   **Vorbereitungen:**  
  
     [Einschränkungen beim automatischen Failover](#Limitations)  
  
     [Erforderliche Komponenten](#Prerequisites)  
  
     [Sicherheit](#Security)  
  
-   **Konfigurieren der flexiblen Failoverrichtlinie mit:**  
  
     [Transact-SQL](#TsqlProcedure)  
  
     [PowerShell](#PowerShellProcedure)  
  
    > [!NOTE]  
    >  Die flexible Failoverrichtlinie für eine Verfügbarkeitsgruppe kann nicht mit [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] konfiguriert werden.  
  
##  <a name="BeforeYouBegin"></a> Vorbereitungen  
  
###  <a name="Limitations"></a> Einschränkungen beim automatischen Failover  
  
-   Damit ein automatisches Failover ausgeführt werden kann, müssen das aktuelle primäre Replikat und ein sekundäres Replikat für den Verfügbarkeitsmodus für synchrone Commits und automatischem Failover konfiguriert und das sekundäre Replikat mit dem primären Replikat synchronisiert sein.  
  
-   Für das automatische Failover werden nur drei Replikate unterstützt.  
  
-   Wenn eine Verfügbarkeitsgruppe den Schwellenwert für WSFC-Fehler überschreitet, versucht der WSFC-Cluster nicht, ein automatisches Failover für die Verfügbarkeitsgruppe auszuführen. Außerdem verbleibt die WSFC-Ressourcengruppe der Verfügbarkeitsgruppe so lange in einem fehlerhaften Zustand, bis der Clusteradministrator die fehlerhafte Gruppe manuell online schaltet oder bis der Datenbankadministrator ein manuelles Failover der Verfügbarkeitsgruppe ausführt. Der *WSFC-Fehlerschwellenwert* ist als maximale Anzahl von Fehlern definiert, die während eines bestimmten Zeitraums für die Verfügbarkeitsgruppe unterstützt werden. Der Standardzeitraum beträgt sechs Stunden, und der Standardwert für die maximale Anzahl von Fehlern während dieses Zeitraums entspricht *n*-1, wobei *n* für die Anzahl der WSFC-Knoten steht. Um den Fehlerschwellenwert für eine angegebene Verfügbarkeitsgruppe zu ändern, verwenden Sie die WSFC Failover Manager Console.  
  
###  <a name="Prerequisites"></a> Erforderliche Komponenten  
  
-   Sie müssen mit der Serverinstanz verbunden sein, die das primäre Replikat hostet.  
  
###  <a name="Security"></a> Sicherheit  
  
####  <a name="Permissions"></a> Berechtigungen  
  
|Task|Berechtigungen|  
|----------|-----------------|  
|Konfigurieren der flexiblen Failoverrichtlinie für eine neue Verfügbarkeitsgruppe|Erfordert die Mitgliedschaft in der festen Serverrolle **sysadmin** und die CREATE AVAILABILITY GROUP-Serverberechtigung, ALTER ANY AVAILABILITY GROUP-Berechtigung oder CONTROL SERVER-Berechtigung.|  
|Ändern der Richtlinie einer vorhandenen Verfügbarkeitsgruppe|Erfordert die ALTER AVAILABILITY GROUP-Berechtigung für die Verfügbarkeitsgruppe, die CONTROL AVAILABILITY GROUP-Berechtigung, die ALTER ANY AVAILABILITY GROUP-Berechtigung oder die CONTROL SERVER-Berechtigung.|  
  
##  <a name="TsqlProcedure"></a> Verwenden von Transact-SQL  
 **So konfigurieren Sie die flexible Failoverrichtlinie**  
  
1.  Stellen Sie eine Verbindung mit der Serverinstanz her, die das primäre Replikat hostet.  
  
2.  Für eine neue Verfügbarkeitsgruppe verwenden Sie die [-Anweisung](../../../t-sql/statements/create-availability-group-transact-sql.md)[!INCLUDE[tsql](../../../includes/tsql-md.md)] . Verwenden Sie zum Ändern einer vorhandenen Verfügbarkeitsgruppe die [ALTER AVAILABILITY GROUP](../../../t-sql/statements/alter-availability-group-transact-sql.md)[!INCLUDE[tsql](../../../includes/tsql-md.md)]-Anweisung.  
  
    -   Um die Failover-Bedingungsebene festzulegen, verwenden Sie die Option FAILURE_CONDITION_LEVEL = *n*, wobei *n* für eine ganze Zahl zwischen 1 und 5 steht.  
  
         Beispielsweise wird mit der folgenden [!INCLUDE[tsql](../../../includes/tsql-md.md)]-Anweisung die Fehlerbedingungsebene der vorhandenen Verfügbarkeitsgruppe `AG1` in Ebene 1 geändert:  
  
        ```  
  
        ALTER AVAILABILITY GROUP AG1 SET (FAILURE_CONDITION_LEVEL = 1);  
        ```  
  
         Diese ganzzahligen Werte stehen in folgender Beziehung zu den Fehlerbedingungsebenen:  
  
        |[!INCLUDE[tsql](../../../includes/tsql-md.md)] Wert|Ebene|Automatisches Failover wird initiiert, wenn...|  
        |------------------------------|-----------|-------------------------------------------|  
        |1|1 (eins)|der Server ausfällt. Der SQL Server-Dienst wird aufgrund eines Failovers oder Neustarts beendet.|  
        |2|2 (zwei)|der Server nicht reagiert. Der Wert der Bedingungsebene wird unterschritten, der SQL Server-Dienst ist mit dem Cluster verbunden, und der Schwellenwert für das Timeout der Integritätsprüfung wird überschritten, oder das aktuelle primäre Replikat weist einen fehlerhaften Status auf.|  
        |3|3 (drei)|ein kritischer Serverfehler auftritt. Der Wert der Bedingungsebene wird unterschritten, oder es tritt ein interner kritischer Serverfehler auf.<br /><br /> Dies ist der Standardebene.|  
        |4|4 (vier)|ein mittelschwerer Serverfehler auftritt. Der Wert der Bedingungsebene wird unterschritten, oder es tritt ein mittelschwerer Serverfehler auf.|  
        |5|5 (fünf)|eine qualifizierte Fehlerbedingung auftritt. Der Wert der Bedingungsebene wird unterschritten, oder es tritt eine qualifizierte Fehlerbedingung auf.|  
  
         Weitere Informationen zu den Failover-Bedingungsebenen finden Sie unter [Flexible Failoverrichtlinie für automatisches Failover einer Verfügbarkeitsgruppe &#40;SQL Server&#41;](../../../database-engine/availability-groups/windows/flexible automatic failover policy - availability group.md).  
  
    -   Um den Schwellenwert für das Timeout der Integritätsprüfung zu konfigurieren, verwenden Sie die Option HEALTH_CHECK_TIMEOUT = *n*, wobei *n* für eine ganze Zahl zwischen 15000 Millisekunden (15 Sekunden) und 4294967295 Millisekunden steht. Der Standardwert ist 30.000 Millisekunden (oder 30 Sekunden).  
  
         Mit der folgenden [!INCLUDE[tsql](../../../includes/tsql-md.md)]-Anweisung wird z. B. der Schwellenwert für das Timeout der Integritätsprüfung einer vorhandenen Verfügbarkeitsgruppe mit dem Namen `AG1` in 60.000 Millisekunden (eine Minute) geändert.  
  
        ```  
  
        ALTER AVAILABILITY GROUP AG1 SET (HEALTH_CHECK_TIMEOUT = 60000);  
        ```  
  
##  <a name="PowerShellProcedure"></a> PowerShell  
 **So konfigurieren Sie die flexible Failoverrichtlinie**  
  
1.  Legen Sie mit **cd** die Serverinstanz als Standard fest, auf der das primäre Replikat gehostet wird.  
  
2.  Verwenden Sie beim Hinzufügen eines Verfügbarkeitsreplikats zu einer Verfügbarkeitsgruppe das Cmdlet **New-SqlAvailabilityGroup**. Verwenden Sie beim Ändern eines vorhandenen Verfügbarkeitsreplikats das Cmdlet **Set-SqlAvailabilityGroup**.  
  
    -   Um die Failover-Bedingungsebene festzulegen, verwenden Sie den **FailureConditionLevel** *level*-Parameter, wobei *level* für einen der folgenden Werte steht:  
  
        |Wert|Ebene|Automatisches Failover wird initiiert, wenn...|  
        |-----------|-----------|-------------------------------------------|  
        |**OnServerDown**|1 (eins)|der Server ausfällt. Der SQL Server-Dienst wird aufgrund eines Failovers oder Neustarts beendet.|  
        |**OnServerUnresponsive**|2 (zwei)|der Server nicht reagiert. Der Wert der Bedingungsebene wird unterschritten, der SQL Server-Dienst ist mit dem Cluster verbunden, und der Schwellenwert für das Timeout der Integritätsprüfung wird überschritten, oder das aktuelle primäre Replikat weist einen fehlerhaften Status auf.|  
        |**OnCriticalServerError**|3 (drei)|ein kritischer Serverfehler auftritt. Der Wert der Bedingungsebene wird unterschritten, oder es tritt ein interner kritischer Serverfehler auf.<br /><br /> Dies ist der Standardebene.|  
        |**OnModerateServerError**|4 (vier)|ein mittelschwerer Serverfehler auftritt. Der Wert der Bedingungsebene wird unterschritten, oder es tritt ein mittelschwerer Serverfehler auf.|  
        |**OnAnyQualifiedFailureConditions**|5 (fünf)|eine qualifizierte Fehlerbedingung auftritt. Der Wert der Bedingungsebene wird unterschritten, oder es tritt eine qualifizierte Fehlerbedingung auf.|  
  
         Weitere Informationen zu den Failover-Bedingungsebenen finden Sie unter [Flexible Failoverrichtlinie für automatisches Failover einer Verfügbarkeitsgruppe &#40;SQL Server&#41;](../../../database-engine/availability-groups/windows/flexible automatic failover policy - availability group.md).  
  
         Beispielsweise wird mit dem folgenden Befehl die Fehlerbedingungsebene der vorhandenen Verfügbarkeitsgruppe `AG1` in Ebene 1 geändert.  
  
        ```  
        Set-SqlAvailabilityGroup `   
        -Path SQLSERVER:\Sql\PrimaryServer\InstanceName\AvailabilityGroups\MyAg `   
        -FailureConditionLevel OnServerDown  
        ```  
  
    -   Um den Schwellenwert für das Timeout der Integritätsprüfung festzulegen, verwenden Sie den **HealthCheckTimeout***n*-Parameter, wobei *n* für eine ganze Zahl zwischen 15000 Millisekunden (15 Sekunden) und 4294967295 Millisekunden steht. Der Standardwert ist 30000 Millisekunden (oder 30 Sekunden).  
  
         Mit dem folgenden Befehl wird z. B. der Schwellenwert für das Timeout der Integritätsprüfung der vorhandenen Verfügbarkeitsgruppe `AG1` in 120.000 Millisekunden (zwei Minuten) geändert.  
  
        ```  
        Set-SqlAvailabilityGroup `   
        -Path SQLSERVER:\Sql\PrimaryServer\InstanceName\AvailabilityGroups\MyAG `   
        -HealthCheckTimeout 120000  
        ```  
  
> [!NOTE]  
>  Um die Syntax eines Cmdlets anzuzeigen, verwenden Sie das Cmdlet **Get-Help** in der [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]-PowerShell-Umgebung. Weitere Informationen finden Sie unter [Get Help SQL Server PowerShell](../../../relational-databases/scripting/get-help-sql-server-powershell.md).  
  
 **Einrichten und Verwenden des SQL Server PowerShell-Anbieters**  
  
-   [SQL Server PowerShell-Anbieter](../../../relational-databases/scripting/sql-server-powershell-provider.md)  
  
-   [Aufrufen der SQL Server PowerShell-Hilfe](../../../relational-databases/scripting/get-help-sql-server-powershell.md)  
  
## Siehe auch  
 [Übersicht über AlwaysOn-Verfügbarkeitsgruppen &#40;SQL Server&#41;](../../../database-engine/availability-groups/windows/overview-of-always-on-availability-groups-sql-server.md)   
 [Verfügbarkeitsmodi &#40;AlwaysOn-Verfügbarkeitsgruppen&#41;](../../../database-engine/availability-groups/windows/availability-modes-always-on-availability-groups.md)   
 [Failover und Failovermodi &#40;AlwaysOn-Verfügbarkeitsgruppen&#41;](../../../database-engine/availability-groups/windows/failover-and-failover-modes-always-on-availability-groups.md)   
 [Windows Server-Failoverclustering &#40;WSFC&#41; mit SQL Server](../../../sql-server/failover-clusters/windows/windows-server-failover-clustering-wsfc-with-sql-server.md)   
 [Failoverrichtlinie für Failoverclusterinstanzen](../../../sql-server/failover-clusters/windows/failover-policy-for-failover-cluster-instances.md)   
 [sp_server_diagnostics &#40;Transact-SQL&#41;](../../../relational-databases/system-stored-procedures/sp-server-diagnostics-transact-sql.md)  
  
  