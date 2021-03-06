---
title: WillChangeField- und FieldChangeComplete-Ereignis (ADO) | Microsoft-Dokumentation
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- FieldChangeComplete
- Recordset::WillChangeField
- Recordset::FieldChangeComplete
- WillChangeField
helpviewer_keywords:
- WillChangeField event [ADO]
- fieldchangecomplete event [ADO]
ms.assetid: 3e49fb89-c45b-4d39-823e-3cc887c59b37
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: f046a3a33e05228ab5e49116bc46eb9451f43129
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/01/2018
ms.locfileid: "47673658"
---
# <a name="willchangefield-and-fieldchangecomplete-events-ado"></a>WillChangeField- und FieldChangeComplete-Ereignis (ADO)
Die **WillChangeField** Ereignis wird immer dann aufgerufen, bevor Sie ein ausstehender Vorgang ändert sich den Wert einer oder mehreren [Feld](../../../ado/reference/ado-api/field-object.md) Objekte in der [Recordset](../../../ado/reference/ado-api/recordset-object-ado.md). Die **FieldChangeComplete** -Ereignis wird aufgerufen, nachdem sich der Wert von einem oder mehreren **Feld** -Quellobjekten geändert wurde.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
WillChangeField cFields, Fields, adStatus, pRecordset  
FieldChangeComplete cFields, Fields, pError, adStatus, pRecordset  
```  
  
#### <a name="parameters"></a>Parameter  
 *cFields*  
 Ein **lange** , der angibt, dass der Anzahl der **Feld** Objekte im *Felder*.  
  
 *Fields*  
 Für **WillChangeField**, *Felder* -Parameter ist ein Array von **Varianten** , enthält **Feld** Objekte mit den ursprünglichen Werten. Für **FieldChangeComplete**, *Felder* -Parameter ist ein Array von **Varianten** , enthält **Feld** Objekte mit den geänderten Werten .  
  
 *pError*  
 Ein [Fehler](../../../ado/reference/ado-api/error-object.md) Objekt. Es wird beschrieben, den aufgetretenen Wenn der Wert des *AdStatus* ist **AdStatusErrorsOccurred**; andernfalls ist es nicht festgelegt.  
  
 *adStatus*  
 Ein [EventStatusEnum](../../../ado/reference/ado-api/eventstatusenum.md) Statuswert.  
  
 Wenn **WillChangeField** wird aufgerufen, wird dieser Parameter auf festgelegt **AdStatusOK** , wenn der Vorgang, der das Ereignis ausgelöst wurde erfolgreich war. Es wird festgelegt, um **AdStatusCantDeny** Wenn dieses Ereignis auf Abbruch des ausstehenden Vorgangs anfordern kann.  
  
 Wenn **FieldChangeComplete** wird aufgerufen, wird dieser Parameter auf festgelegt **AdStatusOK** , wenn der Vorgang, der das Ereignis ausgelöst wurde erfolgreich war, oder mit **AdStatusErrorsOccurred** Wenn der Vorgang ist fehlgeschlagen.  
  
 Vor dem **WillChangeField** zurückgegeben wird, legen Sie diesen Parameter zu **AdStatusCancel** auf den Abbruch der Anforderung des ausstehenden Vorgangs.  
  
 Vor dem **FieldChangeComplete** zurückgegeben wird, legen Sie diesen Parameter zu **AdStatusUnwantedEvent** , nachfolgende Benachrichtigungen zu verhindern.  
  
 *pRecordset*  
 Ein **Recordset** Objekt. Die **Recordset** für die dieses Ereignis aufgetreten ist.  
  
## <a name="remarks"></a>Hinweise  
 Ein **WillChangeField** oder **FieldChangeComplete** Ereignis kann eintreten, wenn die [Wert](../../../ado/reference/ado-api/value-property-ado.md) -Eigenschaft ab, und rufen die [Update](../../../ado/reference/ado-api/update-method.md) Methode mit Arrayparametern Feld und dem Wert.  
  
## <a name="see-also"></a>Siehe auch  
 [ADO-Ereignismodell – Beispiel (VC++)](../../../ado/reference/ado-api/ado-events-model-example-vc.md)   
 [ADO-Ereignishandler – Zusammenfassung](../../../ado/guide/data/ado-event-handler-summary.md)
