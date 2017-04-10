---
title: "&#196;ndern der f&#252;r Englisch (USA) und Englisch (Gro&#223;britannien) verwendeten W&#246;rtertrennung | Microsoft Docs"
ms.custom: ""
ms.date: "03/14/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dbe-search"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 6b5d2177-db98-47f5-b32e-4b80a2f74ffe
caps.latest.revision: 10
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 10
---
# &#196;ndern der f&#252;r Englisch (USA) und Englisch (Gro&#223;britannien) verwendeten W&#246;rtertrennung
  [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] installiert eine neue Version (Version 14.0.4999.1038) der Wörtertrennung und der Wortstammerkennung für Englisch, die die frühere Version dieser Komponenten (Version 12.0.6828.0) ersetzt. Informationen zum geänderten Verhalten der neuen Komponenten finden Sie unter [Verhaltensänderungen der Volltextsuche](../Topic/Behavior%20Changes%20to%20Full-Text%20Search.md). In diesem Thema wird beschrieben, wie von der neuen Version dieser Komponenten zur früheren Version gewechselt bzw. von der früheren Version zu der neuen Version zurückgewechselt wird. Bei Clusterinstallationen sollten diese Änderungen auf allen primären und passiven Knoten vorgenommen werden.  
  
 In früheren Versionen von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] wurden andere Wörtertrennungen verwendet, die durch andere CLSIDs für Englisch (USA) (LCID 1033) und Englisch (Großbritannien) (LCID 2057) dargestellt wurden. In dieser Version verwenden beide LCIDs die gleichen Komponenten mit den gleichen CLSIDs, wie in der folgenden Tabelle dargestellt:  
  
