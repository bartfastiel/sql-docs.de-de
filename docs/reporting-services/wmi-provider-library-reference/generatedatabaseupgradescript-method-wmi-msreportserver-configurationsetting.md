---
title: "GenerateDatabaseUpgradeScript-Methode (WMI: MSReportServer_ConfigurationSetting) | Microsoft Docs"
ms.custom: ""
ms.date: "12/09/2016"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "reporting-services-sharepoint"
  - "reporting-services-native"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "GenerateDatabaseUpgradeScript (WMI MSReportServer_ConfigurationSetting Class)"
apilocation: 
  - "reportingservices.mof"
apitype: "MOFDef"
helpviewer_keywords: 
  - "GenerateDatabaseUpgradeScript-Methode"
ms.assetid: 88534e8e-2877-41cd-b5c2-b1d33a0fd203
caps.latest.revision: 22
author: "guyinacube"
ms.author: "asaxton"
manager: "erikre"
---
# GenerateDatabaseUpgradeScript-Methode (WMI: MSReportServer_ConfigurationSetting)
  Generiert ein Skript, das verwendet werden kann, um ein Upgrade der Berichtsserver-Datenbank auf das [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] -Schema durchzuführen.  
  
## Syntax  
  
```vb  
Public Sub GenerateDatabaseUpgradeScript(DatabaseName as String, _  
    ServerVersion as String, ByRef Script as String, _  
    ByRef HRESULT as Int32)  
```  
  
```csharp  
public void GenerateDatabaseUpgradeScript (string DatabaseName,   
    string ServerVersion, out string Script,   
    out Int32 HRESULT);  
```  
  
## Parameter  
 *Databasename*  
 Eine Zeichenfolge, die den Namen der zu aktualisierenden Berichtsserver-Datenbank enthält  
  
 *ServerVersion*  
 Eine Zeichenfolge, die die Version des Berichtsservers enthält  
  
 *Skript*  
 [out] Eine Zeichenfolge, die das generierte SQL-Skript enthält  
  
 *HRESULT*  
 [out] Wert, der angibt, ob der Aufruf erfolgreich war oder zu einem Fehler geführt hat.  
  
## Rückgabewert  
 Gibt *HRESULT* zurück, wodurch der Erfolg oder das Fehlschlagen des Methodenaufrufs angegeben wird. Der Wert 0 (null) gibt an, dass der Methodenaufruf erfolgreich war. Ein Wert ungleich 0 (null) gibt an, dass ein Fehler aufgetreten ist.  
  
## Hinweise  
 Das generierte Skript unterstützt [!INCLUDE[ssVersion2000](../../includes/ssversion2000-md.md)], [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)]und [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)].  
  
## Anforderungen  
 **Namespace:** [!INCLUDE[ssRSWMInmspcA](../../includes/ssrswminmspca-md.md)]  
  
## Siehe auch  
 [MSReportServer_ConfigurationSetting-Member](../../reporting-services/wmi-provider-library-reference/msreportserver-configurationsetting-members.md)  
  
  