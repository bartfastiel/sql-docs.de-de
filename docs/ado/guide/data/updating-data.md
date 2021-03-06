---
title: Aktualisieren von Daten | Microsoft-Dokumentation
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- data updates [ADO], about data updates
- updating data [ADO], about updating data
ms.assetid: 6508e4e9-e33a-4dad-b340-5d632fd78a91
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: d593bd3ad745f316b833b375ceaae8b764d21ec2
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/01/2018
ms.locfileid: "47828548"
---
# <a name="updating-data"></a>Aktualisieren von Daten
Update-Verhaltens und der Funktionen ist größtenteils abhängig aktualisieren-Modus (Type-Sperre), Cursortyp und Cursorposition.  
  
 Verwenden der **Update** Methode zum Speichern von Änderungen Sie, um den aktuellen Datensatz des vorgenommen haben eine **Recordset** Objekt seit dem Aufrufen der **AddNew** Methode oder seit Feldwerte ändern in einem vorhandenen Datensatz. Die **Recordset** Objekt muss Updates unterstützen.  
  
 Wenn die **Recordset** Objekt unterstützt die Batch zu aktualisieren, können Sie mehrere Änderungen an einen oder mehrere Datensätze zwischenspeichern, lokal, bis Sie aufrufen, die **UpdateBatch** Methode. Wenn Sie den aktuellen Datensatz bearbeiten oder Hinzufügen eines neuen Datensatzes, beim Aufrufen der **UpdateBatch** -Methode, ADO ruft automatisch die **Update** Methode, um alle ausstehenden Änderungen am aktuellen Datensatz vor dem Speichern übertragen die im Batchmodus Änderungen an den Anbieter.  
  
 Der aktuelle Datensatz bleibt die aktuelle aufzurufen, nachdem Sie die **Update** oder **UpdateBatch** Methoden.  
  
 Dieser Abschnitt enthält die folgenden Themen.  
  
-   [Immediate Mode (Immediate-Modus)](../../../ado/guide/data/immediate-mode.md)  
  
-   [Batchmodus](../../../ado/guide/data/batch-mode.md)  
  
-   [Transaktionsverarbeitung](../../../ado/guide/data/transaction-processing.md)