|LCID|Von früheren Versionen installierte Wörtertrennung<br /><br /> Version 12.0.6828.0|Von früheren Versionen installierte Wortstammerkennung|Von dieser Version installierte Wörtertrennung<br /><br /> Version 14.0.4999.1038|Von dieser Version installierte Wortstammerkennung|  
|----------|-------------------------------------------------------------------------|--------------------------------------------|-----------------------------------------------------------------------|---------------------------------------|  
|1033<br />(Englisch (USA))|188D6CC5-CB03-4C01-912E-47D21295D77E|EEED4C20-7F1B-11CE-BE57-00AA0051FE20|9faed859-0b30-4434-ae65-412e14a16fb8|e1e5ef84-c4a6-4e50-8188-99aef3de2659|  
|2057<br />(Englisch (Großbritannien))|173C97E2-AEBE-437C-9445-01B237ABF2F6|D99F7670-7F1A-11CE-BE57-00AA0051FE20|9faed859-0b30-4434-ae65-412e14a16fb8|e1e5ef84-c4a6-4e50-8188-99aef3de2659|  
  
 Bei den in diesem Thema beschriebenen Komponenten handelt es sich um DLL-Dateien, die im `MSSQL\Binn` -Ordner für die [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Instanz installiert sind. Der vollständige Pfad ist in der Regel `C:\Program Files\Microsoft SQL Server\<instance>\MSSQL\Binn`.  
  
 Weitere Informationen zur Wörtertrennung und Wortstammerkennung finden Sie unter [Konfigurieren und Verwalten von Wörtertrennungen und Wortstammerkennungen für die Suche](../../relational-databases/search/configure-and-manage-word-breakers-and-stemmers-for-search.md).  
  
## Wechseln von der aktuellen englischen Wörtertrennung zu den vorherigen englischen Wörtertrennungen  
  
#### So wechseln Sie von der aktuellen Version der Wörtertrennung für Englisch (USA) zur früheren Version  
  
1.  Navigieren Sie in der Registrierung zu folgendem Knoten: **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Microsoft SQL Server\\<Instanzstamm\>\MSSearch\CLSID**.  
  
2.  Fügen Sie mithilfe der folgenden Schritte für die COM ClassIDs für die Schnittstellen der früheren Wörtertrennung für Englisch (USA) und die Wortstammerkennung für LCID 1033 neue Schlüssel hinzu:  
  
    1.  Fügen Sie einen neuen Schlüssel mit dem Wert **{188D6CC5-CB03-4C01-912E-47D21295D77E}** für die frühere Wörtertrennung hinzu.  
  
    2.  Aktualisieren Sie die (standardmäßigen) Daten dieses Schlüsselwerts zu **langwrbk.dll**.  
  
    3.  Fügen Sie einen neuen Schlüssel mit dem Wert **{EEED4C20-7F1B-11CE-BE57-00AA0051FE20}** für die frühere Wortstammerkennung hinzu.  
  
    4.  Aktualisieren Sie die (standardmäßigen) Daten dieses Schlüsselwerts zu **infosoft.dll**.  
  
3.  Navigieren Sie in der Registrierung zu folgendem Knoten: **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Microsoft SQL Server\\<Instanzstamm\>\MSSearch\Language\enu**.  
  
4.  Aktualisieren Sie den **WBreakerClass**-Schlüsselwert zu **{188D6CC5-CB03-4C01-912E-47D21295D77E}**.  
  
5.  Aktualisieren Sie den **StemmerClass**-Schlüsselwert zu **{EEED4C20-7F1B-11CE-BE57-00AA0051FE20}**.  
  
6.  Starten Sie [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] neu.  
  
#### So wechseln Sie von der aktuellen Version der Wörtertrennung für Englisch (Großbritannien) zur früheren Version  
  
1.  Navigieren Sie in der Registrierung zu folgendem Knoten: **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Microsoft SQL Server\\<Instanzstamm\>\MSSearch\CLSID**.  
  
2.  Fügen Sie mithilfe der folgenden Schritte für die COM ClassIDs für die früheren Schnittstellen der Wörtertrennung für Englisch (Großbritannien) und Wortstammerkennung für LCID 2057 einen neuen Schlüssel hinzu:  
  
    1.  Fügen Sie einen neuen Schlüssel mit dem Wert **{173C97E2-AEBE-437C-9445-01B237ABF2F6}** für die frühere Wörtertrennung hinzu.  
  
    2.  Aktualisieren Sie die (standardmäßigen) Daten dieses Schlüsselwerts zu **langwrbk.dll**.  
  
    3.  Fügen Sie einen neuen Schlüssel mit dem Wert **{D99F7670-7F1A-11CE-BE57-00AA0051FE20}** für die frühere Wortstammerkennung hinzu.  
  
    4.  Aktualisieren Sie die (standardmäßigen) Daten dieses Schlüsselwerts zu **infosoft.dll**.  
  
3.  Navigieren Sie in der Registrierung zu folgendem Knoten: **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Microsoft SQL Server\\<Instanzstamm\>\MSSearch\Language\eng**.  
  
4.  Aktualisieren Sie den **WBreakerClass**-Schlüsselwert zu **{173C97E2-AEBE-437C-9445-01B237ABF2F6}**.  
  
5.  Aktualisieren Sie den **StemmerClass**-Schlüsselwert zu **{D99F7670-7F1A-11CE-BE57-00AA0051FE20}**.  
  
6.  Starten Sie [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] neu.  
  
## Zurückwechseln von der aktuellen englischen Wörtertrennung zu der früheren englischen Wörtertrennung  
  
#### So wechseln Sie von der früheren Version der Wörtertrennung für Englisch (USA) zu der aktuellen Version zurück  
  
1.  Navigieren Sie in der Registrierung zu folgendem Knoten: **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Microsoft SQL Server\\<Instanzstamm\>\MSSearch\CLSID**.  
  
2.  Wenn die folgenden Schlüssel nicht vorhanden sind, gehen Sie folgendermaßen vor, um einen neuen Schlüssel für die COM ClassIDs für die Schnittstellen der aktuellen Wörtertrennung für Englisch (USA) und die Wortstammerkennung für LCID 1033 hinzuzufügen:  
  
    1.  Fügen Sie einen neuen Schlüssel mit dem Wert **{9faed859-0b30-4434-ae65-412e14a16fb8}** für die aktuelle Wörtertrennung hinzu.  
  
    2.  Aktualisieren Sie die (standardmäßigen) Daten dieses Schlüsselwerts in **MsWb7.dll**.  
  
    3.  Fügen Sie einen neuen Schlüssel mit dem Wert **{e1e5ef84-c4a6-4e50-8188-99aef3de2659}** für die aktuelle Wortstammerkennung hinzu.  
  
    4.  Aktualisieren Sie die (standardmäßigen) Daten dieses Schlüsselwerts in **MsWb7.dll**.  
  
3.  Navigieren Sie in der Registrierung zu folgendem Knoten: **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Microsoft SQL Server\\<Instanzstamm\>\MSSearch\Language\eng**.  
  
4.  Aktualisieren Sie den **WBreakerClass**-Schlüsselwert in **{9faed859-0b30-4434-ae65-412e14a16fb8}**.  
  
5.  Aktualisieren Sie den **StemmerClass**-Schlüsselwert in **{e1e5ef84-c4a6-4e50-8188-99aef3de2659}**.  
  
6.  Starten Sie [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] neu.  
  
#### So wechseln Sie von der früheren Version der Wörtertrennung für Englisch (Großbritannien) zu der aktuellen Version zurück  
  
1.  Navigieren Sie in der Registrierung zu folgendem Knoten: **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Microsoft SQL Server\\<Instanzstamm\>\MSSearch\CLSID**.  
  
2.  Wenn die folgenden Schlüssel nicht vorhanden sind, gehen Sie folgendermaßen vor, um einen neuen Schlüssel für die COM ClassIDs für die Schnittstellen der aktuellen Wörtertrennung für Englisch (Großbritannien) und die Wortstammerkennung für LCID 2057 hinzuzufügen:  
  
    1.  Fügen Sie einen neuen Schlüssel mit dem Wert **{9faed859-0b30-4434-ae65-412e14a16fb8}** für die aktuelle Wörtertrennung hinzu.  
  
    2.  Aktualisieren Sie die (standardmäßigen) Daten dieses Schlüsselwerts in **MsWb7.dll**.  
  
    3.  Fügen Sie einen neuen Schlüssel mit dem Wert **{e1e5ef84-c4a6-4e50-8188-99aef3de2659}** für die aktuelle Wortstammerkennung hinzu.  
  
    4.  Aktualisieren Sie die (standardmäßigen) Daten dieses Schlüsselwerts in **MsWb7.dll**.  
  
3.  Navigieren Sie in der Registrierung zu folgendem Knoten: **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Microsoft SQL Server\\<Instanzstamm\>\MSSearch\Language\eng**.  
  
4.  Aktualisieren Sie den **WBreakerClass**-Schlüsselwert in **{9faed859-0b30-4434-ae65-412e14a16fb8}**.  
  
5.  Aktualisieren Sie den **StemmerClass**-Schlüsselwert in **{e1e5ef84-c4a6-4e50-8188-99aef3de2659}**.  
  
6.  Starten Sie [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] neu.  
  
## Siehe auch  
 [Wiederherstellen der von der Suche verwendeten Wörtertrennungen auf die vorherige Version](../../relational-databases/search/revert-the-word-breakers-used-by-search-to-the-previous-version.md)   
 [Verhaltensänderungen der Volltextsuche](../Topic/Behavior%20Changes%20to%20Full-Text%20Search.md)  
  
  