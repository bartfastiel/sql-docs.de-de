---
title: Bestimmen von Nutzungsstatistiken und der Leistung von Ansichten mit DMV
description: Bestimmen von Nutzungsstatistiken und der Leistung von Ansichten mit DMV
manager: craigg
author: MashaMSFT
ms.author: mathoma
ms.date: 09/27/2018
ms.prod: sql
ms.reviewer: ''
ms.technology: performance
ms.topic: conceptual
ms.openlocfilehash: 4181615840f62b6e4e8a7447f559f4f0c50eb206
ms.sourcegitcommit: f1cf91e679d1121d7f1ef66717b173c22430cb42
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 11/29/2018
ms.locfileid: "52586313"
---
# <a name="use-dmvs-to-determine-usage-statistics-and-performance-of-views"></a>Bestimmen von Nutzungsstatistiken und der Leistung von Ansichten mit DMV
Dieser Artikel behandelt Methoden und Skripts, mit denen Sie Informationen zur **Leistung von Abfragen, die Sichten verwenden** abrufen können. Der Zweck dieser Skripts besteht darin, Indikatoren für die Nutzung und Leistung verschiedener Sichten in einer Datenbank zu liefern. 

## <a name="sysdmexecqueryoptimizerinfo"></a>sys.dm_exec_query_optimizer_info
Die dynamische Verwaltungssicht (DMV) [sys.dm_exec_query_optimizer_info](../../relational-databases/system-dynamic-management-views/sys-dm-exec-query-optimizer-info-transact-sql.md) stellt Statistiken zu den Optimierungen durch den [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Abfrageoptimierer bereit. Diese Werte sind kumulativ und werden erfasst, wenn [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] gestartet wird. Weitere Informationen zum Abfrageoptimierer finden Sie im [Handbuch zur Architektur der Abfrageverarbeitung](../../relational-databases/query-processing-architecture-guide.md).   

Der common_table_expression (CTE, allgemeiner Tabellenausdruck) unten verwendet diese DMV, um Informationen zur Workload bereitzustellen, z.B. den Prozentsatz der Abfragen, die auf eine Sicht verweisen. Die von dieser Abfrage zurückgegebenen Ergebnisse deuten an sich nicht auf ein Leistungsproblem hin, sondern weisen ggf. auf zugrunde liegende Probleme hin, wenn sie mit Benutzerbeschwerden über langsame Abfragen kombiniert werden. 

```sql
WITH CTE_QO AS
(
  SELECT
    occurrence
  FROM
    sys.dm_exec_query_optimizer_info
  WHERE
    ([counter] = 'optimizations')
),
QOInfo AS
(
  SELECT
    [counter]
    ,[%] = CAST((occurrence * 100.00)/(SELECT occurrence FROM CTE_QO) AS DECIMAL(5, 2))
  FROM
    sys.dm_exec_query_optimizer_info
  WHERE
    [counter] IN ('optimizations'
                  ,'trivial plan'
                  ,'no plan'
                  ,'search 0'
                  ,'search 1'
                  ,'search 2'
                  ,'timeout'
                  ,'memory limit exceeded'
                  ,'insert stmt'
                  ,'delete stmt'
                  ,'update stmt'
                  ,'merge stmt'
                  ,'contains subquery'
                  ,'view reference'
                  ,'remote query'
                  ,'dynamic cursor request'
                  ,'fast forward cursor request'
             )
)
SELECT
  [optimizations] AS [optimizations %]
  ,[trivial plan] AS [trivial plan %]
  ,[no plan] AS [no plan %]
  ,[search 0] AS [search 0 %]
  ,[search 1] AS [search 1 %]
  ,[search 2] AS [search 2 %]
  ,[timeout] AS [timeout %]
  ,[memory limit exceeded] AS [memory limit exceeded %]
  ,[insert stmt] AS [insert stmt %]
  ,[delete stmt] AS [delete stmt]
  ,[update stmt] AS [update stmt]
  ,[merge stmt] AS [merge stmt]
  ,[contains subquery] AS [contains subquery %]
  ,[view reference] AS [view reference %]
  ,[remote query] AS [remote query %]
  ,[dynamic cursor request] AS [dynamic cursor request %]
  ,[fast forward cursor request] AS [fast forward cursor request %]
FROM
  QOInfo
PIVOT (MAX([%]) FOR [counter] 
  IN ([optimizations]
      ,[trivial plan]
      ,[no plan]
      ,[search 0]
      ,[search 1]
      ,[search 2]
      ,[timeout]
      ,[memory limit exceeded]
      ,[insert stmt]
      ,[delete stmt]
      ,[update stmt]
      ,[merge stmt]
      ,[contains subquery]
      ,[view reference]
      ,[remote query]
      ,[dynamic cursor request]
      ,[fast forward cursor request])) AS p;
GO
```

Kombinieren Sie die Ergebnisse dieser Abfrage mit den Ergebnissen der Systemansicht [sys.views](../../relational-databases/system-catalog-views/sys-views-transact-sql.md), um Abfragestatistiken, Abfragetext und den zwischengespeicherten Ausführungsplan zu ermitteln. 

## <a name="sysviews"></a>sys.views
Der folgende allgemeine Tabellenausdruck liefert Informationen über die Anzahl von Ausführungen, die Gesamtlaufzeit und die aus dem Arbeitsspeicher gelesenen Seiten. Mithilfe der Ergebnisse lassen sich Abfragen identifizieren, die möglicherweise optimiert werden können. 
  
> [!NOTE]
> Die Ergebnisse dieser Abfrage können je nach [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Version variieren.  


```sql
WITH CTE_VW_STATS AS
(
  SELECT
    SCHEMA_NAME(vw.schema_id) AS schemaname
    ,vw.name AS viewname
    ,vw.object_id AS viewid
  FROM
    sys.views AS vw
  WHERE
    (vw.is_ms_shipped = 0)
  INTERSECT
  SELECT
    SCHEMA_NAME(o.schema_id) AS schemaname
    ,o.Name AS name
    ,st.objectid AS viewid
  FROM
    sys.dm_exec_cached_plans cp
  CROSS APPLY
    sys.dm_exec_sql_text(cp.plan_handle) st
  INNER JOIN
    sys.objects o ON st.[objectid] = o.[object_id]
  WHERE
    st.dbid = DB_ID()
)
SELECT
  vw.schemaname
  ,vw.viewname
  ,vw.viewid
  ,DB_NAME(t.databaseid) AS databasename
  ,t.databaseid
  ,t.*
FROM
  CTE_VW_STATS AS vw
CROSS APPLY
  (
    SELECT
      st.dbid AS databaseid
      ,st.text
      ,qp.query_plan
      ,qs.*
    FROM
      sys.dm_exec_query_stats AS qs
    CROSS APPLY
      sys.dm_exec_sql_text(qs.plan_handle) AS st
    CROSS APPLY
      sys.dm_exec_query_plan(qs.plan_handle) AS qp
    WHERE
      (CHARINDEX(vw.schemaname, st.text, 1) > 0)
      AND (st.dbid = DB_ID())
  ) AS t;
GO
```

## <a name="sysdmvexeccachedplans"></a>sys.dmv_exec_cached_plans
Die letzte Abfrage stellt mithilfe der DMV [sys.dmv_exec_cached_plans](../../relational-databases/system-dynamic-management-views/sys-dm-exec-cached-plans-transact-sql.md) Informationen zu unbenutzte Ansichten bereit. Der Ausführungsplancache ist jedoch dynamisch und die Ergebnisse können variieren. Führen Sie diese Abfrage daher im Laufe der Zeit aus, um festzustellen, ob eine Ansicht tatsächlich verwendet wird. 

```sql
SELECT
  SCHEMA_NAME(vw.schema_id) AS schemaname
  ,vw.name AS name
  ,vw.object_id AS viewid
FROM
  sys.views AS vw
WHERE
  (vw.is_ms_shipped = 0)
EXCEPT
SELECT
  SCHEMA_NAME(o.schema_id) AS schemaname
  ,o.name AS name
  ,st.objectid AS viewid
FROM
  sys.dm_exec_cached_plans cp
CROSS APPLY
  sys.dm_exec_sql_text(cp.plan_handle) st
INNER JOIN
  sys.objects o ON st.[objectid] = o.[object_id]
WHERE
  st.dbid = DB_ID();
GO
```

## <a name="see-also"></a>Siehe auch
[Dynamische Verwaltungssichten und -funktionen](../../relational-databases/system-dynamic-management-views/system-dynamic-management-views.md)   
[DMVs zur Leistungsoptimierung (Video, SQL Saturday, Pordenone)](https://www.youtube.com/watch?v=9FQaFwpt3-k)  (in italienischer Sprache)  
[DMVs zur Leistungsoptimierung (Präsentation und Demo, SQL Saturday, Pordenone)](https://www.sqlsaturday.com/589/Sessions/Details.aspx?sid=57409)  (in italienischer Sprache)  
[SQL Server: Optimierung in Kürze (Video, SQL Saturday, Parma)](https://vimeo.com/200980883)   (in italienischer Sprache)  
[SQL Server: Optimierung in Kürze (Präsentation und Demo, SQL Saturday, Parma)](https://www.sqlsaturday.com/566/Sessions/Details.aspx?sid=53988)  (in italienischer Sprache)  
[Optimieren der Leistung mit der dynamischen Verwaltungssicht von SQL Server](https://www.red-gate.com/library/performance-tuning-with-sql-server-dynamic-management-views)  (in englischer Sprache)  
[Die wichtigsten Wartetypen von SQL Server 2016](https://channel9.msdn.com/Blogs/MVP-Data-Platform/The-Most-Prominent-Wait-Types-of-your-SQL-Server-2016) (in italienischer Sprache)   
