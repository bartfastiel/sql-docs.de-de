---
title: Konfigurieren von Dienstkonten (Analysis Services) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
ms.topic: conceptual
helpviewer_keywords:
- security [Analysis Services], logon accounts
- logon accounts [Analysis Services]
- accounts [Analysis Services]
- logon accounts [Analysis Services], about logon accounts
ms.assetid: b481bd51-e077-42f6-8598-ce08c1a38716
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 7b6be38afc2c95d6cfce80bcefa6ad0b3ab954fe
ms.sourcegitcommit: 7aa6beaaf64daf01b0e98e6c63cc22906a77ed04
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/09/2019
ms.locfileid: "54125500"
---
# <a name="configure-service-accounts-analysis-services"></a>Konfigurieren von Dienstkonten (Analysis Services)
  Unter [Konfigurieren von Windows-Dienstkonten und -Berechtigungen](../../database-engine/configure-windows/configure-windows-service-accounts-and-permissions.md)wird die Kontobereitstellung für das gesamte Produkt beschrieben. Das Thema enthält umfassende Informationen zu Dienstkonten für alle [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Dienste, einschließlich [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]. Dort erfahren Sie alles über gültige Kontotypen, beim Setup zugewiesene Windows-Berechtigungen, Dateisystemberechtigungen, Registrierungsberechtigungen und vieles mehr.  
  
 Dieses Thema enthält ergänzende Informationen zu [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)], einschließlich erforderlichen zusätzlichen Berechtigungen für tabellarische und gruppierte Installationen. Außerdem werden Berechtigungen behandelt, die zur Unterstützung von Servervorgängen erforderlich sind. Sie können beispielsweise Verarbeitungs- und Abfrageoperationen so konfigurieren, dass sie über das Dienstkonto ausgeführt werden. In diesem Fall müssen Sie zusätzliche Berechtigungen gewähren.  
  
