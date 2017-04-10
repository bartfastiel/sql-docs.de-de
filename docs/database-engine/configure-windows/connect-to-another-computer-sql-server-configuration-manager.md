---
title: "Herstellen einer Verbindung mit einem anderen Computer (SQL Server-Konfigurations-Manager) | Microsoft Docs"
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
  - "Verbindungen [SQL Server], andere Computer"
ms.assetid: c4c1e94f-4f5f-431e-8b5b-d5ff97baf723
caps.latest.revision: 40
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
---
# Herstellen einer Verbindung mit einem anderen Computer (SQL Server-Konfigurations-Manager)
  In diesem Thema wird beschrieben, wie Sie in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] eine Verbindung mit einem anderen Computer herstellen können. Befolgen Sie die erste Prozedur, um die Computerverwaltung von Windows, MMC ([!INCLUDE[msCoName](../../includes/msconame-md.md)] Management Console) zu öffnen, stellen Sie eine Verbindung zu dem Computer her, und erweitern die Struktur "Dienste und Anwendungen". Führen Sie das zweite Verfahren zum Erstellen einer Datei mit einem Link zum [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Konfigurations-Manager auf einem Remotecomputer aus.  
  
> [!NOTE]  
>  Bei einer Remoteverbindung können einige Aktionen nicht von Configuration Manager ausgeführt werden.  
  
 Zum Starten, Stoppen, Anhalten oder Fortsetzen von Diensten auf einem anderen Computer können Sie auch mit [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] eine Verbindung zu dem Server herstellen, mit der rechten Maustaste auf den Server oder den [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Agent und anschließend auf die gewünschte Aktion klicken.  
  
##  <a name="SSMSProcedure"></a>  
  
#### So stellen Sie eine Verbindung mit einem anderen Computer mit der Computerverwaltung von Windows her  
  
1.  Klicken Sie im Menü **Start** mit der rechten Maustaste auf **Arbeitsplatz**, und klicken Sie dann auf **Verwalten**.  
  
2.  Klicken Sie in **Computerverwaltung** mit der rechten Maustaste auf **Computerverwaltung (lokal)**, und klicken Sie dann auf **Verbindung mit anderem Computer herstellen**.  
  
3.  Geben Sie im Dialogfeld **Computer auswählen** in das Textfeld **Anderen Computer** den Namen des Computers ein, den Sie verwalten möchten, und klicken Sie dann auf **OK**.  
  
     Die Computerverwaltung zeigt die Dienste an, die auf dem Remotecomputer ausgeführt werden. Der Knoten der obersten Ebene wird in **Computerverwaltung** \<*Remotecomputer*> geändert.  
  
4.  Erweitern Sie in der Konsolenstruktur **Dienste und Anwendungen**, und erweitern Sie dann **SQL Server-Konfigurations-Manager** , um die Dienste des Remotecomputers zu verwalten.  
  
#### So sichern Sie einen Link zu SQL Server-Konfigurations-Manager für einen anderen Computer  
  
1.  Klicken Sie im Menü **Start** auf **Ausführen**.  
  
2.  Geben Sie im Feld **Öffnen** die Zeichenfolge **mmc -a** ein, um die [!INCLUDE[msCoName](../../includes/msconame-md.md)] Management Console im Autorenmodus zu öffnen.  
  
3.  Klicken Sie im Menü **Datei** auf **Snap-In hinzufügen/entfernen**.  
  
4.  Klicken Sie im Fenster **Snap-In hinzufügen/entfernen** auf **Hinzufügen**.  
  
5.  Klicken Sie im Dialogfeld **Eigenständiges Snap-In hinzufügen** auf **Computerverwaltung**, und klicken Sie dann auf **Hinzufügen**.  
  
6.  Klicken Sie im Dialogfeld **Computerverwaltung** auf **Anderen Computer**, geben Sie den Namen des zu verwaltenden Remotecomputers ein, und klicken Sie dann auf **Fertig stellen**.  
  
7.  Klicken Sie im Dialogfeld **Eigenständiges Snap-In hinzufügen** auf **Schließen**.  
  
8.  Klicken Sie im Fenster **Snap-In hinzufügen/entfernen** auf **OK**.  
  
9. Erweitern Sie **Computerverwaltung (***\<Computername>***)** und **Dienste und Anwendungen**.  
  
10. Klicken Sie mit der rechten Maustaste auf **SQL Server-Konfigurations-Manager**, und klicken Sie dann auf **Neues Fenster**.  
  
11. Klicken Sie im Menü **Fenster** auf **Konsolenstamm**, um zum ersten Fenster zurückzuwechseln, und löschen Sie das Fenster.  
  
12. Klicken Sie im Menü **Datei** auf **Speichern unter**, und speichern Sie die Datei im gewünschten Ordner. Geben Sie der Datei dabei einen passenden Namen mit der Erweiterung **.msc** . Schließen Sie das Fenster [!INCLUDE[msCoName](../../includes/msconame-md.md)] Management Console.  
  
13. Doppelklicken Sie auf die Datei, um [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Konfigurations-Manager auf dem Zielcomputer zu öffnen. Speichern Sie gegebenenfalls einen Link zu der Datei auf dem Desktop oder im Menü **Start** .  
  
> [!CAUTION]  
>  Wenn Sie [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Konfigurations-Manager auf einem Remotecomputer verwenden, ist der Computername nicht offensichtlich, und es ist möglich, versehentlich den falschen Computer zu stoppen oder zu konfigurieren. Überprüfen Sie auf der Registerkarte **Dienst** das Feld **Hostname** , um den Computernamen zu überprüfen, bevor Sie einen Dienst ändern.  
  
## Siehe auch  
 [Konfigurieren von WMI zum Anzeigen des Serverstatus in SQL Server-Tools](../../ssms/configure-wmi-to-show-server-status-in-sql-server-tools.md)  
  
  