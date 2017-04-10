---
title: "Dateispeicherorte f&#252;r Standard- und benannte Instanzen von SQL Server | Microsoft Docs"
ms.custom: ""
ms.date: "03/14/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "setup-install"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 463c570e-9f75-4653-b3b8-4d61753b0013
caps.latest.revision: 16
author: "MikeRayMSFT"
ms.author: "mikeray"
manager: "jhubbard"
caps.handback.revision: 16
---
# Dateispeicherorte f&#252;r Standard- und benannte Instanzen von SQL Server
  Eine Installation von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] besteht aus einer oder mehreren separaten Instanzen. Eine Instanz (Standard- als auch benannte Instanz) besitzt eine Reihe eigener Programm- und Datendateien sowie mehrere freigegebene Dateien, die für alle Instanzen von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] auf dem Computer freigegeben werden.  
  
 Für eine Instanz von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], die [!INCLUDE[ssDE](../../includes/ssde-md.md)], [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] und [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] umfasst, verfügt jede Komponente über einen vollständigen Satz an Daten- und ausführbaren Dateien sowie die für alle Komponenten freigegebenen Dateien.  
  
 Zum Isolieren der Installationsspeicherorte für jede Komponente werden eindeutige Instanz-IDs für jede Komponente innerhalb einer bestimmten [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Instanz generiert.  
  
> [!IMPORTANT]  
>  Programm- und Datendateien können weder auf einem Wechseldatenträger, auf einem Dateisystem mit Komprimierung, in einem Verzeichnis mit Systemdateien noch auf freigegebenen Laufwerken einer Failoverclusterinstanz installiert werden.  
>  
>  Möglicherweise müssen Sie Softwareanwendungen wie beispielsweise Viren- und Spywarescanner so konfigurieren, dass SQL Server-Ordner und -Dateitypen ausgeschlossen werden. Weitere Informationen finden Sie im folgenden Artikel: [Gewusst wie: Auswählen, wie Antivirussoftware auf Computern ausgeführt werden soll, auf denen SQL Server ausgeführt wird](https://support.microsoft.com/kb/309422).
> 
>  Systemdatenbanken (Master, Model, MSDB und TempDB) und [!INCLUDE[ssDE](../../includes/ssde-md.md)]-Benutzerdatenbanken können mit dem SMB (Server Message Block)-Dateiserver als Speicheroption installiert werden. Dies gilt sowohl für eigenständige [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]- als auch für [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Failoverclusterinstallationen (FCI). Weitere Informationen finden Sie unter [Installieren von SQL Server mit SMB-Dateifreigabe als Speicheroption](../../database-engine/install-windows/install-sql-server-with-smb-fileshare-as-a-storage-option.md).  
>   
>  Löschen Sie keines der folgenden Verzeichnisse oder dessen Inhalt: Binn, Data, Ftdata, HTML oder 1033. Andere Verzeichnisse können ggf. gelöscht werden. Möglicherweise können Sie auf diese Weise verloren gegangene Funktionalität oder Daten dann aber nur abrufen, indem Sie [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] deinstallieren und anschließend erneut installieren. Löschen oder ändern Sie keine HTM-Dateien im Verzeichnis HTML. Sie sind für die ordnungsgemäße Funktion der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Tools erforderlich.  
  
## Freigegebene Dateien für alle Instanzen von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]  
 Gemeinsame, von allen Instanzen auf einem Computer verwendete Dateien werden im Ordner [!INCLUDE[ssInstallPathVar](../../includes/ssinstallpathvar-md.md)] installiert, wobei \<*drive*> für den Buchstaben des Laufwerks steht, auf dem die Komponenten installiert sind. Der Standardwert ist Laufwerk "C".  
  
## Dateispeicherorte und Registrierungszuordnung  
 Während des Setups von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] wird für jede Serverkomponente eine Instanz-ID generiert. Die Serverkomponenten in dieser Version von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] sind [!INCLUDE[ssDE](../../includes/ssde-md.md)], [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] und [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)].  
  
 Die Standardinstanz-ID wird mit dem folgenden Format erstellt:  
  
