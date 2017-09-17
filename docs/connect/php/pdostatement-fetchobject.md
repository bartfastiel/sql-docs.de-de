---
title: PDOStatement::fetchObject | Microsoft Docs
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 71ad1932-cab3-4c29-8950-f5e82547d3b5
caps.latest.revision: 10
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: ef6da712209e34e6fcd62ca9436ac16cf3342fea
ms.contentlocale: de-de
ms.lasthandoff: 09/09/2017

---
# <a name="pdostatementfetchobject"></a>PDOStatement::fetchObject
[!INCLUDE[Driver_PHP_Download](../../includes/driver_php_download.md)]

Ruft die nächste Zeile als Objekt ab.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
mixed PDOStatement::fetchObject([ $class_name[,$ctor_args ]] )  
```  
  
#### <a name="parameters"></a>Parameter  
$*CLASS_NAME*: eine optionale Zeichenfolge, die den Namen der zu erstellenden Klasse angibt. Der Standardwert ist „stdClass“.  
  
$*Ctor_args*: ein optionales Array mit Argumenten für einen benutzerdefinierten Klassenkonstruktor.  
  
## <a name="return-value"></a>Rückgabewert  
Bei Erfolg wird ein Objekt mit einer Instanz der Klasse zurückgegeben. Eigenschaften sind Spalten zugeordnet. Gibt bei einem Fehler „false“ zurück.  
  
## <a name="remarks"></a>Hinweise  
Unterstützung für PDO wurde in Version 2.0 von [!INCLUDE[ssDriverPHP](../../includes/ssdriverphp_md.md)]hinzugefügt.  
  
## <a name="example"></a>Beispiel  
  
```  
<?php  
   $server = "(local)";  
   $database = "AdventureWorks";  
   $conn = new PDO( "sqlsrv:server=$server ; Database = $database", "", "");  
  
   $stmt = $conn->query( "select * from Person.ContactType where ContactTypeID < 5 " );  
   $result = $stmt->fetchObject();  
   print $result->Name;  
?>  
```  
  
## <a name="see-also"></a>Siehe auch  
[PDOStatement-Klasse](../../connect/php/pdostatement-class.md)  
[PDO](http://go.microsoft.com/fwlink/?LinkID=187441)  
  
