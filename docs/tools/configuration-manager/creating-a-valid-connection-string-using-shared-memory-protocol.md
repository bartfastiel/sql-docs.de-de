---
title: "Erstellen einer g&#252;ltigen Verbindungszeichenfolge mithilfe des Shared Memory-Protokolls | Microsoft Docs"
ms.custom: ""
ms.date: "03/14/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "database-engine"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Verbindungszeichenfolgen [Datenbankmodul], freigegebener Speicher"
  - "Aliase [SQL Server], freigegebener Speicher"
ms.assetid: 5fff42e8-377f-4b40-b0c8-b02393f8a1af
caps.latest.revision: 25
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 25
---
# Erstellen einer g&#252;ltigen Verbindungszeichenfolge mithilfe des Shared Memory-Protokolls
  Verbindungen mit [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] von einem Client auf dem gleichen Computer verwenden das Shared Memory-Protokoll. Shared Memory verfügt über keine konfigurierbaren Eigenschaften. Es wird immer zuerst versucht, Shared Memory zu verwenden; es ist nicht möglich, dieses Protokoll von der obersten Position der Liste **Aktivierte Protokolle** in der Liste **Eigenschaften der Clientprotokolle** zu verschieben. Das Shared Memory-Protokoll kann deaktiviert werden, was insbesondere bei der Problembehandlung eines der anderen Protokolle nützlich ist.  
  
 Sie können keinen Alias mithilfe des Shared Memory-Protokolls erstellen. Allerdings wird bei aktiviertem Shared Memory über den namentlichen Verbindungsaufbau zu [!INCLUDE[ssDE](../../includes/ssde-md.md)] eine Shared Memory-Verbindung hergestellt. Für Shared Memory-Verbindungszeichenfolgen wird das Format `lpc:<servername>[\instancename]`verwendet.  
  
## Herstellen einer Verbindung mit dem lokalen Server  
 Beim Herstellen einer Verbindung mit [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], das auf dem gleichen Computer wie der Client ausgeführt wird, können Sie **(local)** als Servernamen verwenden. Aus Gründen der Mehrdeutigkeit wird dies nicht empfohlen, kann aber nützlich sein, wenn vom Client bekannt ist, dass er auf dem vorgesehenen Computer ausgeführt wird. Beim Erstellen einer Anwendung für mobile Benutzer mit getrennter Verbindung (beispielsweise für Verkaufspersonal, wobei [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] auf Laptops ausgeführt und zum Speichern von Projektdaten verwendet wird) würde beispielsweise die Verbindung eines Clients zu **(local)** immer zu dem auf dem Laptop ausgeführten [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] hergestellt. Anstelle von **(local)** kann das Wort **localhost** oder ein Punkt (**.**) verwendet werden.  
  
## Überprüfen Ihres Verbindungsprotokolls  
 Von der folgenden Abfrage wird das Protokoll zurückgegeben, das für die aktuelle Verbindung verwendet wird.  
  
```  
SELECT net_transport   
FROM sys.dm_exec_connections   
WHERE session_id = @@SPID;  
  
```  
  
## Beispiele:  
 Die folgenden Namen werden mit dem lokalen Computer mithilfe des Shared Memory-Protokolls verbunden, falls dieses aktiviert ist:  
  
 `<servername>`  
  
 `<servername>\<instancename>`  
  
 `(local)`  
  
 `localhost`  
  
 Sie können keinen Alias für eine Shared Memory-Verbindung erstellen.  
  
> [!NOTE]  
>  Die Angabe einer IP-Adresse im Feld **Server** führt zu einer TCP/IP-Verbindung.  
  
## Siehe auch  
 [Erstellen einer gültigen Verbindungszeichenfolge mithilfe von TCP/IP](../../tools/configuration-manager/creating-a-valid-connection-string-using-tcp-ip.md)   
 [Erstellen einer gültigen Verbindungszeichenfolge mithilfe von Named Pipes](../Topic/Creating%20a%20Valid%20Connection%20String%20Using%20Named%20Pipes.md)   
 [Auswählen eines Netzwerkprotokolls](../Topic/Choosing%20a%20Network%20Protocol.md)  
  
  