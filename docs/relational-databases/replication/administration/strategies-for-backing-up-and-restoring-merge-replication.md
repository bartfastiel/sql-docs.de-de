---
title: "Strategien zum Sichern und Wiederherstellen einer Mergereplikation | Microsoft Docs"
ms.custom: ""
ms.date: "03/14/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "replication"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Wiederherstellung [SQL Server-Replikation], Mergereplikation"
  - "Sicherung [SQL Server-Replikation], Mergereplikation"
  - "Wiederherstellung [SQL Server-Replikation], Mergereplikation"
  - "Mergereplikation [SQL Server-Replikation], sichern und wiederherstellen"
ms.assetid: b8ae31c6-d76f-4dd7-8f46-17d023ca3eca
caps.latest.revision: 48
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 48
---
# Strategien zum Sichern und Wiederherstellen einer Mergereplikation
  Sichern Sie bei Mergereplikationen regelmäßig die folgenden Datenbanken:  
  
-   Veröffentlichungsdatenbank auf dem Verleger  
  
-   Verteilungsdatenbank auf dem Verteiler  
  
-   Abonnementdatenbank auf den einzelnen Abonnenten  
  
-   Die Systemdatenbanken **master** und **msdb** auf dem Verleger, Verteiler und allen Abonnenten. Diese Datenbanken sollten zur selben Zeit wie alle anderen Datenbanken und die entsprechende Replikationsdatenbank gesichert werden. Sichern Sie also z. B. die **master** - und **msdb** -Datenbanken auf dem Verleger immer dann, wenn Sie auch die Veröffentlichungsdatenbank sichern. Beim Wiederherstellen der Veröffentlichungsdatenbank müssen Sie sicherstellen, dass die **master** - und **msdb** -Datenbanken hinsichtlich der Replikationskonfiguration und der Replikationseinstellungen mit der Veröffentlichungsdatenbank übereinstimmen.  
  
 Wenn Sie regelmäßige Protokollsicherungen ausführen, sollten in den Protokollsicherungen auch alle replikationsrelevanten Änderungen erfasst werden. Wenn Sie keine Protokollsicherungen ausführen, sollte immer dann eine Sicherung erfolgen, wenn eine replikationsrelevante Änderung vorgenommen wurde. Weitere Informationen finden Sie unter [Common Actions Requiring an Updated Backup](../../../relational-databases/replication/administration/common-actions-requiring-an-updated-backup.md).  
  
 Entscheiden Sie sich zum Sichern und Wiederherstellen der Veröffentlichungsdatenbank für eine der unten genannten Herangehensweisen, und befolgen Sie dann die entsprechenden Empfehlungen für die Verteilungsdatenbank und die Abonnementdatenbanken.  
  
## Sichern und Wiederherstellen der Veröffentlichungsdatenbank  
 Für die Wiederherstellung einer Mergeveröffentlichungs-Datenbank gibt es zwei Herangehensweisen. Nach dem Wiederherstellen der Veröffentlichungsdatenbank aus einer Sicherung müssen Sie sich für eine der folgenden beiden Varianten entscheiden:  
  
-   Synchronisieren der Veröffentlichungsdatenbank mit einer Abonnementdatenbank  
  
-   Erneutes Initialisieren aller Abonnements der Veröffentlichungen in der Veröffentlichungsdatenbank  
  
 Durch die Verwendung dieser Methoden wird sichergestellt, dass nach einer Wiederherstellung der Verleger und alle Abonnenten synchronisiert werden.  
  
> [!NOTE]  
>  Wenn Tabellen Identitätsspalten enthalten, müssen Sie sicherstellen, dass nach einer Wiederherstellung die richtigen Identitätsbereiche zugewiesen werden. Weitere Informationen finden Sie unter [Replizieren von Identitätsspalten](../../../relational-databases/replication/publish/replicate-identity-columns.md).  
  
### Synchronisieren der Veröffentlichungsdatenbank  
 Durch das Synchronisieren einer Veröffentlichungsdatenbank mit einer Abonnementdatenbank können Sie aus einer oder mehreren Abonnementdatenbank(en) jene Änderungen hochladen, die zuvor in der Veröffentlichungsdatenbank zwar vorgenommen, aber in der wiederhergestellten Sicherung nicht vorhanden sind. Welche Daten dabei hochgeladen werden können, hängt davon ab, wie die Veröffentlichung gefiltert wird:  
  