-   [Analysis Services zugewiesene Windows-Berechtigungen](#bkmk_winpriv)  
  
-   [Analysis Services zugewiesene Dateisystemberechtigungen](#bkmk_FilePermissions)  
  
-   [Erteilen zusätzlicher Berechtigungen für bestimmte Servervorgänge](#bkmk_tasks)  
  
 Ein zusätzlicher Konfigurationsschritt, der hier nicht dokumentiert ist, besteht darin, einen Dienstprinzipalnamen (SPN) für die Instanz und das Dienstkonto von [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] zu registrieren. Dieser Schritt ermöglicht Pass-Through-Authentifizierung von Clientanwendungen zu Back-End-Datenquellen in Double-Hop-Szenarien. Dieser Schritt kann bei Diensten verwendet werden, die für eingeschränkte Kerberos-Delegierung konfiguriert sind. Weitere Anweisungen finden Sie unter [Configure Analysis Services for Kerberos constrained delegation](configure-analysis-services-for-kerberos-constrained-delegation.md) .  
  
## <a name="logon-account-recommendations"></a>Kontoempfehlungen für die Anmeldung  
 In einem Failovercluster sollten alle Instanzen von Analysis Services so konfiguriert werden, dass sie ein Windows-Domänenbenutzerkonto verwenden. Weisen Sie dasselbe Konto für alle Instanzen zu. Weitere Informationen finden Sie unter [Clustern von Analysis Services](https://msdn.microsoft.com/library/dn736073.aspx) .  
  
 Eigenständige Instanzen sollten das virtuelle Standardkonto verwenden: **NT Service\MSSQLServerOLAPService** für die Standardinstanz oder **NT Service\MSOLAP$**_Instanzname_ für eine benannte Instanz. Diese Empfehlung gilt für Analysis Services-Instanzen in allen Servermodi, Windows Server 2008 R2 und höher für das Betriebssystem und SQL Server 2012 und höher für Analysis Services vorausgesetzt.  
  
## <a name="granting-permissions-to-analysis-services"></a>Erteilen von Berechtigungen für Analysis Services  
 Dieser Abschnitt erläutert die Berechtigungen, die Analysis Services für lokale, interne Vorgänge wie das Starten der ausführbaren Datei, das Lesen der Konfigurationsdatei und das Laden von Datenbanken aus dem Datenverzeichnis benötigt. Wenn Sie stattdessen Anleitungen zum Festlegen von Berechtigungen für den Zugriff auf externe Daten und Interoperabilität mit anderen Diensten und Anwendungen suchen, finden Sie weitere Informationen unter [Erteilen zusätzlicher Berechtigungen für bestimmte Servervorgänge](#bkmk_tasks) weiter unten in diesem Thema.  
  
 Für die internen Vorgänge ist der Berechtigungsinhaber in Analysis Services nicht das Anmeldekonto, sondern eine lokale Windows-Sicherheitsgruppe, die bei der Einrichtung erstellt wird und die Pro-Dienst-SID enthält. Das Zuweisen von Berechtigungen für die Sicherheitsgruppe deckt sich mit früheren Versionen von Analysis Services. Darüber hinaus können sich Anmeldekonten mit der Zeit ändern, aber die Pro-Dienst-SID und die lokale Sicherheitsgruppe bleiben für die Lebensdauer der Serverinstallation gleich. Für Analysis Services macht dies die Sicherheitsgruppe statt des Anmeldekontos die bessere Wahl für die Aufnahme von Berechtigungen. Wenn Sie manuell Berechtigungen für die Dienstinstanz erteilen, egal ob Dateisystemberechtigungen oder Windows-Berechtigungen, erteilen Sie der für die Serverinstanz erstellten lokalen Sicherheitsgruppe die Berechtigungen.  
  
 Der Name der Sicherheitsgruppe folgt einem Muster. Das Präfix ist immer `SQLServerMSASUser$`, gefolgt vom Computernamen, und endet mit dem Instanznamen. Die Standardinstanz ist `MSSQLSERVER`. Eine benannte Instanz ist der Name, der während des Einrichtens festgelegt wurde.  
  
 Sie finden diese Sicherheitsgruppe in den lokalen Sicherheitseinstellungen:  
  
-   Führen Sie compmgmt.msc | **Lokale Benutzer und Gruppen** | **Gruppen** | `SQLServerMSASUser$`\<Servername >`$MSSQLSERVER` (für eine Standardinstanz).  
  
-   Doppelklicken Sie auf die Sicherheitsgruppe, um deren Mitglieder anzuzeigen.  
  
 Die einzige Mitglieder der Gruppe ist die Pro-Dienst-SID. Rechts daneben ist das Anmeldekonto. Den Namen des Anmeldekontos ist kosmetischer Natur, um einen Kontext für die Pro-Dienst-SID anzugeben. Wenn Sie später das Anmeldekonto ändern und dann zu dieser Seite zurückkehren, werden Sie feststellen, dass die Sicherheitsgruppe und die Pro-Dienst-SID nicht geändert wurden, aber die Anmeldekontobezeichnung anders ist.  
  
##  <a name="bkmk_winpriv"></a> Windows-Berechtigungen, die dem Analysis Services-Dienstkonto zugewiesen sind  
 Analysis Services benötigt Berechtigungen vom Betriebssystem für das Starten des Dienstes sowie das Anfordern von Systemressourcen. Die Anforderungen variieren je nach Servermodus und sind außerdem abhängig davon, ob die Instanz gruppiert ist. Details zu Windows-Berechtigungen finden Sie unter [Privileges](https://msdn.microsoft.com/library/windows/desktop/aa379306\(v=vs.85\).aspx) und [Privilege Constants (Windows)](/windows/desktop/SecAuthZ/privilege-constants) .  
  
 Alle Instanzen von Analysis Services erfordern die Berechtigung **Anmelden als Dienst** (SeServiceLogonRight). SQL Server-Setup weist die Berechtigung dem Dienstkonto zu, das Sie bei der Installation angegeben haben. Bei Servern, die im mehrdimensionalen oder im Data Mining-Modus ausgeführt werden, ist dies die einzige Windows-Berechtigung, die für das Analysis Services-Dienstkonto für eigenständige Serverinstallationen benötigt wird. Außerdem ist es die einzige Berechtigung, die beim Setup für Analysis Services konfiguriert wird. Für gruppierte und tabellarische Instanzen müssen Sie Windows-Berechtigungen manuell hinzufügen.  
  
 Failoverclusterinstanzen im tabellarischen oder multidimensionalen Modus erfordern außerdem ein **Anheben der Zeitplanungspriorität** (SeIncreaseBasePriorityPrivilege).  
  
 Tabellarische Instanzen nutzen die folgenden drei zusätzlichen Privilegien, die nach der Installation der Instanz manuell hinzugefügt werden müssen.  
  
|||  
|-|-|  
|**Arbeitssatz eines Prozesses vergrößern** (SeIncreaseWorkingSetPrivilege)|Dieses Privileg ist standardmäßig für alle Benutzer über die **Benutzer** -Sicherheitsgruppe verfügbar. Wenn Sie einen Server sperren, indem Sie Berechtigungen für diese Gruppe entfernen, kann Analysis Services unter Umständen nicht gestartet werden. Es wird dann folgende Fehlermeldung ausgegeben: "Dem Client fehlt ein erforderliches Privileg." Stellen Sie bei Auftreten dieses Fehlers die Berechtigung für Analysis Services wieder her, indem Sie sie der entsprechenden Analysis Services-Sicherheitsgruppe gewähren.|  
|**Speicherkontingente für einen Prozess anpassen** (SeIncreaseQuotaSizePrivilege)|Diese Berechtigung wird verwendet, um mehr Speicherplatz anzufordern, wenn ein Prozess nicht über ausreichende Ressourcen verfügt, um die Ausführung abschließen zu können, in Abhängigkeit von den für die Instanz festgelegten Arbeitsspeicherschwellenwerten.|  
|**Sperren von Seiten im Speicher** (SeLockMemoryPrivilege)|Diese Berechtigung ist nur erforderlich, wenn die Auslagerung vollständig ausgeschaltet wird. Standardmäßig verwendet eine tabellarische Serverinstanz die Windows-Auslagerungsdatei. Sie können dieses Verhalten jedoch ändern, indem Sie `VertiPaqPagingPolicy` auf 0 einstellen.<br /><br /> `VertiPaqPagingPolicy` auf 1 (Standard) weist die tabellarische Serverinstanz an, die Windows-Auslagerungsdatei zu verwenden. Belegungen sind nicht gesperrt, sodass Windows erforderliche Auslagerungen vornehmen kann. Da die Auslagerung verwendet wird, ist das Sperren von Seiten im Speicher nicht erforderlich. Daher ist es bei der Standardkonfiguration (, in denen `VertiPaqPagingPolicy` = 1), Sie müssen nicht gewähren der **Sperren von Seiten im Speicher** , einer tabellarischen Instanz die Berechtigung.<br /><br /> `VertiPaqPagingPolicy` auf 0. Wenn Sie die Auslagerung für Analysis Services ausschalten, werden Belegungen gesperrt, wenn die Berechtigung **Sperren von Seiten im Speicher** gewährt wurde. Bei dieser Einstellungen und mit der Berechtigung **Sperren von Seiten im Speicher** kann Windows keine Speicherbelegungen für Analysis Services auslagern, wenn im System nicht genügend Arbeitsspeicher vorhanden ist. Analysis Services greift auf die **Sperren von Seiten im Speicher** Berechtigung, wie die Erzwingung hinter `VertiPaqPagingPolicy` = 0. Beachten Sie, dass das Ausschalten der Windows-Auslagerung nicht empfohlen wird. Dadurch treten mehr Fehler aufgrund von nicht ausreichendem Arbeitsspeicher bei Vorgängen auf, die mit Auslagerung erfolgreich ausgeführt worden wären. Finden Sie unter [Speichereigenschaften](../server-properties/memory-properties.md) für Weitere Informationen zu `VertiPaqPagingPolicy`.|  
  
#### <a name="to-view-or-add-windows-privileges-on-the-service-account"></a>So können Sie Windows-Berechtigungen mit dem Dienstkonto anzeigen oder hinzufügen  
  
1.  Führen Sie GPEDIT.msc aus und wählen Sie Richtlinie für "Lokaler Computer" | Computerkonfiguration | Windows-Einstellungen | Sicherheitseinstellungen | Lokale Richtlinien | Zuweisen von Benutzerrechten.  
  
2.  Prüfen Sie vorhandene Richtlinien, die enthalten `SQLServerMSASUser$`. Hierbei handelt es sich um eine lokale Sicherheitsgruppe auf Computern mit einer Analysis Services-Installation. Diese Sicherheitsgruppe erhält sowohl Windows-Berechtigungen als auch Dateiordnerberechtigungen. Doppelklicken Sie auf die Richtlinie **Anmelden als Dienst** , um anzuzeigen, wie die Sicherheitsgruppe im System angegeben wurde. Der vollständige Name der Sicherheitsgruppe variiert abhängig davon, ob Sie Analysis Services als benannte Instanz installiert haben. Nutzen Sie diese Sicherheitsgruppe, statt des Dienstkontos, wenn Sie Kontoberechtigungen hinzufügen.  
  
3.  Klicken Sie mit der rechten Maustaste auf **Arbeitssatz eines Prozesses vergrößern** , und wählen Sie **Eigenschaften**aus, um Kontoberechtigungen in GPEDIT hinzuzufügen.  
  
4.  Klicken Sie auf **Benutzer oder Gruppe hinzufügen**.  
  
5.  Geben Sie die Benutzergruppe für die Analysis Services-Instanz ein. Beachten Sie, dass das Dienstkonto ein Mitglied der lokalen Sicherheitsgruppe ist. Daher müssen Sie den Namen des lokalen Computers als Domäne des Kontos voranstellen.  
  
     Die folgende Liste enthält zwei Beispiele für eine Standardinstanz. Diese heißt "Tabular" auf einem Computer namens "SQL01-WIN12", wobei der Computername die lokale Domäne ist.  
  
    -   SQL01-WIN12\SQL01-WIN12$SQLServerMSASUser$MSSQLSERVER  
  
    -   SQL01-WIN12\SQL01-WIN12$SQLServerMSASUser$TABULAR  
  
6.  Wiederholen Sie dies für **Anpassen des Arbeitsspeicherkontingents für einen Prozess**und optional für **Sperren von Seiten im Speicher** oder **Erhöhen der Zeitplanungspriorität**.  
  
> [!NOTE]  
>  In vorherigen Versionen von Setup wurde das Analysis Services-Dienstkonto versehentlich der Gruppe **Leistungsprotokollbenutzer** hinzugefügt. Obwohl das Problem behoben wurde, kann diese unnötige Gruppenmitgliedschaft in vorhandenen Installationen noch bestehen. Da das [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] -Dienstkonto keine Mitgliedschaft in der Gruppe **Leistungsprotokollbenutzer** erfordert, können Sie es aus der Gruppe entfernen.  
  
##  <a name="bkmk_FilePermissions"></a> Dateisystemberechtigungen, die dem Analysis Services-Dienstkonto zugewiesen sind  
  
> [!NOTE]  
>  Eine Liste der Berechtigungen für die einzelnen Programmordner finden Sie unter [Konfigurieren von Windows-Dienstkonten und -Berechtigungen](../../database-engine/configure-windows/configure-windows-service-accounts-and-permissions.md) .  
>   
>  Unter [Konfigurieren von HTTP-Zugriff auf Analysis Services unter Internetinformationsdienste &#40;IIS&#41; 8.0](configure-http-access-to-analysis-services-on-iis-8-0.md) finden Sie Informationen zu Dateiberechtigungen im Zusammenhang mit IIS-Konfiguration und [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)].  
  
 Alle Dateisystemberechtigungen, die für Servervorgänge erforderlich sind, – einschließlich der erforderlichen Berechtigung für das Laden und Entladen von Datenbanken in einem festgelegten Datenordner – werden während der Installation von SQL Server Setup zugewiesen.  
  
 Der Berechtigungsinhaber für Datendateien, ausführbare Programmdateien, Konfigurationsdateien, Protokolldateien und temporäre Dateien ist eine lokale Sicherheitsgruppe, die von SQL Server Setup erstellt wurde.  
  
 Für jede installierte Instanz gibt es nur eine Sicherheitsgruppe. Die Sicherheitsgruppe ist nach der Instanz benannt – entweder **SQLServerMSASUser$ MSSQLSERVER** für die Standardinstanz oder `SQLServerMSASUser$` \<Servername >$\<Instancename > für eine benannte Instanz. Diese Sicherheitsgruppe erhält von Setup die Dateiberechtigungen, die zum Ausführen von Servervorgängen erforderlich sind. An den Sicherheitsberechtigungen für das Verzeichnis \MSAS12.MSSQLSERVER\OLAP\BIN erkennen Sie, dass die Sicherheitsgruppe (und nicht das Dienstkonto oder dessen Pro-Dienst-SID (Sicherheits-ID)) die Berechtigungen für dieses Verzeichnis besitzt.  
  
 Die Sicherheitsgruppe enthält nur ein Mitglied: die Pro-Dienst-SID des Startkontos für die [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] -Instanz. Setup fügt die Pro-Dienst-SID zur lokalen Sicherheitsgruppe hinzu. Die Verwendung einer Sicherheitsgruppe mit SID-Mitgliedschaft macht einen kleinen, aber wichtigen Unterschied dabei aus, wie SQL Server Setup im Vergleich mit der Datenbank-Engine Analysis Services bereitstellt.  
  
 Wenn Sie vermuten, dass Dateiberechtigungen beschädigt sind, führen Sie folgende Schritte aus, um sicherzustellen, dass der Dienst immer noch korrekt bereitgestellt wird:  
  
1.  Verwenden Sie das Service Control-Befehlszeilentool (sc.exe), um die SID einer Standarddienstinstanz zu erhalten.  
  
     `SC showsid MSSqlServerOlapService`  
  
     Verwenden Sie bei einer benannten Instanz (mit Instanzname Tabular) folgende Syntax:  
  
     `SC showsid MSOlap$Tabular`  
  
2.  Verwendung **Computer-Manager** | **lokale Benutzer und Gruppen** | **Gruppen** , überprüfen die Mitgliedschaft der SQLServerMSASUser$\<Servername >$\<Instancename > Sicherheitsgruppe.  
  
     Die Mitglieds-SID sollte der Pro-Dienst-SID aus Schritt 1 entsprechen.  
  
3.  Verwenden Sie **Windows-Explorer** | **Programme** | **Microsoft SQL Server** | MSASxx.MSSQLServer | **OLAP** | **bin** , um zu überprüfen, ob der Sicherheitsgruppe in Schritt 2 Ordnersicherheitseigenschaften erteilt wurden.  
  
> [!NOTE]  
>  SIDs sollten niemals entfernt oder geändert werden. Um eine pro-Dienst-SID wiederherzustellen, die versehentlich gelöscht wurde, finden Sie unter [ https://support.microsoft.com/kb/2620201 ](https://support.microsoft.com/kb/2620201).  
  
 **Weitere Informationen zu Pro-Dienst-SIDs**  
  
 Jedes Windows-Konto verfügt über eine zugeordnete [SID](http://en.wikipedia.org/wiki/Security_Identifier), allerdings können Dienste ebenfalls eine SID aufweisen, die daher Pro-Dienst-SID genannt wird. Eine Pro-Dienst-SID wird erstellt, wenn die Dienstinstanz installiert ist. Sie ist das eindeutige, feste Element des Dienstes. Die Pro-Dienst-SID ist eine lokale, auf Computerebene aus dem Dienstnamen generierte SID. Auf einer Standardinstanz lautet der benutzerfreundliche Name NT SERVICE\MSSQLServerOLAPService.  
  
 Eine Pro-Dienst-SID bietet den Vorteil, dass das allgemein sichtbare Anmeldekonto beliebig geändert werden kann, ohne dass sich dies auf die Dateiberechtigungen auswirkt. Angenommen, Sie haben zwei Analysis Services-Instanzen in Form einer Standardinstanz und einer benannten Instanz installiert, die beide unter demselben Windows-Benutzerkonto ausgeführt werden. Solange das Anmeldekonto freigegeben ist, wird jede Dienstinstanz eine eindeutige Pro-Dienst-SID haben. Diese SID unterscheidet sich von der SID des Anmeldekontos. Die Pro-Dienst-SID wird für Dateiberechtigungen und Windows-Berechtigungen verwendet. Im Gegensatz dazu dient die Anmeldekonto-SID für Authentifizierungs- und Autorisierungsszenarien ─ verschiedene SIDs für verschiedene Zwecke.  
  
 Da die SID unveränderlich ist, können während der Installation eines Dienstes erstellte Dateisystem-ACLs beliebig oft verwendet werden, und zwar unabhängig von der Anzahl der Änderungen am Kontonamen. Darüber hinaus bieten ACLs, in denen Berechtigungen per SID angegeben sind, zusätzliche Sicherheit, da sie gewährleisten, dass der Zugriff auf ausführbare Programmdateien und Datenordner ausschließlich über eine einzelne Dienstinstanz erfolgt. Dies gilt selbst dann, wenn weitere Dienste unter demselben Konto ausgeführt werden.  
  
##  <a name="bkmk_tasks"></a> Gewähren zusätzlicher Analysis Services-Berechtigungen für spezifische Servervorgänge  
 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] führt einige Tasks im Sicherheitskontext des Dienstkontos (oder des Anmeldekontos) aus, das zum Starten von [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]verwendet wird; andere Tasks werden im Sicherheitskontext des Benutzers ausgeführt, der den Task anfordert.  
  
 In der folgenden Tabelle werden zusätzliche Berechtigungen beschrieben, die zum Ausführen von Tasks über das Dienstkonto erforderlich sind.  
  
|Servervorgang|Arbeitselement|Begründung|  
|----------------------|---------------|-------------------|  
|Remotezugriff auf externe relationale Datenquellen|Erstellen eines Datenbankanmeldenamens für das Dienstkonto|Bei der Verarbeitung werden Daten aus einer externen Datenquelle (normalerweise einer relationalen Datenbank) abgerufen und anschließend in eine [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] -Datenbank geladen. Eine der Anmeldeinformationsoptionen für das Abrufen externer Daten besteht darin, das Dienstkonto zu verwenden Diese Anmeldeinformationsoption kann nur verwendet werden, wenn Sie eine Datenbankanmeldung für das Dienstkonto erstellen und Leseberechtigungen für die Quelldatenbank erteilen. Informationen dazu, wie diese Dienstkontooption für diesen Task verwendet wird, finden Sie unter [Festlegen von Identitätswechseloptionen &#40;SSAS – mehrdimensional&#41;](../multidimensional-models/set-impersonation-options-ssas-multidimensional.md). Dieselben Identitätswechseloptionen sind auch verfügbar, wenn ROLAP als Speichermodus verwendet wird. In diesem Fall muss das Konto außerdem über Schreibzugriff auf die Quelldaten verfügen, damit die ROLAP-Partitionen verarbeitet (d. h. Aggregationen gespeichert) werden können.|  
|DirectQuery|Erstellen eines Datenbankanmeldenamens für das Dienstkonto|DirectQuery ist eine Tabellenfunktion zum Abfragen externer Datasets, die entweder zu groß für das tabellarische Modell sind oder andere Merkmale aufweisen, für die DirectQuery besser als die Standardoption für die arbeitsspeicherinterne Speicherung geeignet ist. Eine der im DirectQuery-Modus verfügbaren Verbindungsoptionen besteht in der Verwendung des Dienstkontos. Auch in diesem Fall kann die Option nur verwendet werden, wenn das Dienstkonto über eine Datenbankanmeldung sowie über Leseberechtigungen für die Zieldatenquelle verfügt. Informationen dazu, wie diese Dienstkontooption für diesen Task verwendet wird, finden Sie unter [Festlegen von Identitätswechseloptionen &#40;SSAS – mehrdimensional&#41;](../multidimensional-models/set-impersonation-options-ssas-multidimensional.md). Alternativ können Daten mithilfe der Anmeldeinformationen des aktuellen Benutzers abgerufen werden. Da diese Option in den meisten Fällen eine Double-Hop-Verbindung umfasst, sollte das Dienstkonto unbedingt für die eingeschränkte Kerberos-Delegierung konfiguriert werden, sodass das Dienstkonto Identitäten an einen Downstreamserver delegieren kann. Weitere Informationen finden Sie unter [Configure Analysis Services for Kerberos constrained delegation](configure-analysis-services-for-kerberos-constrained-delegation.md).|  
|Remotezugriff auf andere SSAS-Instanzen|Hinzufügen des Dienstkontos zu Analysis Services-Datenbankrollen, die auf dem Remoteserver definiert sind|Sowohl Remotepartitionen als auch verknüpfte Objekte auf anderen [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] -Remoteinstanzen, die auf die Remotepartitionen verweisen, sind Systemfunktionen, die Berechtigungen auf einem Remotecomputer oder -gerät erfordern. Beim Erstellen und Auffüllen von Remotepartitionen oder Einrichten eines verknüpften Objekts wird der Vorgang im Sicherheitskontext des aktuellen Benutzers ausgeführt. Werden diese Vorgänge anschließend automatisiert, erfolgt der [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] -Zugriff auf Remoteinstanzen im Sicherheitskontext des zugehörigen Dienstkontos. Um auf verknüpfte Objekte auf einer Remoteinstanz von [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]zugreifen zu können, muss das Anmeldekonto über Berechtigungen zum Lesen der entsprechenden Objekte auf der Remoteinstanz verfügen, z. B. über den Lesezugriff auf bestimmte Dimensionen. Entsprechend muss das Dienstkonto bei Verwendung von Remotepartitionen über Administratorrechte für die Remoteinstanz verfügen. Diese Berechtigungen werden auf der Analysis Services-Remoteinstanz unter Verwendung von Rollen erteilt, durch die einem bestimmten Objekt zulässige Vorgänge zugeordnet werden. Anleitungen zur Gewährung von Vollzugriffsberechtigungen, die Verarbeitung und Abfrageoperationen zulassen, finden Sie unter [Erteilen von Datenbankberechtigungen &#40;Analysis Services&#41;](../multidimensional-models/grant-database-permissions-analysis-services.md). Informationen zu Remotepartitionen finden Sie unter [Erstellen und Verwalten einer Remotepartition &#40;Analysis Services&#41;](../multidimensional-models/create-and-manage-a-remote-partition-analysis-services.md).|  
|Rückschreiben|Hinzufügen des Dienstkontos zu Analysis Services-Datenbankrollen, die auf dem Remoteserver definiert sind|Wenn die in mehrdimensionalen Modellen verwendbare Rückschreibefunktion in Clientanwendungen aktiviert ist, können während der Datenanalyse neue Datenwerte erstellt werden. Wenn das Rückschreiben in einer Dimension oder einem Cube aktiviert ist, muss das [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] -Dienstkonto über Schreibberechtigungen für die Rückschreibetabelle in der relationalen [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Quelldatenbank verfügen. Wenn diese Tabelle noch nicht vorhanden ist und erstellt werden muss, erfordert das [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] -Dienstkonto außerdem die Berechtigung zum Erstellen von Tabellen in der festgelegten [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Datenbank.|  
|Schreiben in eine Abfrageprotokolltabelle in einer relationalen [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Datenbank|Erstellen eines Datenbankanmeldenamens für das Dienstkonto und Zuweisen von Schreibrechten für die Abfrageprotokolltabelle|Sie können die Abfrageprotokollierung aktivieren, um in einer Datenbanktabelle Verwendungsdaten für nachfolgende Analysen zu sammeln. Das [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] -Dienstkonto muss über Schreibberechtigungen für die Abfrageprotokolltabelle in der festgelegten [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Datenbank verfügen. Wenn diese Tabelle noch nicht vorhanden ist und erstellt werden muss, erfordert das [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] -Anmeldekonto außerdem die Berechtigung zum Erstellen von Tabellen in der festgelegten [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Datenbank. Weitere Informationen finden Sie unter [Improve SQL Server Analysis Services Performance with the Usage Based Optimization Wizard (Blog)](http://www.mssqltips.com/sqlservertip/2876/improve-sql-server-analysis-services-performance-with-the-usage-based-optimization-wizard/) (Verbessern der Leistung von SQL Server Analysis Services mit dem Assistenten für die verwendungsbasierte Optimierung) und [Query Logging in Analysis Services (Blog)](http://weblogs.asp.net/miked/archive/2013/07/31/query-logging-in-analysis-services.aspx)(Abfrageprotokollierung in Analysis Services).|  
  
## <a name="see-also"></a>Siehe auch  
 [Konfigurieren von Windows-Dienstkonten und -Berechtigungen](../../database-engine/configure-windows/configure-windows-service-accounts-and-permissions.md)   
 [SQL Server-Dienstkonto und pro Dienst-SID (Blog)](http://www.travisgan.com/2013/06/sql-server-service-account-and-per.html)   
 [SQL Server verwendet eine Dienst-SID, um die Dienstisolation bereitzustellen (KB-Artikel)](https://support.microsoft.com/kb/2620201)   
 [Zugriffstoken (MSDN)](/windows/desktop/SecAuthZ/access-tokens)   
 [Sicherheits-IDs (MSDN)](/windows/desktop/SecAuthZ/security-identifiers)   
 [Zugriffstoken (Wikipedia)](http://en.wikipedia.org/wiki/Access_token)   
 [Zugriffssteuerungslisten (Wikipedia)](http://en.wikipedia.org/wiki/Access_control_list)  
  
  
