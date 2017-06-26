---
title: "Übergeben von Geräteinformationseinstellungen an Renderingerweiterungen | Microsoft Docs"
ms.custom: 
ms.date: 03/16/2017
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
- device information settings [Reporting Services]
- Render method
- Report Server Web service, device information settings
- Web service [Reporting Services], device information settings
- XML Web service [Reporting Services], device information settings
- passing device information [Reporting Services]
- rendering extensions [Reporting Services], device information settings
- rendering [Reporting Services], settings
- device information settings [Reporting Services], about device information settings
- extensions [Reporting Services], device information settings
ms.assetid: fe718939-7efe-4c7f-87cb-5f5b09caeff4
caps.latest.revision: 47
author: sabotta
ms.author: asaxton
manager: erikre
ms.translationtype: Machine Translation
ms.sourcegitcommit: 0eb007a5207ceb0b023952d5d9ef6d95986092ac
ms.openlocfilehash: da897abf38fb1c6e89178a9314189890b88eab87
ms.contentlocale: de-de
ms.lasthandoff: 06/13/2017

---
# <a name="passing-device-information-settings-to-rendering-extensions"></a>Übergeben von Geräteinformationseinstellungen an Renderingerweiterungen
  In [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)]werden Geräteinformationseinstellungen zum Übergeben von Renderingparametern an eine Renderingerweiterung verwendet. Einstellungen im Berichtsserver-Webdienst werden als **DeviceInfo** -XML-Element übergeben und vom Berichtsserver verarbeitet. Da Geräteinformationseinstellungen Standardwerte besitzen, werden sie als optionale Argumente für das Rendern angesehen. Sie können jedoch Geräteinformationseinstellungen verwenden, um das Rendern anzupassen und die vom Server angegebenen Standardwerte zu überschreiben.  
  
 Die Geräteinformationseinstellungen können auf verschiedene Weisen eingestellt werden. Für eine programmgesteuerte Einstellung können Sie die Render-Methode verwenden. Wenn Sie über die URL eines Berichts auf den Bericht zugreifen, können Sie Geräteinformationen als URL-Parameter festlegen. Sie können die Geräteinformationseinstellungen auch in der Konfigurationsdatei von [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] bearbeiten, um Renderingparameter global festzulegen. Weitere Informationen zum Festlegen von renderingparametern Global finden Sie unter [Anpassen von Parametern für Renderingerweiterungen in der Datei RSReportServer.Config](../../../reporting-services/customize-rendering-extension-parameters-in-rsreportserver-config.md).  
  
## <a name="passing-device-information-using-the-render-method"></a>Übergeben von Geräteinformationen mit der Render-Methode  
 Verwenden Sie die **M:Microsoft.WSSUX.ReportingServicesWebService.RSExecutionService2005.ReportExecutionService.Render(System.String,System.String,System.String@,System.String@,System.String@,Microsoft.WSSUX.ReportingServicesWebService.RSExecutionService2005.Warning[]@,System.String[]@)** -Methode, um Geräteinformationen an eine Renderingerweiterung zu übergeben. Beispielsweise kann die folgende XML-Zeichenfolge übergeben werden, um die <xref:ReportExecution2005.ReportExecutionService.Render%2A> Methode, um ein HTML-Fragment beim Rendern in HTML zu erstellen.  
  
```  
<DeviceInfo>  
   <HTMLFragment>True</HTMLFragment>  
</DeviceInfo>  
```  
  
 Wenn ein Bericht als HTML-Fragment gerendert wird, befindet sich der Inhalt des Berichts in einem TABLE-Element, ohne ein HTML- oder ein BODY-Element zu verwenden. Verwenden Sie das HTML-Fragment, um den Bericht in ein bestehendes HTML-Dokument einzubinden. Weitere Informationen zu Geräteinformationseinstellungen für HTML-Ausgabe finden Sie unter [HTML Device Information Settings](../../../reporting-services/html-device-information-settings.md).  
  
## <a name="passing-device-information-using-url-access"></a>Übergeben von Geräteinformationen mit URL-Zugriff  
 Die Geräteinformationen können auch mithilfe eines URL-Zugriffs übergeben werden. Dabei werden Geräteinformationseinstellungen als URL-Parameter übergeben. Die folgende URL-Zugriffszeichenfolge kann an den Berichtsserver übergeben werden, um einen gerenderten Bericht ohne die Symbolleiste des HTML-Viewers zu generieren.  
  
```  
http://<Server Name>/reportserver?/SampleReports/Sales Order Detail&rs:Command=Render&rs:Format=HTML4.0&rc:Toolbar=False  
```  
  
 Weitere Informationen finden Sie unter [angeben von Geräteinformationseinstellungen in einer URL](../../../reporting-services/specify-device-information-settings-in-a-url.md).  
  
## <a name="see-also"></a>Siehe auch  
 [Die Geräteinformationseinstellungen zum Rendern von Erweiterungen &#40; Reporting Services &#41;](../../../reporting-services/device-information-settings-for-rendering-extensions-reporting-services.md)   
 [Anpassen der Parameter für Renderingerweiterungen in "rsreportserver.config"](../../../reporting-services/customize-rendering-extension-parameters-in-rsreportserver-config.md)   
 [Erstellen von Anwendungen mit dem Webdienst und .NET Framework](../../../reporting-services/report-server-web-service/net-framework/building-applications-using-the-web-service-and-the-net-framework.md)  
  
  