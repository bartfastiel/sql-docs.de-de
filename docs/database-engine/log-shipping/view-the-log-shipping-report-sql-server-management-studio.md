---
title: "Anzeigen des Protokollversandberichts (SQL Server Management Studio) | Microsoft Docs"
ms.custom: ""
ms.date: "03/04/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dbe-high-availability"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Anzeigen von Protokollversandberichten"
  - "Anzeigen von Protokollversandberichten"
  - "Protokollversand [SQL Server], überwachen"
  - "Protokollversand [SQL Server], Anzeigen von Berichten"
ms.assetid: 3b549f2f-3683-45e5-b8e8-8095276c41ab
caps.latest.revision: 18
author: "MikeRayMSFT"
ms.author: "mikeray"
manager: "jhubbard"
caps.handback.revision: 18
---
# Anzeigen des Protokollversandberichts (SQL Server Management Studio)
  In diesem Thema wird erklärt, wie Sie den Transaktionsprotokoll-Versandstatus-Bericht in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]anzeigen. Sie können einen Statusbericht auf einem Überwachungsserver, einem primären Server oder einem sekundären Server ausführen. Wenn die Informationen zu Ihrer Protokollversandkonfiguration möglichst lückenlos angezeigt werden sollen, sollten Sie den Bericht auf der Überwachungsserverinstanz anzeigen.  
  
 Der Bericht zeigt den Status sämtlicher Protokollversandaktivitäten an, die auf der verbundenen Serverinstanz verfügbar sind. Wenn diese Serverinstanz an mehreren Konfigurationen in verschiedenen Rollen beteiligt ist (z. B. wenn sie für eine Datenbank als Überwachungsserver und für eine andere Datenbank als sekundärer Server dient), enthalten die angezeigten Ergebnisse Informationen zu jeder Konfiguration aus der Perspektive der jeweiligen Rolle. Wenn die gespeicherte Prozedur für eine bestimmte Protokollversandkonfiguration eine Verbindung mit der Überwachungsserverinstanz herstellen kann, zeigt der Bericht zusätzliche Statusinformationen für diese Konfiguration an.  
  
 Sie können für jede Rolle, die von der aktuellen Serverinstanz übernommen wird, folgende Informationen anzeigen:  
  
|Rolle|Angezeigte Informationen|  
|----------|---------------------------|  
|Monitor|Name und Status jedes primären Servers und sekundären Servers, der diese Serverinstanz als seinen Überwachungsserver verwendet.|  
|Primär|Für jede primäre Datenbank wird der Status und der Name der aktuellen Serverinstanz (als primärer Server) zusammen mit dem Namen der primären Datenbank angezeigt. Der Bericht zeigt den Status des Sicherungsauftrags an (der lokal auf dem primären Server gespeichert ist).<br /><br /> Der Bericht enthält auch eine Zeile für jeden der entsprechenden sekundären Server. Falls die Konfiguration einen Überwachungsserver verwendet und die gespeicherte Prozedur eine Verbindung mit dem Überwachungsserver herstellen kann, wird in diesen Zeilen der Kopierstatus und der Wiederherstellungsstatus für die letzte Protokollsicherung angezeigt.|  
|Secondary|Für jede sekundäre Datenbank wird der Status und der Name der aktuellen Serverinstanz (als sekundärer Server) zusammen mit dem Namen der sekundären Datenbank angezeigt.<br /><br /> Der Bericht zeigt den Status der Kopier- und Wiederherstellungsaufträge auf dem sekundären Server an.<br /><br /> Der Bericht enthält auch eine Zeile für den entsprechenden primären Server. Falls die Konfiguration einen Überwachungsserver verwendet und die gespeicherte Prozedur eine Verbindung mit dem Überwachungsserver herstellen kann, wird in dieser Zeile der Status der letzten Protokollsicherung angezeigt.|  
  
 Welche Informationen angezeigt werden, hängt davon ab, ob es sich bei der Serverinstanz um einen Überwachungsserver, einen primären Server oder einen sekundären Server handelt. Falls keine Informationen verfügbar sind, sind die entsprechenden Zellen ausgegraut.  
  
 Der Bericht ruft **sp_help_log_shipping_monitor** auf, um die Daten abzurufen. Informationen zu den erforderlichen Berechtigungen finden Sie unter [sp_help_log_shipping_monitor &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-help-log-shipping-monitor-transact-sql.md).  
  
### So zeigen Sie den Transaktionsprotokoll-Versandstatus-Bericht auf einer Serverinstanz an  
  
1.  Stellen Sie eine Verbindung mit einem Überwachungsserver, einem primären Server oder einem sekundären Server her.  
  
2.  Klicken Sie im Objekt-Explorer mit der rechten Maustaste auf die Serverinstanz, zeigen Sie auf **Berichte**, und zeigen Sie auf **Standardberichte**.  
  
3.  Klicken Sie auf **Transaktionsprotokoll-Versandstatus**.  
  
## Siehe auch  
 [Überwachen des Protokollversands &#40;Transact-SQL&#41;](../../database-engine/log-shipping/monitor-log-shipping-transact-sql.md)  
  
  