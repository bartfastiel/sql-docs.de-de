---
title: Sp_apply_job_to_targets (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_apply_job_to_targets
- sp_apply_job_to_targets_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sp_apply_job_to_targets
ms.assetid: 4a3e9173-7e3c-4100-a9ac-2f5d2c60a8b0
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 1583f6de4938451b03eabfb7c9425120fa37f2fc
ms.sourcegitcommit: 2429fbcdb751211313bd655a4825ffb33354bda3
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/28/2018
ms.locfileid: "52537835"
---
# <a name="spapplyjobtotargets-transact-sql"></a>sp_apply_job_to_targets (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Wendet einen Auftrag auf einen oder mehrere Zielserver oder auf die Zielserver an, die einer oder mehreren Zielservergruppen angehören.  
  
 ![Themenlinksymbol](../../database-engine/configure-windows/media/topic-link.gif "Topic link icon") [Transact-SQL Syntax Conventions (Transact-SQL-Syntaxkonventionen)](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```  
  
sp_apply_job_to_targets { [ @job_id = ] job_id | [ @job_name = ] 'job_name' }  
     [ , [ @target_server_groups = ] 'target_server_groups' ]   
     [ , [ @target_servers = ] 'target_servers' ]   
     [ , [ @operation = ] 'operation' ]   
```  
  
## <a name="arguments"></a>Argumente  
 [ **@job_id =**] *job_id*  
 Die ID des Auftrags, der für die angegebenen Zielserver oder Zielservergruppen ausgeführt werden sollen. *Job_id* ist **Uniqueidentifier**, hat den Standardwert NULL.  
  
 [  **@job_name =**] **"**_Job_name_**"**  
 Der Name des Auftrags, der für die angegebenen Zielserver oder Zielservergruppen ausgeführt werden sollen. *Job_name* ist **Sysname**, hat den Standardwert NULL.  
  
> [!NOTE]  
>  Entweder *Job_id* oder *Job_name* muss angegeben werden, aber beide Angaben sind nicht möglich.  
  
 [  **@target_server_groups =**] **"**_Target_server_groups_**"**  
 Eine durch Trennzeichen getrennte Liste von Zielservergruppen, für die der angegebene Auftrag ausgeführt werden soll. *Target_server_groups* ist **nvarchar(2048)**, hat den Standardwert NULL.  
  
 [  **@target_servers=** ] **"**_target_server_**"**  
 Eine durch Trennzeichen getrennte Liste von Zielservern, für die der angegebene Auftrag ausgeführt werden soll. *target_server*ist **nvarchar(2048)**, hat den Standardwert NULL.  
  
 [  **@operation=** ] **"**_Vorgang_**"**  
 Gibt an, ob der angegebene Auftrag für die genannten Zielserver oder Zielservergruppen ausgeführt oder davon entfernt werden soll. *Vorgang*ist **vom Datentyp varchar(7)**, hat den Standardwert übernehmen. Gültige Vorgänge sind **übernehmen** und **entfernen**.  
  
## <a name="return-code-values"></a>Rückgabecodewerte  
 **0** (Erfolg) oder **1** (Fehler)  
  
## <a name="remarks"></a>Hinweise  
 **Sp_apply_job_to_targets** bietet eine einfache Möglichkeit, anzuwenden (oder entfernen) ein Auftrags auf mehrere Zielserver aus, und ist eine Alternative zum Aufruf **Sp_add_jobserver** (oder **Sp_delete_jobserver**) einmal für jeden erforderlichen Zielserver.  
  
## <a name="permissions"></a>Berechtigungen  
 Nur Mitglieder der **Sysadmin** -Serverrolle kann diese Prozedur ausführen.  
  
## <a name="examples"></a>Beispiele  
 Im folgenden Beispiel wird der zuvor erstellte Auftrag `Backup Customer Information` auf alle Zielserver in der Gruppe `Servers Maintaining Customer Information` angewendet.  
  
```  
USE msdb ;  
GO  
  
EXEC dbo.sp_apply_job_to_targets  
    @job_name = N'Backup Customer Information',  
    @target_server_groups = N'Servers Maintaining Customer Information',   
    @operation = N'APPLY' ;  
GO  
```  
  
## <a name="see-also"></a>Siehe auch  
 [sp_add_jobserver &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-add-jobserver-transact-sql.md)   
 [sp_delete_jobserver &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-delete-jobserver-transact-sql.md)   
 [sp_remove_job_from_targets &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-remove-job-from-targets-transact-sql.md)   
 [Gespeicherte Systemprozeduren &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