-   Wird die Veröffentlichung gar nicht gefiltert, sollten Sie die Veröffentlichungsdatenbank durch Synchronisieren mit einem aktuellen Abonnenten auf den neuesten Stand bringen.  
  
-   Wenn die Veröffentlichung gefiltert ist, können Sie möglicherweise die Veröffentlichungsdatenbank nicht auf den aktuellen Stand bringen. Nehmen wir einmal an, es gibt eine Tabelle, die so partitioniert ist, dass jedes Abonnement nur die Kundendaten für eine der folgenden Verkaufsregionen erhält: Nord, Ost, Süd und West. Wenn für jede Datenpartition mindestens ein Abonnent vorhanden ist, würde es reichen, die Veröffentlichungsdatenbank mit einem Abonnenten für jede Partition zu synchronisieren, um sie auf den neuesten Stand zu bringen. Wenn aber beispielsweise die Daten in der Partition West auf keinen Abonnenten repliziert wurden, können diese Daten auf dem Verleger nicht auf den aktuellen Stand gebracht werden.  
  
> [!IMPORTANT]  
>  Wenn eine Veröffentlichungsdatenbank mit einer Abonnementdatenbank synchronisiert wird, kann es passieren, dass veröffentlichte Tabellen nach dem Wiederherstellen aus der Sicherung einen neueren Stand aufweisen als nicht veröffentlichte Tabellen.  
  
 Wenn Sie mit einem Abonnenten synchronisieren, die eine Version von ausgeführt wird [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] vor [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)], das Abonnement nicht anonym sein – es muss ein clientabonnement oder ein Serverabonnement (bezeichnet als lokales Abonnement bzw. globales Abonnement in früheren Versionen).  
  
 Informationen zum Synchronisieren eines Abonnements finden Sie unter [Synchronize a Push Subscription](../../../relational-databases/replication/synchronize-a-push-subscription.md) und [Synchronize a Pull Subscription](../../../relational-databases/replication/synchronize-a-pull-subscription.md).  
  
### Erneutes Initialisieren aller Abonnements  
 Durch das erneute Initialisieren aller Abonnements wird sichergestellt, dass alle Abonnenten konsistent mit der wiederhergestellten Veröffentlichungsdatenbank sind. Diese Herangehensweise sollten Sie verwenden, wenn Sie eine ganze Topologie auf den früheren Status zurücksetzen möchten, der in einer bestimmten Sicherung der Veröffentlichungsdatenbank festgehalten ist. So kann es z. B. erforderlich sein, alle Abonnements neu zu initialisieren, wenn Sie nach einer fehlerhaft ausgeführten Batchoperation einen früheren Zustand Ihrer Veröffentlichungsdatenbank wiederherstellen möchten.  
  
 Generieren Sie bei Wahl dieser Option direkt nach dem Wiederherstellen der Veröffentlichungsdatenbank eine neue Momentaufnahme, die an die erneut initialisierten Abonnenten übertragen wird.  
  
 Informationen zum erneuten Initialisieren eines Abonnement finden Sie unter [Reinitialize a Subscription](../../../relational-databases/replication/reinitialize-a-subscription.md).  
  
 Informationen zum Erstellen und Anwenden einer Momentaufnahme finden Sie unter [Create und Apply the Initial Snapshot](../Topic/Create%20und%20Apply%20the%20Initial%20Snapshot.md) und [Create a Snapshot for a Merge Publication with Parameterized Filters](../../../relational-databases/replication/create-a-snapshot-for-a-merge-publication-with-parameterized-filters.md).  
  
