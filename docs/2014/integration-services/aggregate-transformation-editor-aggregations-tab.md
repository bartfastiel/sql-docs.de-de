---
title: Transformations-Editor (Registerkarte Aggregationen) aggregieren | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.aggregationtransformation.aggregations.f1
helpviewer_keywords:
- Aggregate Transformation Editor
ms.assetid: a01cb124-ec79-4673-b1a1-bf4d60ee1b45
author: douglaslms
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 4aaf14095eab05110845178f4115fc87ea19947a
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/02/2018
ms.locfileid: "48224460"
---
# <a name="aggregate-transformation-editor-aggregations-tab"></a>Transformations-Editor für Aggregieren (Registerkarte Aggregationen)
  Auf der Registerkarte **Aggregationen** des Dialogfelds **Transformations-Editor für Aggregieren** können Sie die Spalten für Aggregationen und Aggregationseigenschaften angeben. Sie können mehrere Aggregationen anwenden. Durch diese Transformation wird keine Fehlerausgabe generiert.  
  
> [!NOTE]  
>  Die Optionen für die Anzahl an Schlüsseln, die Schlüsselskala, die Anzahl unterschiedlicher Schlüssel sowie für unterschiedliche Schlüsselskalen gelten auf der Komponentenebene, wenn sie auf der Registerkarte **Erweitert** angegeben wurden; sie gelten auf der Ausgabeebene, wenn sie in der erweiterten Ansicht der Registerkarte **Aggregationen** angegeben wurden und auf der Spaltenebene, wenn sie in der Spaltenliste im unteren Bereich der Registerkarte **Aggregationen** angegeben wurden.  
>   
>  In der Transformation für das Aggregieren beziehen sich **Schlüssel** und **Schlüsselskala** auf die Anzahl der Gruppen, die als Ergebnis eines **GROUP BY** -Vorgangs erwartet werden. **COUNT DISTINCT-Schlüssel** und **COUNT DISTINCT-Skala** beziehen sich auf die Anzahl der unterschiedlichen Werte, die als Ergebnis eines **DISTINCT COUNT** -Vorgangs erwartet werden.  
  
 Weitere Informationen zur Transformation für das Aggregieren finden Sie unter [Aggregate Transformation](data-flow/transformations/aggregate-transformation.md).  
  
## <a name="options"></a>Tastatur  
 **Erweitert/Standard**  
 Blenden Sie die Optionen ein oder aus, um mehrere Aggregationen für mehrere Ausgaben zu konfigurieren. Die erweiterten Optionen sind standardmäßig ausgeblendet.  
  
 **Aggregationsname**  
 Geben Sie in der erweiterten Anzeige einen Anzeigenamen für die Aggregation ein.  
  
 **Nach Spalten gruppieren**  
 Wählen Sie in der erweiterten Anzeige Spalten für die Gruppierung aus, indem Sie die Liste **Verfügbare Eingabespalten** wie im Folgenden beschrieben verwenden.  
  
 **Schlüsselskala**  
 Geben Sie in der erweiterten Anzeige optional die ungefähre Anzahl der Schlüssel an, die durch die Aggregation geschrieben werden können. Der Standardwert für diese Option ist **Keine Angabe**. Wenn die Eigenschaften **Schlüsselskala** und **Schlüssel** festgelegt sind, wird der Wert von **Schlüssel** vorrangig behandelt.  
  
|value|Description|  
|-----------|-----------------|  
|Keine Angabe|Die Eigenschaft Schlüsselskala wird nicht verwendet.|  
|Low|Die Aggregation kann ungefähr 500.000 Schlüssel schreiben.|  
|Medium|Die Aggregation kann ungefähr 5.000.000 Schlüssel schreiben.|  
|High|Die Aggregation kann mehr als 25.000.000 Schlüssel schreiben.|  
  
 **Schlüssel**  
 Geben Sie in der erweiterten Anzeige optional die genaue Anzahl der Schlüssel an, die durch die Aggregation geschrieben werden können. Wenn sowohl **Schlüsselskala** als auch **Schlüssel** angegeben sind, wird **Schlüssel** vorrangig behandelt.  
  
 **Verfügbare Eingabespalten**  
 Wählen Sie aus der Liste der verfügbaren Eingabespalten mithilfe der Kontrollkästchen in dieser Tabelle Spalten aus.  
  
 **Eingabespalte**  
 Wählen Sie Spalten aus der Liste der verfügbaren Eingabespalten aus.  
  
 **Ausgabealias**  
 Geben Sie einen Alias für jede Spalte ein. Standardmäßig wird der Name der Eingabespalte verwendet. Sie können jedoch auch einen beschreibenden Namen angeben, sofern dieser eindeutig ist.  
  
 **Vorgang**  
 Wählen Sie einen Vorgang aus der Liste der verfügbaren Vorgänge aus, indem Sie die folgende Tabelle zurate ziehen.  
  
