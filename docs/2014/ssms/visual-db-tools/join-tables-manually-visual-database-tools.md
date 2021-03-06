---
title: Manuelles Verknüpfen von Tabellen (Visual Database Tools) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- manual joins [SQL Server]
- joins [SQL Server], manual
- joins [SQL Server], creating
ms.assetid: 9c785356-646b-4c87-82d4-25efd6051d9d
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 0299be9a1cb480a567e0b166c990d25588598aba
ms.sourcegitcommit: ceb7e1b9e29e02bb0c6ca400a36e0fa9cf010fca
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/03/2018
ms.locfileid: "52812762"
---
# <a name="join-tables-manually-visual-database-tools"></a>Manuelles Verknüpfen von Tabellen (Visual Database Tools)
  Wenn Sie einer Abfrage mindestens zwei Tabellen hinzufügen, versucht der [Abfrage- und Sicht-Designer](visual-database-tools.md) diese auf der Grundlage häufig auftretender Daten oder der in der Datenbank gespeicherten Informationen zu Tabellenjoins zu verknüpfen. Ausführliche Informationen finden Sie unter [Automatisches Verknüpfen von Tabellen &#40;Visual Database Tools&#41;](join-tables-automatically-visual-database-tools.md). Wenn der Abfrage- und Sicht-Designer die Tabellen jedoch nicht automatisch verknüpft hat oder wenn Sie weitere Joinbedingungen zwischen Tabellen erstellen möchten, können Sie Tabellen manuell verknüpfen.  
  
 Sie können Joins auf der Grundlage von Vergleichen zwischen zwei beliebigen Spalten erstellen, die aber nicht dieselben Informationen enthalten müssen. Wenn z. B. die Datenbank die zwei Tabellen `titles` und `roysched`enthält, können Sie die Werte in der Spalte `ytd_sales` der Tabelle `titles` mit den Spalten `lorange` und `hirange` in der Tabelle `roysched` vergleichen. Das Erstellen dieses Joins ermöglicht Ihnen das Suchen nach Titeln, für die die Verkäufe des aktuellen Jahres zwischen dem unteren und dem oberen Bereich der Tantiemenzahlungen liegen.  
  
> [!TIP]  
>  Joins funktionieren am schnellsten, wenn die Spalten in der Joinbedingung indiziert sind. In einigen Fällen kann der Join über nicht indizierte Spalten zu einer langsamen Abfrage führen.  
  
### <a name="to-manually-join-tables-or-table-structured-objects"></a>So verknüpfen Sie Tabellen oder Objekte mit Tabellenstruktur manuell  
  
1.  Fügen Sie dem [Diagrammbereich](diagram-pane-visual-database-tools.md) die zu verknüpfenden Objekte hinzu.  
  
2.  Ziehen Sie den Namen der Joinspalte aus der ersten Tabelle bzw. aus dem ersten Objekt mit Tabellenstruktur, und legen Sie diesen auf der entsprechenden Spalte in der zweiten Tabelle bzw. im zweiten Objekt mit Tabellenstruktur ab. Ein Join kann nicht auf der Grundlage der Spalten `text`, `ntext` oder i`mage` erstellt werden.  
  
    > [!NOTE]  
    >  Die Joinspalten müssen denselben (oder einen kompatiblen) Datentyp aufweisen. Wenn z. B. die Joinspalte in der ersten Tabelle eine Datenspalte ist, müssen Sie diese mit einer Datenspalte in der zweiten Tabelle verknüpfen. Wenn es sich jedoch bei der ersten Joinspalte um eine Integer-Spalte handelt, muss die zu verknüpfende Spalte ebenfalls vom Integer-Datentyp sein, kann jedoch eine andere Größe aufweisen. Der Abfrage- und Sicht-Designer überprüft die Datentypen der für einen Join verwendeten Spalten nicht. Wenn Sie jedoch die Abfrage ausführen, zeigt die Datenbank bei nicht kompatiblen Datentypen einen Fehler an.  
  
3.  Ändern Sie ggf. den Joinoperator; in der Standardeinstellung ist der Operator ein Gleichheitszeichen (=). Weitere Informationen finden Sie unter [Ändern von Joinoperatoren &#40;Visual Database Tools&#41;](modify-join-operators-visual-database-tools.md).  
  
 Der Abfrage- und Sicht-Designer fügt der SQL-Anweisung im [SQL-Bereich](sql-pane-visual-database-tools.md) eine INNER JOIN-Klausel hinzu. Sie können den Typ in einen äußeren Join ändern. Weitere Informationen finden Sie unter [Erstellen von äußeren Joins &#40;Visual Database Tools&#41;](create-outer-joins-visual-database-tools.md).  
  
## <a name="see-also"></a>Siehe auch  
 [Erstellen von Abfragen mit Joins &#40;Visual Database Tools&#41;](query-with-joins-visual-database-tools.md)  
  
  