## Sichern und Wiederherstellen der Verteilungsdatenbank  
 Bei einer Mergereplikation sollte die Verteilungsdatenbank in regelmäßigen Abständen gesichert werden. Wenn die Sicherung nicht älter als die kürzeste Beibehaltungsdauer aller Veröffentlichungen ist, die den Verteiler verwenden, kann die Verteilungsdatenbank jederzeit problemlos wiederhergestellt werden. Wenn es z. B. drei Veröffentlichungen mit Beibehaltungsdauerwerten von 10, 20 und 30 Tagen gibt, sollte die zum Wiederherstellen der Datenbank verwendete Sicherung höchstens 10 Tage alt sein. Die Verteilungsdatenbank spielt in einer Mergereplikation nur eine begrenzte Rolle: Sie speichert keine Daten, die bei der Änderungsnachverfolgung verwendet werden, und sie bietet auch keine temporäre Speicherung von Mergereplikationsänderungen, die an Abonnementdatenbanken weitergeleitet werden (wie dies bei Transaktionsreplikationen der Fall ist).  
  
## Sichern und Wiederherstellen einer Abonnementdatenbank  
 Um die erfolgreiche Wiederherstellung einer Abonnementdatenbank sicherzustellen, sollten die Abonnenten eine Synchronisierung mit dem Verleger vornehmen, bevor die Abonnementdatenbank gesichert wird. Auch nach dem Wiederherstellen der Abonnementdatenbank sollte eine Synchronisierung vorgenommen werden:  
  
-   Durch das Synchronisieren mit dem Verleger vor dem Sichern der Abonnementdatenbank wird sichergestellt, dass sich das Abonnement noch in der Beibehaltungsdauer der Veröffentlichung befindet, wenn der Abonnent wiederhergestellt wird. Nehmen wir beispielsweise an, dass eine Veröffentlichung mit einer Beibehaltungsdauer von 10 Tagen vorliegt. Die letzte Synchronisierung liegt 8 Tage zurück, und jetzt wird die Sicherung ausgeführt. Wenn die Sicherung 4 Tage später wiederhergestellt wird, ist die letzte Synchronisierung 12 Tage her. Dies überschreitet die Beibehaltungsdauer. In diesem Fall müssten Sie den Abonnenten erneut initialisieren. Wenn vor der Sicherung eine Synchronisierung mit dem Abonnenten stattgefunden hätte, würde sich die Abonnementdatenbank noch in der Beibehaltungsdauer befinden.  
  
     Das Alter der Sicherung darf die kürzeste Beibehaltungsdauer aller vom Abonnenten abonnierten Veröffentlichungen nicht überschreiten. Wenn ein Abonnent beispielsweise drei Veröffentlichungen abonniert, deren Beibehaltungsdauerwerte 10, 20 und 30 Tage betragen, sollte die zum Wiederherstellen der Datenbank verwendete Sicherung höchstens 10 Tage alt sein.  
  
-   Durch Synchronisieren der Abonnementdatenbank mit allen ihren Veröffentlichungen nach einer erfolgten Wiederherstellung wird sichergestellt, dass der Abonnent alle Änderungen auf dem Verleger übernehmen kann.  
  
 Zum Festlegen der Beibehaltungsdauer der Veröffentlichung finden Sie unter [Festlegen des Ablaufdatums für Abonnements](../../../relational-databases/replication/publish/set-the-expiration-period-for-subscriptions.md).  
  
 Informationen zum Synchronisieren eines Abonnements finden Sie unter [Synchronize a Push Subscription](../../../relational-databases/replication/synchronize-a-push-subscription.md) und [Synchronize a Pull Subscription](../../../relational-databases/replication/synchronize-a-pull-subscription.md).  
  
## Sichern und Wiederherstellen einer Wiederveröffentlichungs-Datenbank  
 Wenn eine Datenbank Daten von einem Verleger abonniert und dieselben Daten selbst auf anderen Abonnementdatenbanken veröffentlicht, wird sie als Wiederveröffentlichungs-Datenbank bezeichnet. Befolgen Sie beim Wiederherstellen einer Wiederveröffentlichungs-Datenbank die in diesem Thema in den Abschnitten zum Sichern und Wiederherstellen einer Veröffentlichungsdatenbank sowie zum Sichern und Wiederherstellen einer Abonnementdatenbank beschriebenen Richtlinien.  
  
## Siehe auch  
 [Sichern und Wiederherstellen von SQL Server-Datenbanken](../../../relational-databases/backup-restore/back-up-and-restore-of-sql-server-databases.md)   
 [Sichern und Wiederherstellen von replizierten Datenbanken](../../../relational-databases/replication/administration/back-up-and-restore-replicated-databases.md)  
  
  