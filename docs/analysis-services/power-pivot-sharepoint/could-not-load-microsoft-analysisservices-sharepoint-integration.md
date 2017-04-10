---
title: "Datei oder Assembly &quot;Microsoft.AnalysisServices.SharePoint.Integration&quot; konnte nicht geladen werden | Microsoft Docs"
ms.custom: ""
ms.date: "03/14/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "analysis-services"
ms.tgt_pltfrm: ""
ms.topic: "reference"
ms.assetid: 6e350b67-5e18-4b90-8fb7-a0109cbb27b7
caps.latest.revision: 7
author: "Minewiskan"
ms.author: "owend"
manager: "erikre"
caps.handback.revision: 7
---
# Datei oder Assembly &quot;Microsoft.AnalysisServices.SharePoint.Integration&quot; konnte nicht geladen werden
  In SharePoint 2010-Umgebungen mit [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] für SharePoint tritt dieser Fehler auf, wenn die Lösung auf Anwendungsebene für [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] nicht ordnungsgemäß bereitgestellt wurde.  
  
## Details  
  
|||  
|-|-|  
|Gilt für|[!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] für SharePoint|  
|Produktversion|[!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)], [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)], [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)]|  
|Ursache|Die Powerpivotwebapp-Lösung wurde nicht ordnungsgemäß oder überhaupt nicht bereitgestellt.|  
|Meldungstext|Datei oder Assembly "Microsoft.AnalysisServices.SharePoint.Integration" konnte nicht geladen werden|  
  
## Erklärung  
 [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] für SharePoint stellt seine Funktionen mithilfe von Lösungspaketen auf einem SharePoint-Server bereit. Eine der Lösungen wurde nicht ordnungsgemäß bereitgestellt. Daher tritt dieser Fehler auf, wenn Sie versuchen, den [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] -Katalog oder andere [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] -Anwendungsseiten auf einer SharePoint-Website zu öffnen.  
  
## Benutzeraktion  
 Stellen Sie das Lösungspaket bereit.  
  
1.  Klicken Sie in der Zentraladministration unter Systemeinstellungen auf **Farmlösungen verwalten**.  
  
2.  Klicken Sie auf **Powerpivotwebapp**.  
  
3.  Klicken Sie auf **Lösung bereitstellen**.  
  
4.  Wählen Sie die Webanwendung aus, für die dieser Fehler aufgetreten ist. Bei mehr als einer Webanwendung stellen Sie die Lösung für alle Anwendungen erneut bereit.  
  
5.  Klicken Sie auf **OK**.  
  
## Siehe auch  
 [Bereitstellen von Power Pivot-Lösungen in SharePoint](../../analysis-services/power-pivot-sharepoint/deploy-power-pivot-solutions-to-sharepoint.md)  
  
  