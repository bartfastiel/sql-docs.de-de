---
title: "Hardware- und Softwareanforderungen f&#252;r die Installation von SQL Server 2016 | Microsoft Docs"
ms.custom: 
  - "SQL2016_New_Updated"
ms.date: "03/14/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "setup-install"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Setup [SQL Server], Software"
  - "Software [SQL Server]"
  - "Installieren von SQL Server, Software"
  - "Betriebssysteme [SQL Server], SQL Server-Anforderungen"
  - "Setup [SQL Server], sprachübergreifende Unterstützung"
  - "Betriebssysteme [SQL Server], sprachübergreifende Unterstützung"
  - "Netzwerkverbindungen [SQL Server], Anforderungen"
  - "Speicherplatz [SQL Server], SQL Server-Installationen"
  - "WOW [SQL Server]"
  - "Setup [SQL Server], hardware"
  - "Abhängigkeiten [SQL Server], SQL Server-Installationen"
  - "Clusterhardwareanforderungen [SQL Server]"
  - "Endpunkte [SQL Server], SQL Server-Installationen"
  - "Internet [SQL Server], SQL Server-Installationen"
  - "Hardware [SQL Server]"
  - "Windows on Windows [SQL Server]"
  - "Installieren von SQL Server, Hardware"
  - "Systemkonfigurationsprüfung"
  - "SCC [SQL Server]"
  - "Betriebssystem [SQL Server]"
  - "Speicherplatz [SQL Server], SQL Server-Installationen"
  - "Systemkonfigurationsprüfung"
  - "Installieren von SQL Server, sprachübergreifende Unterstützung"
  - "Internet [SQL Server]"
  - "Speicherplatz [SQL Server]"
  - "Erweiterte Systemunterstützung [SQL Server]"
  - "64-Bit-Edition [SQL Server]"
  - "Failover-Clusterunterstützung [SQL Server]"
  - "Failover-Clusterunterstützung [SQL Server], Hardwareanforderungen"
  - "32-Bit-Edition [SQL Server]"
  - "Gebietsschemas [SQL Server], SQL Server-Installationen"
  - "Sprachübergreifende Unterstützung"
  - "Speicherplatz [SQL Server]"
  - "Lokalisierte SQL Server-Versionen"
ms.assetid: 09bcf20b-0a40-4131-907f-b61479d5e4d8
caps.latest.revision: 333
ms.author: "mikeray"
manager: "jhubbard"
---
# Hardware- und Softwareanforderungen f&#252;r die Installation von SQL Server 2016
  In diesem Thema sind die Mindestanforderungen an die Hardware und Software aufgeführt, um [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] zu installieren und auszuführen.  
  
 **Probieren Sie es aus:**  
  
