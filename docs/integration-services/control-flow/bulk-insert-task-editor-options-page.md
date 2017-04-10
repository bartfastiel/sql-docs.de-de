---
title: "Masseneinf&#252;gungstask-Editor (Seite Optionen) | Microsoft Docs"
ms.custom: ""
ms.date: "03/14/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "integration-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "sql13.dts.designer.bulkinserttask.options.f1"
helpviewer_keywords: 
  - "Masseneinfügungstask-Editor"
ms.assetid: b3702811-3eb8-4b28-9190-5ae7a1a7bb6f
caps.latest.revision: 31
author: "douglaslMS"
ms.author: "douglasl"
manager: "jhubbard"
caps.handback.revision: 31
---
# Masseneinf&#252;gungstask-Editor (Seite Optionen)
  Auf der Seite **Optionen** des Dialogfelds **Masseneinfügungstask-Editor** können Sie Eigenschaften für den Masseneinfügungsvorgang festlegen. Durch den Masseneinfügungstask werden große Datenmengen in eine Tabelle oder Sicht von [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] kopiert.  
  
 Weitere Informationen zum Arbeiten mit Masseneinfügungen finden Sie unter [Masseneinfügungstask](../../integration-services/control-flow/bulk-insert-task.md) und [BULK INSERT &#40;Transact-SQL&#41;](../../t-sql/statements/bulk-insert-transact-sql.md).  
  
## enthalten  
 **CodePage**  
 Geben Sie die Codepage für die in der Datendatei enthaltenen Daten an.  
  
 **DataFileType**  
 Geben Sie den Wert für den Datentyp an, der beim Ladevorgang verwendet werden soll.  
  
 **BatchSize**  
 Geben Sie die Anzahl der Zeilen in einem Batch an. Der Standardwert ist die gesamte Datendatei. Wenn Sie **BatchSize** auf null festlegen, werden die Daten in einem Batch geladen.  
  
 **LastRow**  
 Geben Sie die letzte zu kopierende Zeile an.  
  
 **FirstRow**  
 Geben Sie die erste zu kopierende Zeile an.  
  
 **enthalten**  
 |Begriff|Definition|  
|----------|----------------|  
|**Check-Einschränkungen**|Wählen Sie diese Option aus, um die Einschränkungen für Tabelle und Spalte zu überprüfen.|  
|**NULL-Werte beibehalten**|Wählen Sie diese Option aus, um NULL-Werte während des Masseneinfügungsvorgangs beizubehalten, statt für leere Spalten Standardwerte einzufügen.|  
|**IDENTITY_INSERT aktivieren**|Wählen Sie diese Option aus, um vorhandene Werte in eine Identitätsspalte einzufügen.|  
|**Tabellensperre**|Wählen Sie diese Option aus, um die Tabelle während des Masseneinfügungsvorgangs zu sperren.|  
|**Trigger auslösen**|Wählen Sie diese Option aus, um das Einfügen, Aktualisieren oder Löschen von Triggern für die Tabelle auszulösen.|  
  
 **SortedData**  
 Geben Sie die ORDER BY-Klausel in der BULK INSERT-Anweisung an. Der Name der angegebenen Spalte muss eine gültige Spalte in der Zieltabelle sein. Der Standardwert ist **false**. Das bedeutet, dass die Daten nicht durch eine ORDER BY-Klausel sortiert werden.  
  
 **MaxErrors**  
 Geben Sie an, wie viele Fehler maximal auftreten müssen, bevor der Masseneinfügungsvorgang abgebrochen wird. Durch den Wert 0 wird gekennzeichnet, dass eine unendliche Anzahl von Fehlern zulässig ist.  
  
> [!NOTE]  
>  Jede Zeile, die beim Massenladevorgang nicht importiert werden kann, zählt als ein Fehler.  
  
## Siehe auch  
 [Fehler- und Meldungsreferenz von Integration Services](../../integration-services/integration-services-error-and-message-reference.md)   
 [Masseneinfügungstask-Editor &#40;Seite „Allgemein“&#41;](../../integration-services/control-flow/bulk-insert-task-editor-general-page.md)   
 [Masseneinfügungstask-Editor &#40;Seite „Verbindung“&#41;](../../integration-services/control-flow/bulk-insert-task-editor-connection-page.md)   
 [Seite Ausdrücke](../../integration-services/expressions/expressions-page.md)   
 [Ablaufsteuerung](../../integration-services/control-flow/control-flow.md)  
  
  