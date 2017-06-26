---
title: "Reporting Services-Dokumentation für Entwickler | Microsoft Docs"
ms.custom: 
ms.date: 03/17/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- docset-sql-devref
- reporting-services-native
ms.tgt_pltfrm: 
ms.topic: reference
applies_to:
- SQL Server 2016 Preview
helpviewer_keywords:
- developer's guide [Reporting Services]
- Reporting Services, programming
- programming [Reporting Services]
ms.assetid: d8afa405-1012-4349-a72d-e10d94f8453d
caps.latest.revision: 21
author: guyinacube
ms.author: asaxton
manager: erikre
ms.translationtype: Machine Translation
ms.sourcegitcommit: 0eb007a5207ceb0b023952d5d9ef6d95986092ac
ms.openlocfilehash: 3704373a08b29a8f36ce843db5f67a860a04a47b
ms.contentlocale: de-de
ms.lasthandoff: 06/22/2017

---
# <a name="reporting-services-developer-documentation"></a>Reporting Services-Entwicklerdokumentation
  [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)][!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] enthält mehrere Programmierungsschnittstellen, die Sie in Ihren eigenen Anwendungen nutzen können. Sie können die vorhandenen Funktionen und Funktionen von [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] verwenden, um benutzerdefinierte Berichts- und Verwaltungstools in Websites und Windows-Anwendungen zu erstellen, oder Sie können die [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)]-Plattform erweitern.  
  
 Das Erweitern der [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)]-Plattform umfasst die Erstellung neuer Komponenten und Ressourcen, die für den Datenzugriff, die Berichtsübermittlung und vieles mehr verwendet werden können. Sie können diese Komponenten und Ressourcen in den Unternehmen vermarkten, die [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] in ihrer Organisation verwenden.  
  
> [!NOTE]  
>  [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] enthält Programmierbeispiele und Lernprogramme, die Ihnen den Einstieg erleichtern. Weitere Informationen finden Sie unter [Reporting Services Samples](https://msdn.microsoft.com/library/ms160954\(v=sql.110\).aspx) und [Entwicklerhandbuch: Lernprogramme (Reporting Services)](https://msdn.microsoft.com/library/aa337423\(v=sql.110\).aspx).  
  
## <a name="in-this-section"></a>In diesem Abschnitt  
 [Integrieren von Reporting Services in Anwendungen](../reporting-services/application-integration/integrating-reporting-services-into-applications.md)  
 Gibt eine Übersicht darüber, wie die Berichterstellung mithilfe von [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] in benutzerdefinierte Anwendungen integriert werden kann. Beschreibt, wann der direkte URL-Zugriff und wann der Webdienst für den Zugriff auf den Berichtsserver verwendet werden sollte.  
  
 [Berichtsserver-Webdienst](../reporting-services/report-server-web-service/report-server-web-service.md)  
 Über den Berichtsserver-Webdienst erhalten Sie Zugriff auf die kompletten Funktionen des Berichtsservers. Der Webdienst verwendet SOAP über HTTP und wurde als Kommunikationsschnittstelle zwischen den Clientprogrammen und dem Berichtsserver konzipiert. Der Webdienst und seine Methoden stellen die Funktionen des Berichtsservers zur Verfügung und ermöglichen die Erstellung benutzerdefinierter Tools für jeden Teil des gesamten Berichtslebenszyklus, von der Verwaltung bis zur Ausführung.  
  
 [URL-Zugriff &#40;SSRS&#41;](../reporting-services/url-access-ssrs.md)  
 [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] unterstützt einen vollständige Satz URL-basierter Anforderungen, über die Sie schnell und problemlos auf die Berichtsnavigation und -anzeige zugreifen können. Sie können diese Technologie zusammen mit dem Berichtsserver-Webdienst verwenden, um eine vollständige Berichtslösung in Ihre vorhandenen Geschäftsanwendungen zu integrieren. Der URL-Zugriff ist dann besonders sinnvoll, wenn Sie Berichte als Teil eines Internetportals integrieren oder wenn Sie Berichte über einen Webbrowser anzeigen.  
  
 [Reporting Services-Erweiterungen](../reporting-services/extensions/reporting-services-extensions.md)  
 Die modulare Architektur von [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] ermöglicht Erweiterungen. Eine verwaltete Code-API steht zur Verfügung, sodass Sie problemlos Erweiterungen entwickeln, installieren und verwalten können, die von vielen [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)]-Komponenten benötigt werden. Sie können Assemblys erstellen, indem die [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] und Hinzufügen neuer [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] Rendering, Sicherheit, Übermittlung und Datenverarbeitung Funktionalität, um den wachsenden betrieblichen Anforderungen zu erfüllen.  
  
 [Benutzerdefinierte Berichtselemente](../reporting-services/custom-report-items/custom-report-items.md)  
 Beschreibt, wie Sie benutzerdefinierte Elemente erstellen, um Funktionen zu RDL hinzuzufügen, oder wie Sie vorhandene Steuerelemente erweitern.  
  
 [Verwenden von benutzerdefinierten Assemblys mit Berichten](../reporting-services/custom-assemblies/using-custom-assemblies-with-reports.md)  
 Beschreibt, wie benutzerdefinierte Assemblys mit Berichten verwendet werden, indem Codeverweise in die Berichtsdefinition aufgenommen werden.  
  
 [Zugriff auf den Reporting Services-WMI-Anbieter](../reporting-services/tools/access-the-reporting-services-wmi-provider.md)  
 Beschreibt, wie Sie den [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)]-WMI-Anbieter zum Verwalten von Berichtsserverbereitstellungen verwenden.  
  
## <a name="see-also"></a>Siehe auch  
 [Reporting Services &#40;SSRS&#41;](../reporting-services/create-deploy-and-manage-mobile-and-paginated-reports.md)   
 [Report Definition Language &#40; SSRS &#41;](../reporting-services/reports/report-definition-language-ssrs.md)   
 [Technische Referenz &#40;SSRS&#41;](../reporting-services/technical-reference-ssrs.md)   
 [Sichere Entwicklung &#40; Reporting Services &#41;](../reporting-services/extensions/secure-development/secure-development-reporting-services.md)  
  
  