-   Download von SQL Server aus dem [**Evaluierungscenter**.](https://www.microsoft.com/en-us/evalcenter/evaluate-sql-server-2016) 
  
-    Starten eines virtuellen Computers mit vorinstalliertem [**SQL Server 2016**](https://azure.microsoft.com/en-us/marketplace/partners/microsoft/sqlserver2016rtmenterprisewindowsserver2012r2/?wt.mc_id=sqL16_vm).  
  
 **Die folgenden Überlegungen betreffen alle Editionen:**  
  
-   Es wird empfohlen, [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] auf Computern mit dem NTFS- oder ReFS-Dateiformat auszuführen. Die Installation von [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] auf einem Computer mit FAT32-Dateisystem wird zwar unterstützt, ist aber nicht empfehlenswert, da sie weniger Sicherheit als eine Installation unter dem NTFS- oder ReFS-Dateisystem bietet.  
  
-   Das [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Setup blockiert Installationen auf schreibgeschützten, zugeordneten oder komprimierten Laufwerken.  
  
-   Bei der Installation tritt ein Fehler auf, wenn Sie das Setup über eine Remotedesktopverbindung mit den Medien auf einer lokalen Ressource im RDC-Client starten. Für die Remoteinstallation müssen sich die Medien auf einer Netzwerkfreigabe oder lokal auf dem physischen oder virtuellen Computer befinden. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Installationsmedien befinden sich entweder auf einer Netzwerkfreigabe, einem zugeordneten Laufwerk, einem lokalen Laufwerk oder werden einem virtuellen Computer als ISO zur Verfügung gestellt.  
  
-   Die [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]-Installation erfordert die Installation von .NET 4.6.1 als erforderliche Komponente. .NET 4.6.1 wird automatisch vom Setup installiert, wenn [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] ausgewählt wird.  
  
-   Beim [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Setup werden die folgenden vom Produkt benötigten Softwarekomponenten installiert:  
  
    -   [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client  
  
    -   [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Setuphilfsdateien  
  
-   Die Mindestanforderungen an die Version zum Installieren von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] unter [!INCLUDE[win8srv](../../includes/win8srv-md.md)] oder [!INCLUDE[win8](../../includes/win8-md.md)]finden Sie unter [Installieren von SQL Server unter Windows Server 2012 oder Windows 8](http://support.microsoft.com/kb/2681562) (http://support.microsoft.com/kb/2681562).  
  
 Dieses Thema enthält folgende Abschnitte:  
  
-   [Hardware- und Softwareanforderungen](../../sql-server/install/hardware-and-software-requirements-for-installing-sql-server-2016.md#hwswr)  
  
-   [Anforderungen an Prozessor, Arbeitsspeicher und Betriebssystem](../../sql-server/install/hardware-and-software-requirements-for-installing-sql-server-2016.md#pmosr)  
  
-   [Sprachübergreifende Unterstützung](../../sql-server/install/hardware-and-software-requirements-for-installing-sql-server-2016.md#CrossLanguageSupport)  
  
-   [Anforderungen an den Festplattenspeicherplatz](../../sql-server/install/hardware-and-software-requirements-for-installing-sql-server-2016.md#HardDiskSpace)  
  
-   [Speichertypen für Datendateien](../../sql-server/install/hardware-and-software-requirements-for-installing-sql-server-2016.md#StorageTypes)  
  
-   [Installieren von SQL Server auf einem Domänencontroller](../../sql-server/install/hardware-and-software-requirements-for-installing-sql-server-2016.md#DC_support)  
  
##  <a name="a-namehwswra-hardware-and-software-requirements"></a><a name="hwswr"></a> Hardware- und Softwareanforderungen  
 Die folgenden Anforderungen gelten für alle Installationen:  
  
|Komponente|Anforderung|  
|---------------|-----------------|  
|.NET Framework|[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]RC1 und höher erfordern [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] 4.6 für das Datenbankmodul, die Master Data Services oder die Replikation. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 2016-Setup installiert automatisch [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)]. Sie können [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] auch manuell von der Seite [Microsoft .NET Framework 4.6 (Web Installer) für Windows](http://support.microsoft.com/kb/3045560) aus installieren.<br/><br/> Weitere Informationen, Empfehlungen und Anleitungen zu [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] 4.6 finden Sie unter [Handbuch für die Bereitstellung von .NET Framework für Entwickler](http://msdn.microsoft.com/library/ee942965\(v=vs.110\).aspx).<br/><br/>[!INCLUDE[winblue_client_2](../../includes/winblue-client-2-md.md)] und [!INCLUDE[winblue_server_2](../../includes/winblue-server-2-md.md)] erfordern [KB2919355](http://support.microsoft.com/kb/2919355) vor der Installation von [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] 4.6.|  
|Netzwerksoftware|Die unterstützten Betriebssysteme für [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] verfügen über integrierte Netzwerksoftware. Benannte und Standardinstanzen einer eigenständigen Installation unterstützen die folgenden Netzwerkprotokolle: Shared Memory, Named Pipes, TCP/IP und VIA.<br/><br/> Hinweis: Das Shared Memory-Protokoll und VIA werden in Failoverclustern nicht unterstützt.<br/><br/> Beachten Sie auch, dass das VIA-Protokoll veraltet ist. [!INCLUDE[ssNoteDepFutureAvoid](../../includes/ssnotedepfutureavoid-md.md)]<br/><br/> <br/><br/> Weitere Informationen zu Netzwerkprotokollen und Netzwerkbibliotheken finden Sie unter [Network Protocols and Network Libraries](../../sql-server/install/network-protocols-and-network-libraries.md).|  
|Festplatte|[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] erfordert mindestens 6 GB verfügbaren Festplattenspeicher.<br/><br/> Der erforderliche freie Festplattenspeicher ist von den installierten [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] -Komponenten abhängig. Weitere Informationen finden Sie unter [Anforderungen an den Festplattenspeicherplatz](../../sql-server/install/hardware-and-software-requirements-for-installing-sql-server-2016.md#HardDiskSpace) weiter unten in diesem Thema. Informationen zu unterstützten Speichertypen für Datendateien finden Sie unter [Speichertypen für Datendateien](../../sql-server/install/hardware-and-software-requirements-for-installing-sql-server-2016.md#StorageTypes).|  
|Laufwerk|Ein DVD-Laufwerk ist erforderlich, falls die Installation von einem DVD-Medium erfolgt.|  
|Monitor|[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] erfordert eine Super VGA-Grafikkarte mit einer Mindestauflösung von 800x600 Pixel.|  
|Internet|Zur Nutzung des Internets ist ein Internetzugang erforderlich (möglicherweise gebührenpflichtig).|  
  
 Hinweis: Das Ausführen von [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] auf einem virtuellen Computer ist wegen des Aufwandes der Virtualisierung langsamer als eine native Ausführung.  
  
 Es gibt zusätzliche Hardware- und Softwareanforderungen für die PolyBase-Funktion. Weitere Informationen finden Sie unter [Get started with PolyBase](../../relational-databases/polybase/get-started-with-polybase.md) (Erste Schritte mit PolyBase).  
  
##  <a name="a-namepmosra-processor-memory-and-operating-system-requirements"></a><a name="pmosr"></a> Anforderungen an Prozessor, Arbeitsspeicher und Betriebssystem  
 Der folgende Arbeitsspeicher- und Prozessoranforderungen gelten für alle Editionen von [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]:  
  
|Komponente|Anforderung|  
|---------------|-----------------|  
|Speicher*|**Minimum:**<br/><br/> Express-Editionen: 512 MB<br/><br/> Alle anderen Editionen: 1 GB<br/><br/> **Empfohlen:**<br/><br/> Express-Editionen: 1 GB<br/><br/> Alle anderen Editionen: mindestens 4 GB. Mit zunehmender Datenbankgröße sollte außerdem der Speicher erhöht werden, um eine optimale Leistung sicherzustellen.|  
|Prozessorgeschwindigkeit:|**Minimum:** x64-Prozessor: 1,4 GHz<br/><br/> **Empfohlen:** 2,0 GHz oder schneller|  
|Prozessortyp|x64-Prozessor: AMD Opteron, AMD Athlon 64, Intel Xeon mit Intel EM64T-Unterstützung, Intel Pentium IV mit EM64T-Unterstützung|  
  
> [!NOTE]  
>  Die Installation von [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] wird nur auf x64-Prozessoren unterstützt. Es wird nicht mehr auf x86 Prozessoren unterstützt.  
  
 *Zur Installation der [!INCLUDE[ssDQSServer](../../includes/ssdqsserver-md.md)]-Komponente in [!INCLUDE[ssDQSnoversion](../../includes/ssdqsnoversion-md.md)] (DQS) sind mindestens 2 GB RAM erforderlich. Dies unterscheidet sich von den Arbeitsspeichermindestanforderungen von [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]. Informationen zum Installieren von DQS finden Sie unter [Install Data Quality Services](../../data-quality-services/install-windows/install-data-quality-services.md).  
  
 **WOW64-Unterstützung:**  
  
 WOW64 (Windows 32-bit on Windows 64-bit) ist eine Funktion von 64-Bit-Editionen von Windows, die es ermöglicht, 32-Bit-Anwendungen systemintern im 32-Bit-Modus auszuführen. Anwendungen sind im 32-Bit-Modus funktionsfähig, obwohl es sich beim zugrunde liegenden Betriebssystem um ein 64-Bit-Betriebssystem handelt. WOW64 wird nicht für [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]-Installationen unterstützt. Allerdings werden Verwaltungstools in WOW64 unterstützt.  
  
 **Betriebssystemunterstützung:**  
  
 Die [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] -Editionen werden wie folgt unterteilt:  
  
-   [Prinzipaleditionen von SQL Server 2016](../../sql-server/install/hardware-and-software-requirements-for-installing-sql-server-2016.md#TOP_Principal)  
  
-   [Breiteneditionen von SQL Server 2016](../../sql-server/install/hardware-and-software-requirements-for-installing-sql-server-2016.md#TOP_Breadth)  
  
> [!NOTE]  
>  Ausnahmen für die Betriebssystemunterstützung, die in diesem Abschnitt erwähnt wurden, sind die folgenden Business Intelligence-Funktionen, die auf Windows Server 2008 R2 SP1 oder höher installiert werden können.  
  
-   [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] – SharePoint  
  
-   [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]-Add-In für SharePoint-Produkte  
  
### <a name="features-supported-on-32-bit-client-operating-systems"></a>Unterstützte Funktionen auf 32-Bit-Clientbetriebssystemen  
 Windows-Clientbetriebssystemen, z.B. Windows 10 und Windows 8.1, sind als 32-Bit- oder 64-Bit-Architekturen verfügbar.   Alle SQL Server-Funktionen werden auf 64-Bit-Clientbetriebssystemen unterstützt. Microsoft unterstützt auf 32-Bit-Clientbetriebssystemen die folgenden Funktionen:  
  
-   Data Quality Client  
  
-   Konnektivität der Clienttools  
  
-   Integration Services  
  
-   Abwärtskompatibilität der Clienttools  
  
-   Clienttools SDK  
  
-   Dokumentationskomponenten  
  
-   Distributed Replay-Komponenten  
  
-   Distributed Replay Controller  
  
-   Distributed Replay Client  
  
-   SQL Client Connectivity SDK  
  
 [!INCLUDE[winserver2008r2](../../includes/winserver2008r2-md.md)] und höhere Server-Betriebssysteme sind nicht als 32-Bit-Architektur verfügbar. Alle unterstützten Serverbetriebssysteme sind nur als 64-Bit verfügbar. Alle Funktionen werden auf 64-Bit-Serverbetriebssystemen unterstützt.  
  
###  <a name="a-nametopprincipala-principal-editions-of-includesscurrenttokensscurrentmdmd"></a><a name="TOP_Principal"></a> Prinzipaleditionen von [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]  
 In der folgenden Tabelle werden die Betriebssystemanforderungen für die Prinzipaleditionen von [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]angezeigt:  
  
|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Edition|Unterstützte Betriebssysteme|  
|---------------------------------------|--------------------------------|  
|[!INCLUDE[ssEnterprise](../../includes/ssenterprise-md.md)]|[!INCLUDE[winserver2016_datacenter_md](../../includes/winserver2016-datacenter-md.md)]<br/><br/>[!INCLUDE[winserver2016_standard_md](../../includes/winserver2016-standard-md.md)]<br/><br/>[!INCLUDE[win8srv](../../includes/win8srv-md.md)] R2 Datacenter<br/><br/>[!INCLUDE[win8srv](../../includes/win8srv-md.md)]R2 Standard<br/><br/>[!INCLUDE[win8srv](../../includes/win8srv-md.md)]R2 Essentials<br/><br/>[!INCLUDE[win8srv](../../includes/win8srv-md.md)]R2 Foundation<br/><br/>[!INCLUDE[win8srv](../../includes/win8srv-md.md)] Datacenter<br/><br/>[!INCLUDE[win8srv](../../includes/win8srv-md.md)] Standard<br/><br/>[!INCLUDE[win8srv](../../includes/win8srv-md.md)] Essentials<br/><br/>[!INCLUDE[win8srv](../../includes/win8srv-md.md)] Foundation|  
|[!INCLUDE[ssStandard](../../includes/ssstandard-md.md)]|[!INCLUDE[winserver2016_datacenter_md](../../includes/winserver2016-datacenter-md.md)]<br/><br/>[!INCLUDE[winserver2016_standard_md](../../includes/winserver2016-standard-md.md)]<br/><br/>[!INCLUDE[win8srv](../../includes/win8srv-md.md)] R2 Datacenter<br/><br/>[!INCLUDE[win8srv](../../includes/win8srv-md.md)]R2 Standard<br/><br/>[!INCLUDE[win8srv](../../includes/win8srv-md.md)]R2 Essentials<br/><br/>[!INCLUDE[win8srv](../../includes/win8srv-md.md)]R2 Foundation<br/><br/>[!INCLUDE[win8srv](../../includes/win8srv-md.md)] Datacenter<br/><br/>[!INCLUDE[win8srv](../../includes/win8srv-md.md)] Standard<br/><br/>[!INCLUDE[win8srv](../../includes/win8srv-md.md)] Essentials<br/><br/>[!INCLUDE[win8srv](../../includes/win8srv-md.md)] Foundation<br/><br/> Windows 10 Home<br/><br/> Windows 10 Professional<br/><br/> Windows 10 Enterprise<br/><br/>[!INCLUDE[winblue_client_2](../../includes/winblue-client-2-md.md)]<br/><br/>[!INCLUDE[winblue_client_pro_2](../../includes/winblue-client-pro-2-md.md)]<br/><br/>[!INCLUDE[winblue_client_ent_2](../../includes/winblue-client-ent-2-md.md)]<br/><br/>[!INCLUDE[win8](../../includes/win8-md.md)]<br/><br/>[!INCLUDE[win8_client_pro_2](../../includes/win8-client-pro-2-md.md)]<br/><br/>[!INCLUDE[win8_client_ent_2](../../includes/win8-client-ent-2-md.md)]|  
|[!INCLUDE[ssWeb](../../includes/ssweb-md.md)]|[!INCLUDE[winserver2016_datacenter_md](../../includes/winserver2016-datacenter-md.md)]<br/><br/>[!INCLUDE[winserver2016_standard_md](../../includes/winserver2016-standard-md.md)]<br/><br/>[!INCLUDE[win8srv](../../includes/win8srv-md.md)] R2 Datacenter<br/><br/>[!INCLUDE[win8srv](../../includes/win8srv-md.md)]R2 Standard<br/><br/>[!INCLUDE[win8srv](../../includes/win8srv-md.md)]R2 Essentials<br/><br/>[!INCLUDE[win8srv](../../includes/win8srv-md.md)]R2 Foundation<br/><br/>[!INCLUDE[win8srv](../../includes/win8srv-md.md)] Datacenter<br/><br/>[!INCLUDE[win8srv](../../includes/win8srv-md.md)] Standard<br/><br/>[!INCLUDE[win8srv](../../includes/win8srv-md.md)] Essentials<br/><br/>[!INCLUDE[win8srv](../../includes/win8srv-md.md)] Foundation|  
  
###  <a name="a-nametopbreadtha-breadth-editions-of-includesscurrenttokensscurrentmdmd"></a><a name="TOP_Breadth"></a> Breiteneditionen von [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]  
 In der folgenden Tabelle werden die Betriebssystemanforderungen für die Breiteneditionen von [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]angezeigt:  
  
|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Edition|Unterstützte Betriebssysteme|  
|---------------------------------------|--------------------------------|  
|[!INCLUDE[ssDeveloper](../../includes/ssdeveloper-md.md)]|[!INCLUDE[winserver2016_datacenter_md](../../includes/winserver2016-datacenter-md.md)]<br/><br/>[!INCLUDE[winserver2016_standard_md](../../includes/winserver2016-standard-md.md)]<br/><br/>[!INCLUDE[win8srv](../../includes/win8srv-md.md)] R2 Datacenter<br/><br/>[!INCLUDE[win8srv](../../includes/win8srv-md.md)]R2 Standard<br/><br/>[!INCLUDE[win8srv](../../includes/win8srv-md.md)]R2 Essentials<br/><br/>[!INCLUDE[win8srv](../../includes/win8srv-md.md)]R2 Foundation<br/><br/>[!INCLUDE[win8srv](../../includes/win8srv-md.md)] Datacenter<br/><br/>[!INCLUDE[win8srv](../../includes/win8srv-md.md)] Standard<br/><br/>[!INCLUDE[win8srv](../../includes/win8srv-md.md)] Essentials<br/><br/>[!INCLUDE[win8srv](../../includes/win8srv-md.md)] Foundation<br/><br/> Windows 10 Home<br/><br/> Windows 10 Professional<br/><br/> Windows 10 Enterprise<br/><br/>[!INCLUDE[winblue_client_2](../../includes/winblue-client-2-md.md)]<br/><br/>[!INCLUDE[winblue_client_pro_2](../../includes/winblue-client-pro-2-md.md)]<br/><br/>[!INCLUDE[winblue_client_ent_2](../../includes/winblue-client-ent-2-md.md)]<br/><br/>[!INCLUDE[win8](../../includes/win8-md.md)]<br/><br/>[!INCLUDE[win8_client_pro_2](../../includes/win8-client-pro-2-md.md)]<br/><br/>[!INCLUDE[win8_client_ent_2](../../includes/win8-client-ent-2-md.md)]|  
|[!INCLUDE[ssExpress](../../includes/ssexpress-md.md)]|[!INCLUDE[winserver2016_datacenter_md](../../includes/winserver2016-datacenter-md.md)]<br/><br/>[!INCLUDE[winserver2016_standard_md](../../includes/winserver2016-standard-md.md)]<br/><br/>[!INCLUDE[win8srv](../../includes/win8srv-md.md)] R2 Datacenter<br/><br/>[!INCLUDE[win8srv](../../includes/win8srv-md.md)]R2 Standard<br/><br/>[!INCLUDE[win8srv](../../includes/win8srv-md.md)]R2 Essentials<br/><br/>[!INCLUDE[win8srv](../../includes/win8srv-md.md)]R2 Foundation<br/><br/>[!INCLUDE[win8srv](../../includes/win8srv-md.md)] Datacenter<br/><br/>[!INCLUDE[win8srv](../../includes/win8srv-md.md)] Standard<br/><br/>[!INCLUDE[win8srv](../../includes/win8srv-md.md)] Essentials<br/><br/>[!INCLUDE[win8srv](../../includes/win8srv-md.md)] Foundation<br/><br/> Windows 10 Home<br/><br/> Windows 10 Professional<br/><br/> Windows 10 Enterprise<br/><br/>[!INCLUDE[winblue_client_2](../../includes/winblue-client-2-md.md)]<br/><br/>[!INCLUDE[winblue_client_pro_2](../../includes/winblue-client-pro-2-md.md)]<br/><br/>[!INCLUDE[winblue_client_ent_2](../../includes/winblue-client-ent-2-md.md)]<br/><br/>[!INCLUDE[win8](../../includes/win8-md.md)]<br/><br/>[!INCLUDE[win8_client_pro_2](../../includes/win8-client-pro-2-md.md)]<br/><br/>[!INCLUDE[win8_client_ent_2](../../includes/win8-client-ent-2-md.md)]|  
  
##  <a name="a-namecrosslanguagesupporta-cross-language-support"></a><a name="CrossLanguageSupport"></a> Sprachübergreifende Unterstützung  
 Weitere Informationen zu sprachübergreifender Unterstützung und Überlegungen zur Installation von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] in lokalisierten Sprachen finden Sie unter [Lokale Sprachversionen in SQL Server](../../sql-server/install/local-language-versions-in-sql-server.md).  
  
##  <a name="a-nameharddiskspacea-hard-disk-space-requirements"></a><a name="HardDiskSpace"></a> Anforderungen an den Festplattenspeicherplatz  
 Während der Installation von [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]erstellt Windows Installer temporäre Dateien auf dem Systemlaufwerk. Überprüfen Sie, ob Sie über mindestens 6,0 GB freien Speicherplatz auf dem Systemlaufwerk für diese Dateien verfügen, bevor Sie Setup ausführen, um [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]zu installieren oder zu aktualisieren. Diese Anforderung gilt auch dann, wenn Sie Komponenten von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] auf einem Nichtstandard-Laufwerk installieren.  
  
 Die tatsächlichen Anforderungen für den Festplattenspeicherplatz basieren auf der Systemkonfiguration und den Funktionen, die Sie installieren möchten. In der folgenden Tabelle sind die Speicherplatzanforderungen für die Komponenten von [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] aufgeführt.  
  
|**Feature**|**Erforderlicher Speicherplatz**|  
|-----------------|--------------------------------|  
|[!INCLUDE[ssDE](../../includes/ssde-md.md)] und Datendateien, Replikation, Volltextsuche und Data Quality Services|1480 MB|  
|[!INCLUDE[ssDE](../../includes/ssde-md.md)] (wie oben beschrieben) mit R-Services (datenbankintern)|2744 MB|  
|[!INCLUDE[ssDE](../../includes/ssde-md.md)] (wie oben beschrieben) mit dem PolyBase-Abfragedienst für externe Daten|4194 MB|  
|[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] und Datendateien|698 MB|  
|[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]|967 MB|  
|[!INCLUDE[rsql_platform](../../includes/rsql-platform-md.md)] (Eigenständig)|280 MB|  
|[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] – SharePoint|1203 MB|  
|[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]-Add-In für SharePoint-Produkte|325 MB|  
|[!INCLUDE[ssDQSClient](../../includes/ssdqsclient-md.md)]|121 MB|  
|Konnektivität der Clienttools|328 MB|  
|[!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]|306 MB|  
|Clientkomponenten (außer [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Onlinedokumentation und Integration Services-Tools)|445 MB|  
|[!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)]|280 MB|  
|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Onlinedokumentation zum Anzeigen und Verwalten von Hilfeinhalten*|27 MB|  
|Alle Funktionen|8030 MB|  
  
 *Die Onlinedokumentation erfordert 200 MB Festplattenspeicherplatz.  
  
##  <a name="a-namestoragetypesa-storage-types-for-data-files"></a><a name="StorageTypes"></a> Speichertypen für Datendateien  
 Für Datendateien werden folgende Speichertypen unterstützt:  
  
-   Lokaler Datenträger  
  
-   Freigegebener Speicher  
  
-   SMB-Dateifreigabe  
  
    > [!NOTE]  
    >  Der SMB-Speicher wird bei eigenständigen oder gruppierten Installationen nicht für [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] -Datendateien unterstützt. Verwenden Sie stattdessen den direkt angeschlossenen Speicher oder ein SAN (Storage Area Network).  
  
    > [!IMPORTANT]  
    >  Der SMB-Speicher kann von einem Windows File Server oder einem SMB-Speichergerät eines Drittanbieters gehostet werden. Bei Verwendung von Windows File Server sollte die Windows File Server-Version 2008 oder höher verwendet werden. Weitere Informationen zum Installieren von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] mit SMB-Dateifreigabe als Speicheroption finden Sie unter [Install SQL Server with SMB Fileshare as a Storage Option](../../database-engine/install-windows/install-sql-server-with-smb-fileshare-as-a-storage-option.md)aufgeführt.  
  
    > [!WARNING]  
    > Bei der  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Failoverclusterinstallation wird nur der lokale Datenträger zum Installieren der tempdb-Dateien unterstützt. Stellen Sie sicher, dass der für die tempdb-Daten und die Protokolldateien angegebene Pfad auf allen Clusterknoten gültig ist. Sind die tempdb-Verzeichnisse auf dem Failoverzielknoten während des Failovers nicht verfügbar, wird die [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Ressource nicht online geschaltet.  
  
##  <a name="a-namedcsupporta-installing-includessnoversiontokenssnoversionmdmd-on-a-domain-controller"></a><a name="DC_support"></a>Installieren von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] auf einem Domänencontroller  
 Aus Sicherheitsgründen sollte [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] nicht auf einem Domänencontroller installiert werden. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Setup blockiert die Installation auf einem Computer, der als Domänencontroller fungiert, nicht, es gelten jedoch die folgenden Einschränkungen:  
  
-   Sie können keine [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Dienste auf einem Domänencontroller unter einem lokalen Dienstkonto ausführen.  
  
-   Nachdem [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] auf einem Computer installiert wurde, können Sie den Computer nicht von einem Domänenmitglied zu einem Domänencontroller ändern. Sie müssen [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] deinstallieren, bevor Sie den Hostcomputer zu einem Domänencontroller ändern.  
  
-   Nachdem [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] auf einem Computer installiert wurde, können Sie den Computer nicht von einem Domänencontroller zu einem Domänenmitglied ändern. Sie müssen [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] deinstallieren, bevor Sie den Hostcomputer zu einem Domänenmitglied ändern.  
  
-   [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] werden nicht unterstützt, wenn es sich bei den Clusterknoten um Domänencontroller handelt.  
  
- [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] wird auf einem schreibgeschützten Domänencontroller nicht unterstützt. Beim Setup von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] können keine Sicherheitsgruppen erstellt oder [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Dienstkonten für einen schreibgeschützten Domänencontroller bereitgestellt werden. In diesem Szenario tritt ein Setupfehler auf.  

- Eine Failoverclusterinstanz von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] wird in einer Umgebung nicht unterstützt, in der nur auf einen schreibgeschützten Domänencontroller zugegriffen werden kann. 
  
## <a name="see-also"></a>Siehe auch  
 [Planen einer SQL Server-Installation](../../sql-server/install/planning-a-sql-server-installation.md)   
 [Überlegungen zur Sicherheit bei SQL Server-Installationen](../../sql-server/install/security-considerations-for-a-sql-server-installation.md)   
 [Produktspezifikationen für SQL Server 2016](../Topic/Product%20Specifications%20for%20SQL%20Server%202016.md)  
  
  