-   Auf MSSQL für [!INCLUDE[ssDE](../../includes/ssde-md.md)] folgt die Hauptversionsnummer, ggf. gefolgt von einem Unterstrich und der Nebenversionsnummer, und ein Punkt, woraufhin wiederum der Instanzname folgt.  
  
-   Auf MSSQL für [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] folgt die Hauptversionsnummer, ggf. gefolgt von einem Unterstrich und der Nebenversionsnummer, und ein Punkt, woraufhin wiederum der Instanzname folgt.  
  
-   Auf MSRS für [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] folgt die Hauptversionsnummer, ggf. gefolgt von einem Unterstrich und der Nebenversionsnummer, und ein Punkt, woraufhin wiederum der Instanzname folgt.  
  
 Beispiele für Standardinstanz-IDs in dieser Version von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] lauten wie folgt:  
  
-   MSSQL13.MSSQLSERVER für eine Standardinstanz von [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].  
  
-   MSAS13.MSSQLSERVER für eine Standardinstanz von [!INCLUDE[ssASCurrent](../../includes/ssascurrent-md.md)].  
  
-   MSSQL13.MyInstance für eine benannte Instanz von [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] mit dem Namen "MyInstance".  
  
 Die Verzeichnisstruktur für eine mit dem Namen "MyInstance" benannte [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]-Instanz, die [!INCLUDE[ssDE](../../includes/ssde-md.md)] und [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] umfasst und in den Standardverzeichnissen installiert ist, lautet wie folgt:  
  
-   C:\Programme\Microsoft SQL Server\MSSQL13.MyInstance\  
  
