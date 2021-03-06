---
title: XQuery-Prolog | Microsoft-Dokumentation
ms.custom: ''
ms.date: 08/09/2016
ms.prod: sql
ms.prod_service: sql
ms.reviewer: ''
ms.technology: xml
ms.topic: language-reference
dev_langs:
- XML
helpviewer_keywords:
- XQuery, prolog
- prolog
- namespaces [XQuery]
- default namespace declarations
ms.assetid: 03924684-c5fd-44dc-8d73-c6ab90f5e069
author: rothja
ms.author: jroth
manager: craigg
ms.openlocfilehash: 731877fced1d14e385f8681d4a436269e518595a
ms.sourcegitcommit: 9c6a37175296144464ffea815f371c024fce7032
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/15/2018
ms.locfileid: "51656799"
---
# <a name="modules-and-prologs---xquery-prolog"></a>Module und Prologe – XQuery-Prolog
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Eine XQuery-Abfrage besteht aus einem Prolog und einem Hauptteil (Body). Der XQuery-Prolog besteht aus einer Reihe von Deklarationen und Definitionen, die gemeinsam die für die Verarbeitung der Abfrage erforderliche Umgebung erstellen. In SQL Server kann der XQuery-Prolog Namespacedeklarationen enthalten. Der XQuery-Hauptteil besteht aus einer Sequenz von Ausdrücken, die das beabsichtigte Abfrageergebnis angeben.  
  
 Z. B. die folgende XQuery-Abfrage angegeben ist, für die Instructions-Spalte der **Xml** Typ, der produktionsanweisungen als XML gespeichert. Die Abfrage ruft die Produktionsanweisungen für den Arbeitsplatzstandort `10` ab. Die `query()` Methode der **Xml** -Datentyp wird zum Angeben der XQuery verwendet.  
  
```  
SELECT Instructions.query('declare namespace AWMI="https://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelManuInstructions";           
    /AWMI:root/AWMI:Location[@LocationID=10]  
') AS Result   
FROM  Production.ProductModel  
WHERE ProductModelID=7  
```  
  
 Beachten Sie hinsichtlich der vorherigen Abfrage Folgendes:  
  
-   Die XQuery-Prolog enthält eine Namespace-Präfixdeklaration (AWMI), `(namespace AWMI="https://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelManuInstructions";`.  
  
-   Das `declare namespace`-Schlüsselwort definiert ein Namespacepräfix, das später im Hauptteil der Abfrage verwendet wird.  
  
-   `/AWMI:root/AWMI:Location[@LocationID="10"]` ist der Hauptteil der Abfrage.  
  
## <a name="namespace-declarations"></a>Namespacedeklarationen  
 Eine Namespacedeklaration definiert ein Präfix und ordnet dieses einem Namespace-URI zu, was in der folgenden Abfrage dargestellt ist. In der Abfrage `CatalogDescription` ist ein **Xml** Type-Spalte.  
  
 Indem die XQuery-Abfrage für die Spalte angegeben wird, gibt der Abfrageprolog mit der `declare namespace`-Deklaration an, dass das Präfix `PD`, die Produktbeschreibung, dem Namespace-URI zugeordnet wird. Dieses Präfix wird dann im Hauptteil der Abfrage anstelle der Namespace-URI verwendet.  Die Knoten des daraus resultierenden XML befinden sich in dem dem Namespace-URI zugeordneten Namespace.  
  
```  
SELECT CatalogDescription.query('  
declare namespace PD="https://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelDescription";  
         /PD:ProductDescription/PD:Summary   
    ') as Result  
FROM Production.ProductModel  
where ProductModelID=19  
```  
  
 Um die Lesbarkeit der Abfrage zu verbessern, können Sie Namespaces mit WITH XMLNAMESPACES deklarieren, statt die Präfix- und Namespacebindung mit `declare namespace` im Abfrageprolog zu deklarieren.  
  
```  
WITH XMLNAMESPACES ('https://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelDescription' AS PD)  
  
SELECT CatalogDescription.query('  
         /PD:ProductDescription/PD:Summary   
    ') as Result  
FROM Production.ProductModel  
where ProductModelID=19  
```  
  
 Weitere Informationen finden Sie unter, [Hinzufügen von Namespaces zu Abfragen mit WITH XMLNAMESPACES](../relational-databases/xml/add-namespaces-to-queries-with-with-xmlnamespaces.md).  
  
### <a name="default-namespace-declaration"></a>Standardnamespacedeklaration  
 Statt ein Namespacepräfix mit der `declare namespace`-Deklaration zu deklarieren, können Sie die `declare default element namespace`-Deklaration verwenden, um einen Standardnamespace für Elementnamen zu binden. In diesem Fall definieren Sie kein Präfix.  
  
 Im folgenden Beispiel gibt der Pfadausdruck der Abfrage kein Namespacepräfix an. Standardmäßig gehören alle Elementnamen zu dem im Prolog angegebenen Standardnamespace.  
  
```  
SELECT CatalogDescription.query('  
     declare default element namespace  "https://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelDescription";  
        /ProductDescription/Summary   
    ') as Result  
FROM  Production.ProductModel  
WHERE ProductModelID=19   
```  
  
 Einen Standardnamespace können Sie mit WITH XMLNAMESPACES deklarieren:  
  
```  
WITH XMLNAMESPACES (DEFAULT 'https://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelDescription')  
SELECT CatalogDescription.query('  
        /ProductDescription/Summary   
    ') as Result  
FROM  Production.ProductModel  
WHERE ProductModelID=19   
```  
  
## <a name="see-also"></a>Siehe auch  
 [Hinzufügen von Namespaces zu Abfragen mit WITH XMLNAMESPACES](../relational-databases/xml/add-namespaces-to-queries-with-with-xmlnamespaces.md)  
  
  