|Vorgang|Description|  
|---------------|-----------------|  
|**GroupBy**|Unterteilt Datasets in Gruppen. Zum Gruppieren können Spalten aller Datentypen verwendet werden. Weitere Informationen finden Sie unter GROUP BY.|  
|**Sum**|Summiert die Werte einer Spalte. Summiert werden können nur Spalten mit einem numerischen Datentyp. Weitere Informationen finden Sie unter SUM.|  
|**Mittelwert**|Gibt den Mittelwert der Werte in einer Spalte zurück. Der Mittelwert kann nur für Spalten mit einem numerischen Datentyp ermittelt werden. Weitere Informationen finden Sie unter AVG.|  
|**Count**|Gibt die Anzahl von Elementen in einer Gruppe zurück. Weitere Informationen finden Sie unter COUNT.|  
|**CountDistinct**|Gibt die Anzahl eindeutiger Werte ungleich null in einer Gruppe zurück. Weitere Informationen finden Sie unter COUNT und Distinct.|  
|**Minimum**|Gibt den kleinsten Wert in einer Gruppe zurück. Ist auf numerische Datentypen beschränkt.|  
|**Maximum**|Gibt den größten Wert in einer Gruppe zurück. Ist auf numerische Datentypen beschränkt.|  
  
 **Vergleichsflags**  
 Wenn Sie **Group By**auswählen, steuern Sie mithilfe der Kontrollkästchen, wie der Vergleich durch die Transformation ausgeführt wird. Weitere Informationen zu den Optionen für das Vergleichen von Zeichenfolgen finden Sie unter [Comparing String Data](data-flow/comparing-string-data.md).  
  
 **Count Distinct Scale**  
 Gibt optional die ungefähre Anzahl unterschiedlicher Werte an, die durch die Aggregation geschrieben werden können. Der Standardwert für diese Option ist **Keine Angabe**. Wenn beide `CountDistinctScale` und **CountDistinctKeys** angegeben sind, **CountDistinctKeys** hat Vorrang vor.  
  
|value|Description|  
|-----------|-----------------|  
|Keine Angabe|Die `CountDistinctScale` Eigenschaft wird nicht verwendet.|  
|Low|Die Aggregation kann ungefähr 500.000 unterschiedliche Werte schreiben.|  
|Medium|Die Aggregation kann ungefähr 5.000.000 unterschiedliche Werte schreiben.|  
|High|Die Aggregation kann mehr als 25.000.000 unterschiedliche Werte schreiben.|  
  
 **Count Distinct Keys**  
 Gibt optional die genaue Anzahl unterschiedlicher Werte an, die durch die Aggregation geschrieben werden können. Wenn beide `CountDistinctScale` und **CountDistinctKeys** angegeben sind, **CountDistinctKeys** hat Vorrang vor.  
  
## <a name="see-also"></a>Siehe auch  
 [Erstellen und Meldungsreferenz von Integration Services-Fehler](../../2014/integration-services/integration-services-error-and-message-reference.md)   
 [Transformations-Editor für aggregieren &#40;Registerkarte "Erweitert"&#41;](../../2014/integration-services/aggregate-transformation-editor-advanced-tab.md)   
 [Aggregieren von Werten in einem Dataset mithilfe der Transformation für das Aggregieren](data-flow/transformations/aggregate-values-in-a-dataset-by-using-the-aggregate-transformation.md)  
  
  