-   C:\Programme\Microsoft SQL Server\MSAS13.MyInstance\  
  
 Sie können jeden Wert für die Instanz-ID angeben, sollten aber Sonderzeichen und reservierte Schlüsselwörter vermeiden.  
  
 Sie können während des [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Setups eine nicht standardmäßige Instanz-ID angeben. Anstelle von \<Programme>\\[!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] wird ein \<benutzerdefinierter Pfad>\\[!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] verwendet, wenn der Benutzer eine Änderung des Standardinstallationsverzeichnisses auswählt. Beachten Sie, dass die Instanz-IDs, die mit einem Unterstrich (_) beginnen oder das Nummernzeichen (#) oder Dollarzeichen ($) enthalten, nicht unterstützt werden.  
  
> [!NOTE]  
>  [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] und Clientkomponenten sind nicht instanzabhängig und bekommen daher keine Instanz-ID zugewiesen. Standardmäßig werden nicht instanzabhängige Komponenten in einem einzelnen Verzeichnis installiert: [!INCLUDE[ssInstallPathVar](../../includes/ssinstallpathvar-md.md)]. Wenn der Installationspfad einer freigegebenen Komponente geändert wird, wirkt sich diese Änderung auch auf die anderen freigegebenen Komponenten aus. Bei allen zukünftigen Installationen werden die nicht instanzbezogenen Komponenten wieder im gleichen Verzeichnis installiert wie bei der ursprünglichen Installation.  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] ist die einzige [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Komponente, die nach der Installation Instanzumbenennung unterstützt. Wenn eine Instanz von [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] umbenannt wird, ändert sich die Instanz-ID nicht. Nach abgeschlossener Instanzumbenennung wird die während der Installation erstellte Instanz-ID von Verzeichnissen und Registrierungsschlüsseln weiterhin verwendet.  
  
 Die Registrierungsstruktur wird für instanzabhängige Komponenten unter HKLM\Software\\[!INCLUDE[msCoName](../../includes/msconame-md.md)]\\[!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]\\<*Instanz-ID*> erstellt. Beispiel:  
  
-   HKLM\Software\\[!INCLUDE[msCoName](../../includes/msconame-md.md)]\\[!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]\MSSQL13.MyInstance  
  
-   HKLM\Software\\[!INCLUDE[msCoName](../../includes/msconame-md.md)]\\[!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]\MSAS13.MyInstance  
  
-   HKLM\Software\\[!INCLUDE[msCoName](../../includes/msconame-md.md)]\\[!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]\MSRS13.MyInstance  
  
 Die Registrierung verwaltet auch eine Zuordnung der Instanz-ID zum Instanznamen. Die Zuordnung der Instanz-ID zum Instanznamen wird folgendermaßen verwaltet:  
  
-   [HKEY_LOCAL_MACHINE\Software\\[!INCLUDE[msCoName](../../includes/msconame-md.md)]\\[!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]\Instanznamen\SQL] "InstanceName"="MSSQL13"  
  
-   [HKEY_LOCAL_MACHINE\Software\\[!INCLUDE[msCoName](../../includes/msconame-md.md)]\\[!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]\Instanznamen\OLAP] "InstanceName"="MSAS13"  
  
-   [HKEY_LOCAL_MACHINE\Software\\[!INCLUDE[msCoName](../../includes/msconame-md.md)]\\[!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]\Instanznamen\RS] "InstanceName"="MSRS13"  
  
## Angeben von Dateipfaden  
 Beim Setup können Sie den Installationspfad für die folgenden Funktionen ändern:  
  
 Der Installationspfad wird im Setup nur für die Funktionen angezeigt, die einen vom Benutzer konfigurierbaren Zielordner besitzen.  
  
|Komponente|Standardpfad|Konfigurierbarer oder fester Pfad|  
|---------------|------------------|--------------------------------|  
|[!INCLUDE[ssDE](../../includes/ssde-md.md)] Serverkomponenten|\Programme\\[!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]\MSSQL13.\<InstanceID>\|Konfigurierbar|  
|[!INCLUDE[ssDE](../../includes/ssde-md.md)] Datendateien|\Programme\\[!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]\MSSQL13.\<InstanceID>\|Konfigurierbar|  
|[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] server|\Program Files\\[!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]\MSAS13.\<InstanceID>\|Konfigurierbar|  
|[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] Datendateien|\Program Files\\[!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]\MSAS13.\<InstanceID>\|Konfigurierbar|  
|[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] Berichtsserver|\Programme\\[!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]\MSRS13.\<Instanz-ID>\Reporting Services\ReportServer\Bin\|Konfigurierbar|  
|[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] Berichts-Manager|\Programme\\[!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]\MSRS13.\<Instanz-ID>\Reporting Services\ReportManager\|Fester Pfad|  
|[!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]|\<Installationsverzeichnis>\130\DTS\|Konfigurierbar*|  
|Clientkomponenten (außer bcp.exe und sqlcmd.exe)|\<Installationsverzeichnis>\130\Tools\|Konfigurierbar*|  
|Clientkomponenten (bcp.exe und sqlcmd.exe)|\<Installationsverzeichnis>\Client SDK\ODBC\110\Tools\Binn|Fester Pfad|  
|Replikations- und serverbasierte COM-Objekte|[!INCLUDE[ssInstallPathVar](../../includes/ssinstallpathvar-md.md)]COM\\**|Fester Pfad|  
|[!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] Von Integration Services bereitgestellte DLLs für das Data Transformation Runtime-Modul, das Data Transformation Pipeline-Modul und das **dtexec**-Eingabeaufforderungshilfsprogramm|[!INCLUDE[ssInstallPathVar](../../includes/ssinstallpathvar-md.md)]DTS\Binn|Fester Pfad|  
|DLLs, die die Verbindungsunterstützung für Integration Services verwalten [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]|[!INCLUDE[ssInstallPathVar](../../includes/ssinstallpathvar-md.md)]DTS\Verbindungen|Fester Pfad|  
|DLLs für alle Arten von Enumeratoren, die von [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] unterstützt werden|[!INCLUDE[ssInstallPathVar](../../includes/ssinstallpathvar-md.md)]DTS\ForEach-Enumeratoren|Fester Pfad|  
|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Browser-Dienst, WMI-Anbieter|[!INCLUDE[ssInstallPathVar](../../includes/ssinstallpathvar-md.md)]Shared\|Fester Pfad|  
|Komponenten, die von allen Instanzen von gemeinsam genutzt werden [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]|[!INCLUDE[ssInstallPathVar](../../includes/ssinstallpathvar-md.md)]Shared\|Fester Pfad|  
  
 **\*\*Sicherheitshinweis\*\*** Stellen Sie sicher, dass der Ordner \Programme\\[!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]\ durch entsprechend eingeschränkte Berechtigungen geschützt wird.  
  
 Beachten Sie, dass das Standardlaufwerk für Dateispeicherorte *systemdrive* lautet, normalerweise Laufwerk C. Installationspfade für untergeordnete Funktionen werden durch die Installationspfade der übergeordneten Funktion bestimmt.  
  
 *Ein einzelner Installationspfad wird von [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] und Clientkomponenten gemeinsam genutzt. Wenn der Installationspfad einer Komponente geändert wird, wirkt sich diese Änderung auch auf die anderen Komponenten aus. Bei allen zukünftigen Installationen werden die Komponenten wieder am gleichen Speicherort installiert wie bei der ursprünglichen Installation.  
  
 **Das Verzeichnis wird von allen auf dem Computer installierten Instanzen von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] verwendet. Wenn Sie ein Update auf eine der Instanzen auf dem Computer anwenden, wirken sich alle Änderungen an den Dateien dieses Ordners auch auf die übrigen auf dem Computer installierten Instanzen aus. Wenn Sie Funktionen zu einer vorhandenen Installation hinzufügen, können Sie den Speicherort einer vorher installierten Funktion nicht ändern und auch keinen Speicherort für eine neue Funktion angeben. Sie müssen zusätzliche Funktionen entweder in die durch das Setup bereits vorgegebenen Verzeichnisse installieren, oder Sie deinstallieren das Produkt und installieren es anschließend neu.  
  
> [!NOTE]  
>  Bei gruppierten Konfigurationen müssen Sie ein lokales Laufwerk auswählen, das für jeden Knoten des Clusters verfügbar ist.  
  
 Wenn Sie beim Setup einen Installationspfad für die Serverkomponenten oder Datendateien angeben, verwendet das Setup-Programm die Instanzkennung zusätzlich zum angegebenen Speicherort für Programm- und Datendateien. Die Instanz-ID wird vom Setup nicht für Tools und andere freigegebene Dateien verwendet. Darüber hinaus verwendet das Setup keine Instanz-ID für das [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]-Programm und Datendateien. Für das [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]-Repository wird jedoch eine Instanz-ID verwendet.  
  
 Wenn Sie einen Installationspfad für die Funktion [!INCLUDE[ssDE](../../includes/ssde-md.md)] festlegen, wird dieser Pfad vom [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Setup als Stammverzeichnis für alle instanzspezifischen Ordner der Installation, einschließlich der SQL-Datendateien, verwendet. Wenn Sie in diesem Fall C:\Programme\\[!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]\MSSQL13.\<Instanzname>\MSSQL\\ als Stammverzeichnis festlegen, werden die instanzspezifischen Verzeichnisse am Ende dieses Pfads hinzugefügt.  
  
 Wenn die im Installations-Assistenten für [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] bereitgestellte Upgradefunktionalität USESYSDB verwendet wird, kann der Fall eintreten, dass das Produkt in einer rekursiven Ordnerstruktur installiert wird. Zum Beispiel \<*SQLProgramFiles*>\MSSQL13\MSSQL\MSSQL10_50\MSSQL\Data\\. Legen Sie stattdessen bei Verwendung der USESYSDB-Funktion nur einen Installationspfad für die Funktion "SQL-Datendateien" und nicht für die Funktion [!INCLUDE[ssDE](../../includes/ssde-md.md)] fest.  
  
> [!NOTE]  
>  Datendateien werden erwartungsgemäß immer in einem untergeordneten Verzeichnis mit dem Namen Data gesucht. Geben Sie beispielsweise beim Upgrade C:\Programme\\[!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]\MSSQL13.\<Instanzname>\ als Stammpfad zum Datenverzeichnis der Systemdatenbanken an, wenn sich die Datendateien unter C:\Programme\\[!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]\MSSQL13.\<Instanzname>\MSSQL\Data befinden.  
  
## Siehe auch  
 [Konfiguration des Datenbankmodells - Datenverzeichnisse](../Topic/Database%20Engine%20Configuration%20-%20Data%20Directories.md)   
 [Konfigurationseigenschaften von Analysis Services – Datenverzeichnisse](../Topic/Analysis%20Services%20Configuration%20-%20Data%20Directories.md)  
  
  