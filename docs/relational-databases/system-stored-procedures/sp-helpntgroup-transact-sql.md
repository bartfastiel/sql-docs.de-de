---
title: Sp_helpntgroup (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_helpntgroup
- sp_helpntgroup_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sp_helpntgroup
ms.assetid: 02b4f7c1-480a-436c-8bae-7a2488be45d2
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: c23e80cf3024b238595785f0976f52ae41c8defc
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/01/2018
ms.locfileid: "47739768"
---
# <a name="sphelpntgroup-transact-sql"></a>sp_helpntgroup (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Meldet Informationen zu Windows-Gruppen mit Konten in der aktuellen Datenbank.  
  
 ![Themenlinksymbol](../../database-engine/configure-windows/media/topic-link.gif "Topic link icon") [Transact-SQL Syntax Conventions (Transact-SQL-Syntaxkonventionen)](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```  
  
sp_helpntgroup [ [ @ntname= ] 'name' ]   
```  
  
## <a name="arguments"></a>Argumente  
 [ **@ntname =** ] **'***name***'**  
 Der Name der Windows-Gruppe. *name* ist vom Datentyp **sysname**und hat den Standardwert NULL. *name* muss eine gültige Windows-Gruppe mit Zugriff auf die aktuelle Datenbank sein. Wird *name* nicht angegeben, umfasst die Ausgabe alle Windows-Gruppen mit Zugriff auf die aktuelle Datenbank.  
  
## <a name="return-code-values"></a>Rückgabecodewerte  
 0 (Erfolg) oder 1 (Fehler)  
  
## <a name="result-sets"></a>Resultsets  
  
|Spaltenname|Datentyp|Description|  
|-----------------|---------------|-----------------|  
|**NTGroupName**|**sysname**|Name der Windows-Gruppe.|  
|**NTGroupId**|**smallint**|Gruppenbezeichner (ID).|  
|**SID**|**varbinary(85)**|Sicherheits-ID (SID) von **NTGroupName**.|  
|**HasDbAccess**|**int**|1 = Windows-Gruppe hat Zugriffsberechtigungen für die Datenbank.|  
  
## <a name="remarks"></a>Hinweise  
 Um eine Liste der finden Sie unter den [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Rollen in der aktuellen Datenbank **Sp_helprole**.  
  
## <a name="permissions"></a>Berechtigungen  
 Erfordert die Mitgliedschaft in der **public** -Rolle.  
  
## <a name="examples"></a>Beispiele  
 Im folgenden Beispiel wird eine Liste der Windows-Gruppen mit Zugriff auf die aktuelle Datenbank ausgegeben.  
  
```  
EXEC sp_helpntgroup;  
```  
  
## <a name="see-also"></a>Siehe auch  
 [Security Stored Procedures &#40;Transact-SQL&#41; (Gespeicherte Sicherheitsprozeduren (Transact-SQL))](../../relational-databases/system-stored-procedures/security-stored-procedures-transact-sql.md)   
 [sp_grantdbaccess &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-grantdbaccess-transact-sql.md)   
 [Sp_helprole &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-helprole-transact-sql.md)   
 [sp_revokedbaccess &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-revokedbaccess-transact-sql.md)   
 [Gespeicherte Systemprozeduren &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
