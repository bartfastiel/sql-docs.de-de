---
title: "Sicherungs- und Wiederherstellungsvorg&#228;nge f&#252;r Reporting Services | Microsoft Docs"
ms.custom: ""
ms.date: "03/18/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "reporting-services-native"
  - "reporting-services-sharepoint"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Datenbanken [Reporting Services], sichern"
  - "Datenbanken [Reporting Services], wiederherstellen"
  - "Datenbanken [Reporting Services], verschieben"
  - "Sichern von Datenbanken [Reporting Services]"
  - "Verschieben von Datenbanken"
  - "Wiederherstellen von Datenbanken [Reporting Services]"
  - "Dateien [Reporting Services], wiederherstellen"
  - "Dateien [Reporting Services], sichern"
ms.assetid: 157bc376-ab72-4c99-8bde-7b12db70843a
caps.latest.revision: 43
author: "guyinacube"
ms.author: "asaxton"
manager: "erikre"
caps.handback.revision: 43
---
# Sicherungs- und Wiederherstellungsvorg&#228;nge f&#252;r Reporting Services
  Dieses Thema bietet eine Übersicht über alle Datendateien, die in einer [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] -Installation verwendet werden. Zudem wird beschrieben, wann und auf welche Weise Sicherungskopien für die Dateien erstellt werden sollten. Das Entwickeln eines Sicherungs- und Wiederherstellungsplans für die Berichtsserver-Datenbankdateien stellt den wichtigsten Teil einer Wiederherstellungsstrategie dar. Eine umfassendere Wiederherstellungsstrategie würde jedoch Sicherungen der Verschlüsselungsschlüssel, der benutzerdefinierten Assemblys oder Erweiterungen, der Konfigurationsdateien und der Quelldateien für Berichte und Modelle einschließen.  
  
 **[!INCLUDE[applies](../../includes/applies-md.md)]**  [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] Einheitlicher Modus | [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] SharePoint-Modus  
  
 Sicherungs- und Wiederherstellungsvorgänge werden häufig zum Verschieben einer gesamten [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]-Installation oder eines Teils derselben verwendet:  
  
