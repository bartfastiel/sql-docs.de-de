---
title: Konfigurieren der Serverkonfigurationsoption „Umstellungsjahr für Angaben mit zwei Ziffern“ | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
helpviewer_keywords:
- two digit year cutoff option
- four-digit years [SQL Server]
ms.assetid: d94e81b6-f2e6-47ef-b497-ec3d827a1646
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: da1bf028421855ee08584abae78bd66f75058e6e
ms.sourcegitcommit: 04dd0620202287869b23cc2fde998a18d3200c66
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/30/2018
ms.locfileid: "52641451"
---
# <a name="configure-the-two-digit-year-cutoff-server-configuration-option"></a>Konfigurieren der Serverkonfigurationsoption Umstellungsjahr für Angaben mit zwei Ziffern
  In diesem Thema wird beschrieben, wie die Serverkonfigurationsoption **Umstellungsjahr für Angaben mit zwei Ziffern** in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] mithilfe von [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] oder [!INCLUDE[tsql](../../includes/tsql-md.md)]konfiguriert wird. Mithilfe der Option **Umstellungsjahr für Angaben mit zwei Ziffern** können Sie eine ganze Zahl zwischen 1753 und 9999 angeben, die das Umstellungsjahr für das Interpretieren zweistelliger Jahre als vierstellige Jahre darstellt. Der Standardzeitraum für [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ist 1950 bis 2049, wobei 2049 das Umstellungsjahr ist. Dies bedeutet, dass [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] eine zweistellige Jahreszahl von 49 als 2049, eine zweistellige Jahreszahl von 50 als 1950 und eine zweistellige Jahreszahl von 99 als 1999 interpretiert. Übernehmen Sie bei der Einstellung den Standardwert, um Abwärtskompatibilität zu gewährleisten.  
  
 **In diesem Thema**  
  
-   **Vorbereitungen:**  
  
     [Empfehlungen](#Recommendations)  
  
     [Sicherheit](#Security)  
  
-   **So konfigurieren Sie die Option Umstellungsjahr für Angaben mit zwei Ziffern mit:**  
  
     [SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
-   **Nachverfolgung:**  [Nach dem Konfigurieren der Option Umstellungsjahr für Angaben mit zwei Ziffern](#FollowUp)  
  
##  <a name="BeforeYouBegin"></a> Vorbereitungen  
  
###  <a name="Recommendations"></a> Empfehlungen  
  
-   Diese Option ist eine erweiterte Option und sollte ausschließlich von einem erfahrenen Datenbankadministrator oder einem zertifizierten [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Techniker geändert werden.  
  
-   OLE-Automatisierungsobjekte verwenden 2030 als Umstellungsjahr für Angaben mit zwei Ziffern. Mithilfe der Option **Umstellungsjahr für Angaben mit zwei Ziffern** können Sie Konsistenz zwischen den Datenwerten von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] und Clientanwendungen herstellen. Wenn Sie die Mehrdeutigkeit von Daten vermeiden möchten, sollten Sie allerdings vierstellige Jahre verwenden.  
  
###  <a name="Security"></a> Sicherheit  
  
####  <a name="Permissions"></a> Berechtigungen  
 Die Ausführungsberechtigungen für **sp_configure** ohne Parameter oder nur mit dem ersten Parameter werden standardmäßig allen Benutzern erteilt. Zum Ausführen von **sp_configure** mit beiden Parametern zum Ändern einer Konfigurationsoption oder zum Ausführen der RECONFIGURE-Anweisung muss einem Benutzer die ALTER SETTINGS-Berechtigung auf Serverebene erteilt worden sein. Die ALTER SETTINGS-Berechtigung ist in den festen Serverrollen **sysadmin** und **serveradmin** eingeschlossen.  
  
##  <a name="SSMSProcedure"></a> Verwendung von SQL Server Management Studio  
  
#### <a name="to-configure-the-two-digit-year-cutoff-option"></a>So konfigurieren Sie die Option Umstellungsjahr für Angaben mit zwei Ziffern  
  
1.  Klicken Sie im Objekt-Explorer mit der rechten Maustaste auf einen Server, und wählen Sie **Eigenschaften** aus.  
  
2.  Klicken Sie auf den **Sonstige Servereinstellungen** -Knoten.  
  
3.  Geben Sie unter **Unterstützung zweistelliger Jahresangaben**im Feld **Bei Eingabe einer zweistelligen Jahresangabe** **soll diese interpretiert werden als Jahr zwischen** einen Wert ein, der das Endjahr des Zeitraums angibt, oder wählen Sie einen Wert aus.  
  
##  <a name="TsqlProcedure"></a> Verwenden von Transact-SQL  
  
#### <a name="to-configure-the-two-digit-year-cutoff-option"></a>So konfigurieren Sie die Option Umstellungsjahr für Angaben mit zwei Ziffern  
  
1.  Stellen Sie eine Verbindung mit dem [!INCLUDE[ssDE](../../includes/ssde-md.md)]her.  
  
2.  Klicken Sie in der Standardleiste auf **Neue Abfrage**.  
  
3.  Kopieren Sie das folgende Beispiel, fügen Sie es in das Abfragefenster ein, und klicken Sie auf **Ausführen**. In diesem Beispiel wird gezeigt, wie [sp_configure](/sql/relational-databases/system-stored-procedures/sp-configure-transact-sql) verwendet wird, um den Wert der Option `two digit year cutoff` auf `2030`festzulegen.  
  
```tsql  
USE AdventureWorks2012 ;  
GO  
EXEC sp_configure 'show advanced options', 1;  
GO  
RECONFIGURE ;  
GO  
EXEC sp_configure 'two digit year cutoff', 2030 ;  
GO  
RECONFIGURE;  
GO  
  
```  
  
 Weitere Informationen finden Sie unter [Serverkonfigurationsoptionen &#40;SQL Server&#41;](server-configuration-options-sql-server.md)angezeigt oder konfiguriert wird.  
  
##  <a name="FollowUp"></a> Zur Nachverfolgung: Nach dem Konfigurieren der Option Umstellungsjahr für Angaben mit zwei Ziffern  
 Die Einstellung tritt ohne Neustarten des Servers sofort in Kraft.  
  
## <a name="see-also"></a>Siehe auch  
 [Serverkonfigurationsoptionen &#40;SQL Server&#41;](server-configuration-options-sql-server.md)   
 [sp_configure &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-configure-transact-sql)   
 [RECONFIGURE &#40;Transact-SQL&#41;](/sql/t-sql/language-elements/reconfigure-transact-sql)  
  
  
