---
title: Quellen-Editor für ODBC (Seite Fehlerausgabe) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/14/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- integration-services
ms.topic: conceptual
f1_keywords:
- sql12.ssis.designer.odbcsource.errorhandling.f1
ms.assetid: b2f6866c-db07-4cb3-9f38-889f8d2b03e6
author: douglaslms
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 1bf6d22a2cbe6111f9cce1a3be446c507969ca82
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/02/2018
ms.locfileid: "48158420"
---
# <a name="odbc-source-editor-error-output-page"></a>Quellen-Editor für ODBC (Seite Fehlerausgabe)
  Auf der Seite **Fehlerausgabe** des Dialogfelds **Quellen-Editor für ODBC** können Sie Optionen für die Fehlerbehandlung auswählen.  
  
 Weitere Informationen zur ODBC-Quelle finden Sie unter [CDC Source](data-flow/cdc-source.md).  
  
## <a name="task-list"></a>Aufgabenliste  
 **So öffnen Sie die Seite "Fehlerausgabe" des Quellen-Editors für ODBC**  
  
-   Öffnen Sie in [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)]das [!INCLUDE[ssISCurrent](../includes/ssiscurrent-md.md)] -Paket, das die ODBC-Quelle enthält.  
  
-   Doppelklicken Sie auf der Registerkarte **Datenfluss** auf die ODBC-Quelle.  
  
-   Klicken Sie im **Quellen-Editor für ODBC**auf **Fehlerausgabe**.  
  
## <a name="options"></a>Tastatur  
  
### <a name="inputoutput"></a>Eingabe/Ausgabe  
 Zeigt den Namen der Datenquelle an.  
  
### <a name="column"></a>Spalte  
 Wird nicht verwendet.  
  
### <a name="error"></a>Fehler  
 Wählen Sie aus, wie die ODBC-Quelle Fehler in einem Fluss behandeln soll: Fehler ignorieren, Zeile umleiten oder Komponente mit einem Fehler abbrechen.  
  
### <a name="truncation"></a>Abschneiden  
 Wählen Sie aus, wie die ODBC-Quelle Kürzungen in einem Fluss behandeln soll: Fehler ignorieren, Zeile umleiten oder Komponente mit einem Fehler abbrechen.  
  
### <a name="description"></a>Description  
 Wird nicht verwendet.  
  
### <a name="set-this-value-to-selected-cells"></a>Diesen Wert für ausgewählte Zellen festlegen  
 Wählen Sie aus, wie die ODBC-Quelle im Fall eines Fehlers oder einer Kürzung mit den ausgewählten Zellen verfahren soll: Fehler ignorieren, Zeile umleiten oder Komponente mit einem Fehler abbrechen.  
  
### <a name="apply"></a>Anwenden  
 Wendet die Fehlerbehandlungsoptionen auf die ausgewählten Zellen an.  
  
## <a name="error-handling-options"></a>Fehlerbehandlungsoptionen  
 Mit den folgenden Optionen konfigurieren Sie, wie die ODBC-Quelle Fehler und Kürzungen behandelt.  
  
### <a name="fail-component"></a>Fehler bei Komponente  
 Bei einem Fehler oder beim Abschneiden von Daten wird der Datenflusstask nicht ausgeführt. Dies ist das Standardverhalten.  
  
### <a name="ignore-failure"></a>Fehler ignorieren  
 Der Fehler oder die Kürzung wird ignoriert.  
  
### <a name="redirect-flow"></a>Zeile umleiten  
 Die Zeile, die den Fehler oder die Kürzung verursacht, wird an die Fehlerausgabe der ODBC-Quelle umgeleitet. Weitere Informationen finden Sie unter [ODBC Source](data-flow/odbc-source.md).  
  
## <a name="see-also"></a>Siehe auch  
 [Quellen-Editor für ODBC &#40;Seite Verbindungs-Manager&#41;](../../2014/integration-services/odbc-source-editor-connection-manager-page.md)   
 [Quellen-Editor für ODBC &#40;Seite "Spalten"&#41;](../../2014/integration-services/odbc-source-editor-columns-page.md)  
  
  
