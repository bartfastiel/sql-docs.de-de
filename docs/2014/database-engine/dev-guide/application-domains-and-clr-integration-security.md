---
title: Anwendungsdomänen und Sicherheit der CLR-Integration | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- database-engine
- docset-sql-devref
ms.topic: reference
helpviewer_keywords:
- security [CLR integration]
- application domains [CLR integration]
ms.assetid: 54ee904e-e21a-4ee7-b4ad-a6f6f71bd473
author: mashamsft
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 34814ab19f96ff7e6232638ef4446b05b5b41ba3
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/02/2018
ms.locfileid: "48102344"
---
# <a name="application-domains-and-clr-integration-security"></a>Anwendungsdomänen und Sicherheit der CLR-Integration
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] lädt Assemblys, die demselben Besitzer in derselben Anwendungsdomäne gehören. Bei einem Assemblysatz, die in derselben Anwendungsdomäne ausgeführt wird, können sich Assemblys während der Ausführung untereinander erkennen, indem sie den Reflektions-APIs von .NET Framework oder andere Verfahren anwenden, und können sich so auf spät gebundene Weise aufrufen. Da diese Aufrufe unter Assemblys stattfinden, die denselben Besitzer haben, werden dafür keine [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Berechtigungen überprüft. Das Platzierungsschema von Assemblys in Anwendungsdomänen wurde hauptsächlich mit Blick auf Skalierbarkeit, Sicherheit und Isolierung konzipiert und wird möglicherweise in zukünftigen Versionen geändert. Sie sollten sich daher nicht darauf verlassen, Assemblys mit später Bindung in derselben Anwendungsdomäne zu finden.  
  
## <a name="see-also"></a>Siehe auch  
 [Sicherheit der CLR-Integration](../../relational-databases/clr-integration/security/clr-integration-security.md)  
  
  
