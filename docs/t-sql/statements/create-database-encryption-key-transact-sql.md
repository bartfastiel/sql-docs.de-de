---
title: Erstellen Sie DATABASE ENCRYPTION KEY (Transact-SQL) | Microsoft Docs
ms.custom: 
ms.date: 08/24/2016
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- DATABASE_ENCRYPTION_KEY_TSQL
- ENCRYPTION_KEY_TSQL
- sql13.swb.dbencryptionkeyo.f1
- ENCRYPTION KEY
- DATABASE ENCRYPTION KEY
- CREATE_DATABASE_ENCRYPTION_KEY_TSQL
- CREATE DATABASE ENCRYPTION KEY
- sql13.swb.dbencryptionkeyg.f1
- CREATE DATABASE ENCRYPTION
- CREATE_DATABASE_ENCRYPTION_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- database encryption key
- CREATE DATABASE ENCRYPTION KEY statement
- database encryption key, create
ms.assetid: 2ee95a32-5140-41bd-9ab3-a947b9990688
caps.latest.revision: 30
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 559e85cf5ba8e565a6afc86d3537b476365bd980
ms.contentlocale: de-de
ms.lasthandoff: 09/01/2017

---
# <a name="create-database-encryption-key-transact-sql"></a>CREATE DATABASE ENCRYPTION KEY (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-pdw_md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-pdw-md.md)]

 Erstellt einen Verschlüsselungsschlüssel für eine Datenbank, der für die transparente Datenbankverschlüsselung verwendet wird. Weitere Informationen über transparente datenbankverschlüsselung finden Sie unter [transparente datenverschlüsselung &#40; TDE &#41; ](../../relational-databases/security/encryption/transparent-data-encryption.md).  
  
![Themenlinksymbol](../../database-engine/configure-windows/media/topic-link.gif "Topic link icon") [Transact-SQL Syntax Conventions (Transact-SQL-Syntaxkonventionen)](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```  
-- Syntax for SQL Server  

CREATE DATABASE ENCRYPTION KEY  
       WITH ALGORITHM = { AES_128 | AES_192 | AES_256 | TRIPLE_DES_3KEY }  
   ENCRYPTION BY SERVER   
    {  
        CERTIFICATE Encryptor_Name |  
        ASYMMETRIC KEY Encryptor_Name  
    }  
[ ; ]  
```  
  
```  
-- Syntax for Parallel Data Warehouse  

CREATE DATABASE ENCRYPTION KEY  
       WITH ALGORITHM = { AES_128 | AES_192 | AES_256 | TRIPLE_DES_3KEY }  
   ENCRYPTION BY SERVER CERTIFICATE Encryptor_Name   
[ ; ]  
```  
  
## <a name="arguments"></a>Argumente  
WITH ALGORITHM = { AES_128 | AES_192 | AES_256 | TRIPLE_DES_3KEY  }  
Gibt den Verschlüsselungsalgorithmus an, der für den Verschlüsselungsschlüssel verwendet wird.   
>  [!NOTE]
>    Ab SQL Server 2016 sind alle Algorithmen als AES_128, AES_192 und AES_256 als veraltet markiert. Um ältere Algorithmen zu verwenden (was nicht empfohlen wird), müssen Sie den Kompatibilitätsgrad zwischen Datenbanken auf höchsten 120 festlegen.  
  
Die Verschlüsselung durch SERVER Zertifikat Encryptor_Name  
Gibt den Namen der Verschlüsselung an, die zum Verschlüsseln des Verschlüsselungsschlüssels für die Datenbank verwendet wird.  
  
Verschlüsselung mit ASYMMETRISCHEN Schlüssel Encryptor_Name für SERVER  
Gibt den Namen des asymmetrischen Schlüssels an, der zum Verschlüsseln des Verschlüsselungsschlüssels für die Datenbank verwendet wird. Um den Verschlüsselungsschlüssel für die Datenbank mit einem asymmetrischen Schlüssel zu verschlüsseln, muss sich der asymmetrische Schlüssel auf einem erweiterbaren Schlüsselverwaltungsanbieter befinden.  
  
## <a name="remarks"></a>Hinweise  
Datenbank-Verschlüsselungsschlüssel ist erforderlich, bevor eine Datenbank verschlüsselt werden kann, mit *transparente Datenbankverschlüsselung* (TDE). Wenn eine Datenbank transparent verschlüsselt ist, so ist die gesamte Datenbank auf Dateiebene ohne spezielle Codeänderungen verschlüsselt. Das Zertifikat oder der asymmetrische Schlüssel, das bzw. der zum Verschlüsseln des Verschlüsselungsschlüssels für die Datenbank verwendet wird, muss sich in der master-Systemdatenbank befinden.  
  
Datenbankverschlüsselungsanweisungen sind nur für Benutzerdatenbanken zulässig.  
  
Der Verschlüsselungsschlüssel für die Datenbank kann nicht aus der Datenbank exportiert werden. Er ist nur für das System, für Benutzer, die Debugberechtigungen auf dem Server haben, und für Benutzer verfügbar, die Zugriff auf die Zertifikate zum Verschlüsseln und Entschlüssen des Verschlüsselungsschlüssels für die Datenbank haben.  
  
Der Verschlüsselungsschlüssel für die Datenbank muss nicht erneut generiert werden, wenn ein Datenbankbesitzer (DBO) geändert wird.  
  
Datenbank-Verschlüsselungsschlüssel wird automatisch erstellt, für eine [!INCLUDE[ssSDS](../../includes/sssds-md.md)] Datenbank. Sie müssen nicht zum Erstellen eines Schlüssels mit der CREATE DATABASE ENCRYPTION KEY-Anweisung.  
  
## <a name="permissions"></a>Berechtigungen  
Erfordert die CONTROL-Berechtigung für die Datenbank und die VIEW DEFINITION-Berechtigung für das Zertifikat oder den asymmetrischen Schlüssel, die zum Verschlüsseln des Verschlüsselungsschlüssels für die Datenbank verwendet werden.  
  
## <a name="examples"></a>Beispiele  
Weitere Beispiele zur Verwendung von TDE, finden Sie unter [transparente datenverschlüsselung &#40; TDE &#41; ](../../relational-databases/security/encryption/transparent-data-encryption.md), [Aktivieren von TDE in SQLServer mithilfe von EKM](../../relational-databases/security/encryption/enable-tde-on-sql-server-using-ekm.md), und [erweiterbare Schlüsselverwaltung mit Azure Key Vault &#40; SQLServer &#41; ](../../relational-databases/security/encryption/extensible-key-management-using-azure-key-vault-sql-server.md).  
  
Im folgenden Beispiel wird der Datenbank-Verschlüsselungsschlüssel mithilfe des `AES_256`-Algorithmus erstellt, und der private Schlüssel wird mit einem Zertifikat namens `MyServerCert` geschützt.  
  
```  
USE AdventureWorks2012;  
GO  
CREATE DATABASE ENCRYPTION KEY  
WITH ALGORITHM = AES_256  
ENCRYPTION BY SERVER CERTIFICATE MyServerCert;  
GO  
```  
  
## <a name="examples-includesspdwincludessspdw-mdmd"></a>Beispiele:[!INCLUDE[ssPDW](../../includes/sspdw-md.md)]  
Weitere Beispiele zur Verwendung von TDE, finden Sie unter [Transparent Data Encryption (SQL Server PDW)](http://msdn.microsoft.com/en-us/b82ad21d-09dd-43dd-8fab-bcf2c8c3ac6d).  
  
Im folgenden Beispiel wird der Datenbank-Verschlüsselungsschlüssel mithilfe des `AES_256`-Algorithmus erstellt, und der private Schlüssel wird mit einem Zertifikat namens `MyServerCert` geschützt.  
  
```  
-- Uses AdventureWorks  
  
CREATE DATABASE ENCRYPTION KEY  
WITH ALGORITHM = AES_256  
ENCRYPTION BY SERVER CERTIFICATE MyServerCert;  
GO  
```  
  
## <a name="see-also"></a>Siehe auch  
[Transparente Datenverschlüsselung &#40;TDE&#41;](../../relational-databases/security/encryption/transparent-data-encryption.md)   
[SQL Server-Verschlüsselung](../../relational-databases/security/encryption/sql-server-encryption.md)   
[Verschlüsselungsschlüssel für SQL Server und Datenbank &#40;Datenbankmodul&#41;](../../relational-databases/security/encryption/sql-server-and-database-encryption-keys-database-engine.md)   
[Verschlüsselungshierarchie](../../relational-databases/security/encryption/encryption-hierarchy.md)   
[ALTER DATABASE SET-Optionen &#40;Transact-SQL&#41;](../../t-sql/statements/alter-database-transact-sql-set-options.md)   
[ALTER DATABASE ENCRYPTION KEY &#40; Transact-SQL &#41;](../../t-sql/statements/alter-database-encryption-key-transact-sql.md)   
[DROP DATABASE ENCRYPTION KEY &#40; Transact-SQL &#41;](../../t-sql/statements/drop-database-encryption-key-transact-sql.md)   
[sys.dm_database_encryption_keys &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-database-encryption-keys-transact-sql.md)  
    