-   Wenn Sie nur die Berichtsserver-Datenbanken verschieben, können Sie Sichern und Wiederherstellen oder Anfügen und Trennen verwenden, um die Datenbanken in eine andere [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Instanz zu verschieben. Weitere Informationen finden Sie unter [Verschieben von Berichtsserver-Datenbanken auf einen anderen Computer &#40;einheitlicher SSRS-Modus&#41;](../../reporting-services/report-server/moving-the-report-server-databases-to-another-computer-ssrs-native-mode.md).  
  
-   Das Verschieben einer [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]-Installation auf einen neuen Computer wird als Migration bezeichnet. Wenn Sie eine Installation migrieren, führen Sie Setup aus, um eine neue Berichtsserverinstanz zu installieren, und kopieren Sie anschließend die Instanzdaten auf den neuen Computer. Weitere Informationen zum Migrieren einer [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]-Installation finden Sie unter den folgenden Themen:  
  
    -   [Aktualisieren und Migrieren von Reporting Services](../../reporting-services/install-windows/upgrade-and-migrate-reporting-services.md)  
  
    -   [Migrieren einer Installation von Reporting Services &#40;SharePoint Modus&#41;](../../reporting-services/install-windows/migrate-a-reporting-services-installation-sharepoint-mode.md)  
  
    -   [Migrieren einer Reporting Services-Installation &#40;einheitlicher Modus&#41;](../../reporting-services/install-windows/migrate-a-reporting-services-installation-native-mode.md)  
  
## Sichern der Berichtsserver-Datenbanken  
 Da es sich bei einem Berichtsserver um einen statuslosen Server handelt, werden alle Anwendungsdaten in den Datenbanken **reportserver** und **reportservertempdb** gespeichert, die in einer [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] -Instanz ausgeführt werden. Mithilfe einer der zum Sichern von **-Datenbanken unterstützten Methoden können Sie die Datenbanken** reportserver **und** reportservertempdb [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] sichern. Speziell für die Berichtsserver-Datenbanken gelten die folgenden Empfehlungen:  
  
-   Verwenden Sie zum Sichern der **reportserver** -Datenbank das Modell der vollständigen Wiederherstellung.  
  
-   Verwenden Sie zum Sichern der **reportservertempdb** -Datenbank das einfache Wiederherstellungsmodell.  
  
-   Die Sicherungszeitpläne für die beiden Datenbanken sollten sich voneinander unterscheiden. Der einzige Grund für das Sichern der **reportservertempdb** -Datenbank besteht darin, sie nach einem Hardwarefehler nicht erneut erstellen zu müssen. Wenn ein Hardwarefehler auftritt, ist es nicht nötig, die Daten in **reportservertempdb**wiederherzustellen, Sie benötigen jedoch die Tabellenstruktur. Wenn Sie **reportservertempdb**verlieren, können Sie sie nur zurückbekommen, indem Sie die Berichtsserver-Datenbank erneut erstellen. Wenn Sie **reportservertempdb**neu erstellen, ist es wichtig, dass sie denselben Namen wie die primäre Berichtsserver-Datenbank aufweist.  
  
 Weitere Informationen zur Sicherung und Wiederherstellung von relationalen [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Datenbanken finden Sie unter [Sichern und Wiederherstellen von SQL Server-Datenbanken](../../relational-databases/backup-restore/back-up-and-restore-of-sql-server-databases.md).  
  
> [!IMPORTANT]  
>  Wenn sich der [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]-Berichtsserver im SharePoint-Modus befindet, muss er mit zusätzlichen Datenbanken verbunden werden, u. a. den SharePoint-Konfigurationsdatenbanken und der [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]-Warnungsdatenbank. Im SharePoint-Modus werden drei Datenbanken für jede [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] -Dienstanwendung erstellt: **reportserver**, **reportservertempdb**und **dataalerting** . Weitere Informationen finden Sie unter [Sichern und Wiederherstellen von Reporting Services-SharePoint-Dienstanwendungen](../../reporting-services/report-server-sharepoint/backup-and-restore-reporting-services-sharepoint-service-applications.md).  
  
## Sichern der Verschlüsselungsschlüssel  
 Sie sollten die Verschlüsselungsschlüssel sichern, wenn Sie eine [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] -Installation zum ersten Mal konfigurieren. Sie sollen die Schlüssel zudem jedes Mal sichern, wenn Sie die Identität der Dienstkonten ändern oder den Computer umbenennen. Weitere Informationen finden Sie unter [Back Up and Restore Reporting Services Encryption Keys](../../reporting-services/install-windows/back-up-and-restore-reporting-services-encryption-keys.md). Weitere Informationen zu Berichtsservern im SharePoint-Modus finden Sie im Abschnitt „Schlüsselverwaltung“ des Artikels [Verwalten einer Reporting Services-SharePoint-Dienstanwendung](../../reporting-services/report-server-sharepoint/manage-a-reporting-services-sharepoint-service-application.md).  
  
## Sichern der Konfigurationsdateien  
 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] werden Anwendungseinstellungen in Konfigurationsdateien gespeichert. Sie sollten die Dateien sichern, wenn Sie den Server erstmalig konfigurieren und nachdem Sie benutzerdefinierte Erweiterungen bereitgestellt haben. Folgende Dateien müssen gesichert werden:  
  
-   Rsreportserver.config  
  
-   Rssvrpolicy.config  
  
-   Rsmgrpolicy.config  
  
-   Reportingservicesservice.exe.config  
  
-   Web.config für die beiden [!INCLUDE[vstecasp](../../includes/vstecasp-md.md)] -Anwendungen Berichtsserver und Berichts-Manager.  
  
-   Machine.config für [!INCLUDE[vstecasp](../../includes/vstecasp-md.md)]  
  
## Sichern von Datendateien  
 Sichern Sie die im Berichts-Designer und Modell-Designer erstellten und verwalteten Dateien. Diese umfassen Berichtsdefinitionsdateien (RDL), Berichtsmodelldateien (SMDL), freigegebene Datenquellendateien (RDS), Datenansichtsdateien (DV), Datenquellendateien (DS), Berichtsserver-Projektdateien (RPTPROJ) und Berichtsprojektmappen-Dateien (SLN).  
  
 Sichern Sie alle Skriptdateien (RSS), die Sie für Verwaltungs- oder Bereitstellungsaufgaben erstellt haben.  
  
 Stellen Sie sicher, dass Sie eine Sicherungskopie aller verwendeten benutzerdefinierten Erweiterungen und benutzerdefinierten Assemblys haben.  
  
## Siehe auch  
 [Berichtsserver-Datenbank &#40;einheitlicher SSRS-Modus&#41;](../../reporting-services/report-server/report-server-database-ssrs-native-mode.md)   
 [Reporting Services-Konfigurationsdateien](../../reporting-services/report-server/reporting-services-configuration-files.md)   
 [rskeymgmt-Hilfsprogramm &#40;SSRS&#41;](../../reporting-services/tools/rskeymgmt-utility-ssrs.md)   
 [Kopieren von Datenbanken durch Sichern und Wiederherstellen](../../relational-databases/databases/copy-databases-with-backup-and-restore.md)   
 [Verwalten einer Berichtsserver-Datenbank &#40;einheitlicher SSRS-Modus&#41;](../../reporting-services/report-server/administer-a-report-server-database-ssrs-native-mode.md)   
 [Konfigurieren und Verwalten von Verschlüsselungsschlüsseln &#40;SSRS-Konfigurations-Manager&#41;](../../reporting-services/install-windows/configure-and-manage-encryption-keys-ssrs-configuration-manager.md)  
  
  