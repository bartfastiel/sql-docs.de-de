---
title: "Installieren von SQL Server 2016-Wartungsupdates | Microsoft Docs"
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
ms.assetid: 7d6c962b-c8d0-49f7-a2ac-00ad8dca930a
caps.latest.revision: 13
ms.author: "mikeray"
manager: "jhubbard"
---
# Installieren von SQL Server 2016-Wartungsupdates
  Dieses Thema enthält Informationen zum Installieren von Updates für [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]. In diesem Abschnitt finden Sie Informationen zu den folgenden Themen:  
  
-   Installieren von Updates für [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] während einer neuen Installation  
  
-   Installieren von Updates für [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)], nachdem es bereits installiert wurde.  
  
 Es empfiehlt sich, dass Kunden neue [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Updates zeitnah bewerten und installieren, um sicherzustellen, dass Systeme mit den letzten Sicherheitsupdates aktualisiert wurden.  
  
## Installieren von Updates für [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] während einer neuen Installation  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Setup integriert die neuesten Produktupdates in die Installation des Hauptprodukts, sodass das Hauptprodukt und geeignete Updates gleichzeitig installiert werden. Das Produktupdate kann an folgenden Orten nach anwendbaren Updates suchen:  
  
-   [!INCLUDE[msCoName](../../includes/msconame-md.md)] Update  
  
-   Windows Server Update Services (WSUS)  
  
-   Ein lokaler Ordner  
  
-   Eine Netzwerkfreigabe  
  
 Nachdem Setup die neuesten Versionen der anwendbaren Updates gefunden hat, lädt es diese herunter und integriert sie in den aktuellen [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Installationsvorgang. Produktupdate kann ein kumulatives Update, Service Pack oder Service Pack plus kumulatives Update enthalten.  
  
## Installieren von Updates für [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)], nachdem es bereits installiert wurde  
 Auf einer installierten Instanz von [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] empfiehlt es sich, dass Sie die letzten Sicherheitsupdates und wichtige Updates einschließlich allgemeiner Verteilungsversionen (GDRs), Service Packs (SPS) und kumulativer Updates anwenden. Weitere Informationen finden Sie in der [Ankündigung zum SQL Server Incremental Servicing Model (ISM) aus März 2016](http://blogs.msdn.microsoft.com/sqlreleaseservices/announcing-updates-to-the-sql-server-incremental-servicing-model-ism/). 
  
 Die [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Updates sind über [!INCLUDE[msCoName](../../includes/msconame-md.md)] Update (MU), Windows Server Update Services (WSUS) und das Microsoft Download Center verfügbar. Sicherheits- und wichtige Updates für [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] sind über [!INCLUDE[msCoName](../../includes/msconame-md.md)] Update verfügbar. Um diese Updates sehen zu können, müssen Sie sich in MU durch das Windows Update-Applet in der Systemsteuerung anmelden.  
  
 Wenn Sie über [!INCLUDE[msCoName](../../includes/msconame-md.md)] Update ein Update empfangen, aktualisiert es alle [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Funktionen im unbeaufsichtigten Modus auf die neueste Version. Wenn Sie mehr Flexibilität benötigen oder keinen Internet oder WSUS-Zugriff haben, müssen Sie die Updates vom [!INCLUDE[msCoName](../../includes/msconame-md.md)] Download Center abrufen.  
  
## Siehe auch  
 [Installieren von SQL Server 2016 vom Installations-Assistenten aus &#40;Setup&#41;](../../database-engine/install-windows/install-sql-server-2016-from-the-installation-wizard-setup.md)   
 [Hinzufügen von Funktionen zu einer Instanz von SQL Server 2016 &#40;Setup&#41;](../../database-engine/install-windows/add-features-to-an-instance-of-sql-server-2016-setup.md)   
 [Reparieren von Fehlern bei einer SQL Server 2016-Installation](../../database-engine/install-windows/repair-a-failed-sql-server-2016-installation.md)  
  
  