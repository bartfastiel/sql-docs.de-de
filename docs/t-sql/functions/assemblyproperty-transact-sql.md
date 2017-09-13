---
title: ASSEMBLYPROPERTY (Transact-SQL) | Microsoft Docs
ms.custom: 
ms.date: 07/24/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- ASSEMBLYPROPERTY_TSQL
- ASSEMBLYPROPERTY
dev_langs:
- TSQL
helpviewer_keywords:
- ASSEMBLYPROPERTY statement
- assemblies [CLR integration], properties
ms.assetid: cf03d1b1-724c-48bf-a8df-3fe2586b150a
caps.latest.revision: 40
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 9556834a173302e19358f5333b059d7b4f902519
ms.contentlocale: de-de
ms.lasthandoff: 09/01/2017

---
# <a name="assemblyproperty-transact-sql"></a>ASSEMBLYPROPERTY (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx_md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

Gibt Informationen zu einer Eigenschaft einer Assembly zurück.
  
![Themenlinksymbol](../../database-engine/configure-windows/media/topic-link.gif "Topic link icon") [Transact-SQL Syntax Conventions (Transact-SQL-Syntaxkonventionen)](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)
  
## <a name="syntax"></a>Syntax  
  
```sql
ASSEMBLYPROPERTY('assembly_name', 'property_name')  
```  
  
## <a name="arguments"></a>Argumente  
*AssemblyName*  
Der Name der Assembly.
  
*Eigenschaftsname*  
Der Name einer Eigenschaft, zu der Informationen abgerufen werden sollen. *Property_name* kann einen der folgenden Werte sein.
  
|Wert|Description|  
|---|---|
|**CultureInfo**|Gebietsschema der Assembly.|  
|**PublicKey**|Öffentlicher Schlüssel oder öffentlicher Schlüsseltoken der Assembly.|  
|**MvID**|Vollständige, vom Compiler generierte Versions-ID der Assembly.|  
|**VersionMajor**|Komponente für die Angabe der Hauptversion (erster Teil) der aus vier Teilen bestehenden Versions-ID der Assembly.|  
|**VersionMinor**|Komponente für die Angabe der Nebenversion (zweiter Teil) der aus vier Teilen bestehenden Versions-ID der Assembly.|  
|**VersionBuild**|Komponente für die Angabe der Buildnummer (dritter Teil) der aus vier Teilen bestehenden Versions-ID der Assembly.|  
|**VersionRevision**|Komponente für die Angabe der Revisionsnummer (vierter Teil) der aus vier Teilen bestehenden Versions-ID der Assembly.|  
|**SimpleName**|Einfacher Name der Assembly.|  
|**Aufbau**|Prozessorarchitektur der Assembly.|  
|**CLRName**|Kanonische Zeichenfolge, die den einfachen Namen, die Versionsnummer, die Kultur, den öffentlichen Schlüssel und die Architektur der Assembly codiert. Durch diesen Wert wird die CLR-seitige Assembly (Common Language Runtime) eindeutig identifiziert.|  
  
## <a name="return-type"></a>Rückgabetyp
**sql_variant**
  
## <a name="examples"></a>Beispiele  
Im folgenden Beispiel wird davon ausgegangen, dass eine `HelloWorld`-Assembly in der [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)]-Datenbank registriert ist. Weitere Informationen finden Sie unter [Hello World-Beispiel](http://msdn.microsoft.com/library/fed6c358-f5ee-4d4c-9ad6-089778383ba7).
  
```sql
USE AdventureWorks2012;  
GO  
SELECT ASSEMBLYPROPERTY ('HelloWorld' , 'PublicKey');  
```  
  
## <a name="see-also"></a>Siehe auch
[CREATE ASSEMBLY &#40;Transact-SQL&#41;](../../t-sql/statements/create-assembly-transact-sql.md)  
[DROP ASSEMBLY &#40;Transact-SQL&#41;](../../t-sql/statements/drop-assembly-transact-sql.md)
  
  
