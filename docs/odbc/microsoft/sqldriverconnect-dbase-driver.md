---
title: SQLDriverConnect (dBASE-Treiber) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- DBase driver [ODBC], SQLDriverConnect
- SQLDriverConnect function [ODBC], dBASE Driver
ms.assetid: c837aa31-068e-4fa3-bc00-aae09bec21de
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 3e4eeaa7ba710814bfeb8c5b4f5aa0dbd2d30ef7
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/01/2018
ms.locfileid: "47690878"
---
# <a name="sqldriverconnect-dbase-driver"></a>SQLDriverConnect (dBASE-Treiber)
> [!NOTE]  
>  Dieses Thema enthält die dBASE-Treiber-spezifische Informationen. Allgemeine Informationen zu dieser Funktion finden Sie unter den entsprechenden Themen unter [ODBC-API-Referenz](../../odbc/reference/syntax/odbc-api-reference.md).  
  
 **SQLDriverConnect** können Sie auf einen Treiber zu verbinden, ohne das Erstellen einer Datenquelle (DSN).  
  
 Die folgenden Schlüsselwörter werden in der Verbindungszeichenfolge für alle Treiber unterstützt: **DSN**, **DBQ**, und **FIL**.  
  
 Wenn die Paradox-Treiber, verwendet wird nachdem eine kennwortgeschützte Datei von einem Benutzer geöffnet wurde, sind andere Benutzer nicht zulässig, um die gleiche Datei zu öffnen.  
  
 Die folgende Tabelle zeigt die minimale Schlüsselwörter, die für die Verbindung mit jeder Treiber und enthält ein Beispiel der Schlüsselwort-Wert-Paare, die mit verwendet **SQLDriverConnect**. Eine vollständige Liste der Werte von DRIVERID, finden Sie unter [SQLConfigDataSource](../../odbc/microsoft/sqlconfigdatasource-dbase-driver.md).  
  
> [!NOTE]  
>  Wenn es sich bei DBQ oder Wert für die dBASEdriver nicht angegeben ist, werden die Treiber in das aktuelle Verzeichnis verbunden.  
  
|Treiber|Schlüsselwörter, die erforderlich sind|Beispiele|  
|------------|-----------------------|--------------|  
|dBASE|DriverID-Treiber|Driver = {Microsoft-dBASE-Treiber * (.DBF)}; DBQ = "c:\Temp"; DriverID 277 =|
