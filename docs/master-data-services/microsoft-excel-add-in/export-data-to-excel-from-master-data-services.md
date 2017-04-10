---
title: "Export Data to Excel from Master Data Services | Microsoft Docs"
ms.custom: ""
ms.date: "03/01/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "master-data-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: dd29389b-928c-4e50-995c-c6af27f97805
caps.latest.revision: 16
author: "sabotta"
ms.author: "carlasab"
manager: "jhubbard"
caps.handback.revision: 16
---
# Export Data to Excel from Master Data Services
  In [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)][!INCLUDE[ssMDSXLS](../../includes/ssmdsxls-md.md)] müssen Sie Daten aus dem MDS-Repository laden, um damit zu arbeiten.  
  
 Wenn Sie das Dataset vor dem Laden filtern möchten, gehen Sie stattdessen zum Thema [Filter Data before Exporting &#40;MDS Add-in for Excel&#41;](../../master-data-services/microsoft-excel-add-in/filter-data-before-exporting-mds-add-in-for-excel.md) (Filtern von Daten vor dem Exportieren (MDS-Add-In für Excel)).  
  
## Erforderliche Komponenten  
 So führen Sie diese Prozedur aus  
  
-   Sie müssen über die Berechtigung für den Zugriff auf den Funktionsbereich **Explorer** verfügen.  
  
### So exportieren Sie Daten aus MDS in Excel  
  
1.  Öffnen Sie Excel, und stellen Sie auf der Registerkarte **Masterdaten** eine Verbindung mit einem MDS-Repository her. Weitere Informationen finden Sie unter [Herstellen einer Verbindung mit einem MDS-Repository &#40;MDS-Add-In für Excel&#41;](../../master-data-services/microsoft-excel-add-in/connect-to-an-mds-repository-mds-add-in-for-excel.md).  
  
2.  Wählen Sie im Bereich **Master Data Explorer** ein Modell und eine Version aus. Die Liste der Entitäten wird aufgefüllt.  
  
    -   Wenn der Bereich **Master Data Explorer** nicht sichtbar ist, klicken Sie in der Gruppe **Verbinden und Laden** auf **Explorer anzeigen**.  
  
    -   Wenn der Bereich **Master Data Explorer** deaktiviert ist, liegt dies daran, dass das vorhandene Blatt bereits von MDS verwaltete Daten enthält. Um den Bereich zu aktivieren, öffnen Sie ein neues Arbeitsblatt.  
  
3.  Doppelklicken Sie im Bereich **Master Data Explorer** in der Liste der Entitäten auf die Entität, die Sie laden möchten.  
  
    > [!NOTE]  
    >  -   Nur die erste eine Million von Elementen wird in Excel geladen. Klicken Sie zum Filtern der Liste vor dem Laden im Menüband in der Gruppe **Verbinden und Laden** auf **Filtern**.  
    > -   In Spalten, die beschränkte Listen (domänenbasierte Attribute) sind, werden standardmäßig nur die ersten 25.000 Werte geladen. Sie können diese Zahl in der Eigenschaft "MaximumDbaEntitySize" der Datei "excelusersettings.config" ändern, die sich auf dem Computer befindet, auf dem Excel installiert ist. Diese Datei befindet in „C:\Benutzer\\<Benutzer\>\AppData\Local\Microsoft\Microsoft SQL Server\130\MasterDataServices\\“.  
    >   
    >      Wenn ein domänenbasiertes Attribut mehrere Werte hat, die die Einstellung der Eigenschaft "MaximumDbEntitySize" überschreiten, wird die Liste der Werte nicht geladen.  
  
    > [!NOTE]  
    >  Es wird ein Fehler über unzureichenden Arbeitsspeicher angezeigt, wenn Sie textgetrennte Daten mithilfe des Add-Ins für Microsoft Excel in einer 32-Bit-Version von Excel laden und die Eigenschaften **Cell Count to Load** und **Cell Count to Publish** auf das Maximum von „1000“ festlegen. Sie müssen die 64-Bit-Version von Excel verwenden, um die Maximaleinstellungen für **Cell Count to Load** und **Cell Count to Publish** verwenden zu können.  
  
## Nächste Schritte  
 [Importieren von Daten aus Excel in Master Data Services &#40;MDS-Add-In für Excel&#41;](../../master-data-services/microsoft-excel-add-in/import-data-from-excel-to-master-data-services-mds-add-in-for-excel.md)  
  
## Siehe auch  
 [Overview: Exporting Data to Excel &#40;MDS Add-in for Excel&#41; (Übersicht: Exportieren von Daten nach Excel (MDS-Add-in für Excel))](../../master-data-services/microsoft-excel-add-in/overview-exporting-data-to-excel-mds-add-in-for-excel.md)   
 [Filtern &#40;Dialogfeld, MDS-Add-In für Excel&#41;](../../master-data-services/microsoft-excel-add-in/filter-dialog-box-mds-add-in-for-excel.md)   
 [Übersicht: Importieren von Daten aus Excel &#40;MDS-Add-In für Excel&#41;](../../master-data-services/microsoft-excel-add-in/overview-importing-data-from-excel-mds-add-in-for-excel.md)  
  
  