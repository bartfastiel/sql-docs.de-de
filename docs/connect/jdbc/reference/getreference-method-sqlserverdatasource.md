---
title: GetReference-Methode (SQLServerDataSource) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerDataSource.getReference
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: b3fb1a97-86ee-4977-adca-c35ae199dbb3
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 33a1b82b5855447df7e9b55c7506e87f6ffb8f2a
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MTE75
ms.contentlocale: de-DE
ms.lasthandoff: 10/01/2018
ms.locfileid: "47825993"
---
# <a name="getreference-method-sqlserverdatasource"></a>getReference-Methode (SQLServerDataSource)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Gibt einen Verweis auf dieses [SQLServerDataSource](../../../connect/jdbc/reference/sqlserverdatasource-class.md)-Objekt zurück.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
public javax.naming.Reference getReference()  
```  
  
## <a name="return-value"></a>Rückgabewert  
 Ein Verweis-Objekt.  
  
## <a name="remarks"></a>Remarks  
 Diese GetReference-Methode wird von der GetReference-Methode in der javax.naming.Referenceable-Schnittstelle angegeben.  
  
 Vor dem JDBC-Treiber 3.0 für [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] war beim Aufruf von „SQLServerDataSource.setTrustStorePassword“ für ein SQLServerDataSource-Objekt das Kennwort im von SQLServerDataSource.getReference zurückgegebenen Objekt enthalten, und mit dem Objekt konnten zusätzliche Verbindungen hergestellt werden. In JDBC Driver 3.0 muss das Kennwort für das von "SQLServerDataSource.getReference" zurückgegebene Objekt festgelegt werden, bevor Verbindungen mit dem Objekt hergestellt werden.  
  
 Wenn Sie "SQLServerDataSource.setTrustStorePassword" vor dem Binden der Datenquelleneigenschaften festlegen, muss "SQLServerDataSource.setTrustStorePassword" vor dem Herstellen der Verbindung aufgerufen werden. Beispiel:  
  
```  
ctx = new InitialContext(System.getProperties());  
  
SQLServerDataSource ds1 = (SQLServerDataSource) ctx.lookup(jndiName);  
  
ds1.setTrustStorePassword("XXXXX");  
Connection con = ds1.getConnection("user", "XXXXXX");  
  
ctx.rebind(jndiName, ds1);  
SQLServerDataSource ds2 = (SQLServerDataSource) ctx.lookup(jndiName);  
ds2.setTrustStorePassword("XXXXX");   // reset the truststore password  
con = ds2.getConnection("user", "XXXXXX");   // provide userid and password again  
```  
  
## <a name="see-also"></a>Weitere Informationen finden Sie unter  
 [SQLServerDataSource-Elemente](../../../connect/jdbc/reference/sqlserverdatasource-members.md)   
 [SQLServerDataSource-Klasse](../../../connect/jdbc/reference/sqlserverdatasource-class.md)  
  
  
