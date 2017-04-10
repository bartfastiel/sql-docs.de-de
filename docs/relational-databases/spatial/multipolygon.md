---
title: "MultiPolygon | Microsoft Docs"
ms.custom: ""
ms.date: "03/03/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dbe-spatial"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "geometry-Untertyp Multipolygon [SQL Server]"
  - "geometry-Untertypen [SQL Server]"
ms.assetid: 2c5db358-2a16-49d9-aac5-a74e86813932
caps.latest.revision: 20
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 20
---
# MultiPolygon
  Eine **MultiPolygon** -Instanz ist eine Sammlung von null oder mehr **Polygon** -Instanzen.  
  
## Polygon-Instanzen  
 Die nachfolgende Abbildung enthält Beispiele für **MultiPolygon** -Instanzen.  
  
 ![Beispiele für MultiPolygon-Geometrieinstanzen](../../relational-databases/spatial/media/multipolygon.png "Beispiele für MultiPolygon-Geometrieinstanzen")  
  
 Folgendes wird dargestellt:  
  
-   Abbildung 1 zeigt eine **MultiPolygon** -Instanz mit zwei **Polygon** -Elementen. Die Begrenzung wird durch die beiden äußeren Ringe und die drei inneren Ringe definiert.  
  
-   Abbildung 2 zeigt eine **MultiPolygon** -Instanz mit zwei **Polygon** -Elementen. Die Begrenzung wird durch die beiden äußeren Ringe und die drei inneren Ringe definiert. Die beiden **Polygon** -Elemente überschneiden sich an einem Tangentenpunkt.  
  
### Akzeptierte Instanzen  
 Eine **MultiPolygon** -Instanz ist akzeptiert, wenn eine der folgenden Bedingungen erfüllt ist.  
  
-   Es handelt sich um eine leere **MultiPolygon** -Instanz.  
  
-   Alle Instanzen, aus denen die **MultiPolygon** -Instanz besteht, sind akzeptierte **Polygon** -Instanzen. Weitere Informationen über akzeptierte **Polygon** -Instanzen finden Sie unter [Polygon](../../relational-databases/spatial/polygon.md).  
  
 In den folgenden Beispielen werden akzeptierte **MultiPolygon** -Instanzen veranschaulicht.  
  
```  
DECLARE @g1 geometry = 'MULTIPOLYGON EMPTY';  
DECLARE @g2 geometry = 'MULTIPOLYGON(((1 1, 1 -1, -1 -1, -1 1, 1 1)),((1 1, 3 1, 3 3, 1 3, 1 1)))';  
DECLARE @g3 geometry = 'MULTIPOLYGON(((2 2, 2 -2, -2 -2, -2 2, 2 2)),((1 1, 3 1, 3 3, 1 3, 1 1)))';  
```  
  
 Das folgende Beispiel zeigt eine MultiPolygon-Instanz, die eine `System.FormatException`auslöst.  
  
```  
DECLARE @g geometry = 'MULTIPOLYGON(((1 1, 1 -1, -1 -1, -1 1, 1 1)),((1 1, 3 1, 3 3)))';  
```  
  
 Die zweite Instanz im MultiPolygon ist eine LineString-Instanz und keine akzeptierte Polygon-Instanz.  
  
### Gültige Instanzen  
 Eine **MultiPolygon** -Instanz ist gültig, wenn es sich um eine leere **MultiPolygon** -Instanz handelt bzw. wenn die folgenden Kriterien erfüllt werden.  
  
1.  Alle Instanzen, aus denen die **MultiPolygon** -Instanz besteht, sind gültige **Polygon** -Instanzen. Informationen über gültige **Polygon** -Instanzen finden Sie unter [Polygon](../../relational-databases/spatial/polygon.md).  
  
2.  Die **Polygon** -Instanzen, aus denen die **MultiPolygon** -Instanz besteht, überschneiden sich nicht.  
  
 Im folgende Beispiel werden zwei gültige **MultiPolygon** -Instanzen und eine ungültige **MultiPolygon** -Instanz veranschaulicht.  
  
```  
DECLARE @g1 geometry = 'MULTIPOLYGON EMPTY';  
DECLARE @g2 geometry = 'MULTIPOLYGON(((1 1, 1 -1, -1 -1, -1 1, 1 1)),((1 1, 3 1, 3 3, 1 3, 1 1)))';  
DECLARE @g3 geometry = 'MULTIPOLYGON(((2 2, 2 -2, -2 -2, -2 2, 2 2)),((1 1, 3 1, 3 3, 1 3, 1 1)))';  
SELECT @g1.STIsValid(), @g2.STIsValid(), @g3.STIsValid();  
```  
  
 `@g2` ist gültig, da sich die zwei **Polygon**-Instanzen nur an einem Tangenspunkt berühren. `@g3` ist ungültig, da sich die Innenbereiche der zwei **Polygon**-Instanzen überlappen.  
  
## Beispiele  
 Im folgenden Beispiel wird die Erstellung einer `geometry``MultiPolygon`-Instanz veranschaulicht und das WKT-Format (Well-Known Text) der zweiten Komponente zurückgegeben.  
  
```  
DECLARE @g geometry;  
SET @g = geometry::Parse('MULTIPOLYGON(((0 0, 0 3, 3 3, 3 0, 0 0), (1 1, 1 2, 2 1, 1 1)), ((9 9, 9 10, 10 9, 9 9)))');  
SELECT @g.STGeometryN(2).STAsText();  
```  
  
 In diesem Beispiel wird eine leere `MultiPolygon`-Instanz instantiiert.  
  
```  
DECLARE @g geometry;  
SET @g = geometry::Parse('MULTIPOLYGON EMPTY');  
```  
  
## Siehe auch  
 [Polygon](../../relational-databases/spatial/polygon.md)   
 [STArea &#40;geometry-Datentyp&#41;](../../t-sql/spatial-geometry/starea-geometry-data-type.md)   
 [STCentroid &#40;geometry-Datentyp&#41;](../../t-sql/spatial-geometry/stcentroid-geometry-data-type.md)   
 [STPointOnSurface &#40;geometry-Datentyp&#41;](../../t-sql/spatial-geometry/stpointonsurface-geometry-data-type.md)   
 [Räumliche Daten &#40;SQL Server&#41;](../../relational-databases/spatial/spatial-data-sql-server.md)  
  
  