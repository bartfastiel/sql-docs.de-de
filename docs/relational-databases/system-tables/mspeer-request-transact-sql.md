---
title: MSpeer_request (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- MSpeer_request
- MSpeer_request_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- MSpeer_request system table
ms.assetid: ed048c46-7a2f-4ad0-bc7c-c2d65e83b4fb
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 904919bfac6dc9fc0c5bf638605d363eba5a68f2
ms.sourcegitcommit: ceb7e1b9e29e02bb0c6ca400a36e0fa9cf010fca
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/03/2018
ms.locfileid: "52796260"
---
# <a name="mspeerrequest-transact-sql"></a>MSpeer_request (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Die MSpeer_request-Tabelle wird bei der Peer-zu-Peer-Replikation verwendet, um Statusanforderungen für eine bestimmte Veröffentlichung nachzuverfolgen. Diese Tabelle wird in der Veröffentlichungsdatenbank gespeichert.  
  
|Spaltenname|Datentyp|Description|  
|-----------------|---------------|-----------------|  
|id|**int**|Identifiziert eine Anforderung.|  
|publication|**sysname**|Name der Veröffentlichung, für die die Statusanforderung initiiert wurde.|  
|sent_date|**datetime**|Datum und Uhrzeit der Initiierung der Statusanforderung.|  
|description|**nvarchar(4000)**|Benutzerdefinierte Informationen, mit denen einzelne Statusanforderungen identifiziert werden können.|  
  
## <a name="see-also"></a>Siehe auch  
 [Replikationstabellen &#40;Transact-SQL&#41;](../../relational-databases/system-tables/replication-tables-transact-sql.md)   
 [Replikationssichten &#40;Transact-SQL&#41;](../../relational-databases/system-views/replication-views-transact-sql.md)  
  
  
