---
title: Batchverarbeitung von gespeicherten Prozeduraufrufen | Microsoft Docs
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: 
ms.component: native-client-odbc-stored-procedures
ms.reviewer: 
ms.suite: sql
ms.technology: docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords:
- stored procedures [ODBC], batching
- ODBC, stored procedures
- SQL Server Native Client ODBC driver, stored procedures
- batches [ODBC]
- ODBC CALL escape sequence
ms.assetid: b7f53e11-15f0-4602-8134-b166160888f0
caps.latest.revision: "31"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 1211a23285997acbf44a4136208247b64167d12e
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/17/2017
---
# <a name="batching-stored-procedure-calls"></a>Batchverarbeitung von gespeicherten Prozeduraufrufen
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[!INCLUDE[SNAC_Deprecated](../../includes/snac-deprecated.md)]

  Die [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client ODBC-Treiber batches automatisch gespeicherte Prozeduraufrufe an den Server aus, wenn dies angebracht. Der Treiber führt diese Aktion nur aus, wenn die ODBC CALL-Escapesequenz verwendet wird, aber nicht für die [!INCLUDE[tsql](../../includes/tsql-md.md)]-EXECUTE-Anweisung. Durch die Batchverarbeitung gespeicherter Prozeduraufrufe wird die Anzahl der Roundtrips zum Server reduziert und die Leistung deutlich verbessert.  
  
 Der Treiber führt Prozeduraufrufe an den Server als Batches aus, wenn Sie einen Batch ausführen, der mehrere ODBC CALL-Escapesequenzen enthält. Außerdem werden Prozeduraufrufe als Batches ausgeführt, wenn gebundene Parameterarrays mit einer ODBC CALL-Escapesequenz verwendet werden. Angenommen, Sie verwenden entweder zeilenweise oder spaltenweise parameterbindungen so binden Sie ein Array mit fünf Elementen an die Parameter einer ODBC CALL SQL-Anweisung, wenn **SQLExecute** oder **SQLExecDirect** aufgerufen wird, der Treiber sendet einen einzelnen Batch mit fünf Prozeduraufrufen an den Server.  
  
## <a name="see-also"></a>Siehe auch  
 [Ausführen gespeicherter Prozeduren](../../relational-databases/native-client-odbc-stored-procedures/running-stored-procedures.md)  
  
  