---
title: "Audit Add Member to DB Role (Ereignisklasse) | Microsoft Docs"
ms.custom: ""
ms.date: "03/14/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "database-engine"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Audit Add Member to DB Role-Ereignisklasse"
ms.assetid: a5ac46b6-765b-4424-b6c7-4d5a1b898d65
caps.latest.revision: 31
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 31
---
# Audit Add Member to DB Role (Ereignisklasse)
  Die **Audit Add Member to DB Role** -Ereignisklasse tritt auf, wenn einer Datenbankrolle ein Anmeldename hinzugefügt oder aus ihr entfernt wird. Diese Ereignisklasse wird mit den gespeicherten Prozeduren **sp_addrolemember**, **sp_changegroup** und **sp_droprolemember** verwendet.  
  
## Datenspalten der Audit Add Member to DB Role-Ereignisklasse  
  
|Datenspaltenname|Datentyp|Beschreibung|Column ID|Filterbar|  
|----------------------|---------------|-----------------|---------------|----------------|  
|**ApplicationName**|**nvarchar**|Der Name der Clientanwendung, die die Verbindung mit einer Instanz von [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]hergestellt hat. Diese Spalte wird mit den Werten aufgefüllt, die von der Anwendung übergeben werden, und nicht mit dem angezeigten Namen des Programms.|10|ja|  
|**ClientProcessID**|**int**|Die ID, die der Hostcomputer dem Prozess zuweist, in dem die Clientanwendung ausgeführt wird. Diese Datenspalte wird aufgefüllt, wenn der Client die Clientprozess-ID angibt.|9|ja|  
|**DatabaseID**|**int**|Die ID der Datenbank, die durch die USE *database* -Anweisung angegeben wurde, bzw. die ID der Standarddatenbank, wenn für eine bestimmte Instanz keine USE *database* -Anweisung ausgegeben wurde. [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] zeigt den Namen der Datenbank an, wenn die **ServerName** -Datenspalte in der Ablaufverfolgung aufgezeichnet wird und der Server verfügbar ist. Der Wert für eine Datenbank kann mithilfe der DB_ID-Funktion ermittelt werden.|3|Ja|  
|**DatabaseName**|**nvarchar**|Name der Datenbank, in der die Rollenmitgliedschaft geändert wird.|35|Ja|  
|**DBUserName**|**nvarchar**|Der Benutzername des Ausstellers in der Datenbank.|40|Ja|  
|**EventClass**|**int**|Ereignistyp = 110.|27|Nein|  
|**EventSequence**|**int**|Sequenz eines bestimmten Ereignisses innerhalb der Anforderung.|51|Nein|  
|**EventSubClass**|**int**|Der Typ der Ereignisunterklasse.<br /><br /> 1 = Hinzufügen<br /><br /> 2 = Löschen<br /><br /> 3 = Gruppe ändern|21|Ja|  
|**HostName**|**nvarchar**|Der Name des Computers, auf dem der Client ausgeführt wird. Diese Datenspalte wird aufgefüllt, wenn der Hostname vom Client bereitgestellt wird. Der Hostname kann mithilfe der HOST_NAME-Funktion bestimmt werden.|8|Ja|  
|**IsSystem**|**int**|Gibt an, ob das Ereignis bei einem Systemprozess oder einem Benutzerprozess aufgetreten ist. 1 = System, 0 = Benutzer.|60|Ja|  
|**LoginName**|**nvarchar**|Anmeldename des Benutzers (Anmeldung der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Sicherheit oder [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows-Anmeldeinformationen im Format DOMAIN\username).|11|Ja|  
|**LoginSid**|**image**|Sicherheits-ID (SID) des angemeldeten Benutzers. Diese Informationen finden Sie in der **sys.server_principals**-Katalogsicht. Die SID ist für jede Anmeldung beim Server eindeutig.|41|Ja|  
|**NTDomainName**|**nvarchar**|Windows-Domäne, zu der der Benutzer gehört.|7|ja|  
|**NTUserName**|**nvarchar**|Windows-Benutzername.|6|Ja|  
|**ObjectName**|**nvarchar**|Name des Objekts, auf das verwiesen wird|34|Ja|  
|**ObjectType**|**int**|Der Wert, der den Typ des am Ereignis beteiligten Objekts darstellt. Dieser Wert entspricht der type-Spalte in der **sys.objects** -Katalogsicht. Weitere Werte finden Sie unter [ObjectType (Spalte für Ablaufverfolgungsereignisse)](../../relational-databases/event-classes/objecttype-trace-event-column.md).|28|Ja|  
|**OwnerName**|**nvarchar**|Datenbank-Benutzername des Objektbesitzers.|37|Ja|  
|**RequestID**|**int**|Die ID der Anforderung, die die Anweisung enthält.|49|ja|  
|**RoleName**|**nvarchar**|Name einer Anwendungsrolle, die aktiviert wird.|38|Ja|  
|**ServerName**|**nvarchar**|Name der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Instanz, für die eine Ablaufverfolgung ausgeführt wird.|26|Nein|  
|**SessionLoginName**|**Nvarchar**|Der Anmeldename des Benutzers, der die Sitzung gestartet hat. Wenn Sie z. B. mit Login1 eine Verbindung zu [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] herstellen und mit Login2 eine Anweisung ausführen, zeigt **SessionLoginName** Login1 an, und **LoginName** zeigt Login2 an. Diese Spalte zeigt sowohl den [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] - als auch den Windows-Anmeldenamen an.|64|Ja|  
|**SPID**|**int**|Die ID der Sitzung, in der das Ereignis aufgetreten ist.|12|ja|  
|**StartTime**|**datetime**|Zeitpunkt, zu dem das Ereignis begonnen hat (falls vorhanden).|14|Ja|  
|**Success**|**int**|1 = Erfolg 0 = Fehler. Der Wert 1 deutet beispielsweise auf eine erfolgreiche Überprüfung der Berechtigungen hin, während die Überprüfung bei dem Wert 0 fehlgeschlagen ist.|23|ja|  
|**TargetUserName**|**nvarchar**|Name des Benutzers, dessen Rollenmitgliedschaft geändert wird.|39|ja|  
|**TransactionID**|**bigint**|Die vom System zugewiesene ID der Transaktion.|4|Ja|  
|**XactSequence**|**bigint**|Token zur Beschreibung der aktuellen Transaktion.|50|ja|  
  
## Siehe auch  
 [Erweiterte Ereignisse](../../relational-databases/extended-events/extended-events.md)   
 [sp_trace_setevent &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-trace-setevent-transact-sql.md)   
 [sp_addrolemember &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-addrolemember-transact-sql.md)   
 [sp_droprolemember &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-droprolemember-transact-sql.md)  
  
  