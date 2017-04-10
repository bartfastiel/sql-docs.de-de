---
title: "Erneutes Initialisieren eines Abonnements | Microsoft Docs"
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
  - "Initialisieren von Abonnements [SQL Server-Replikation], erneutes Initialisieren"
  - "Abonnements [SQL Server-Replikation], erneutes Initialisieren"
  - "Erneutes Initialisieren von Abonnements"
ms.assetid: ca3625c5-c62e-4ab7-9829-d511f838e385
caps.latest.revision: 37
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 37
---
# Erneutes Initialisieren eines Abonnements
  In diesem Thema wird beschrieben, wie ein Abonnement in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] mit [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], [!INCLUDE[tsql](../../includes/tsql-md.md)] oder Replikationsverwaltungsobjekten (RMO) neu initialisiert wird. Einzelne Abonnements können für die erneute Initialisierung markiert werden, sodass während der nächsten Synchronisierung eine neue Momentaufnahme angewendet wird.  
  
 **In diesem Thema**  
  
-   **So initialisieren Sie ein Abonnement erneut mit:**  
  
     [SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
     [Replikationsverwaltungsobjekte (RMO)](#RMOProcedure)  
  
##  <a name="SSMSProcedure"></a> Verwendung von SQL Server Management Studio  
 Das erneute Initialisieren eines Abonnements ist ein zweistufiger Prozess:  
  
1.  Zunächst müssen die Abonnements für eine Veröffentlichung, die erneut initialisiert werden sollen, *gekennzeichnet* werden. Kennzeichnen der Abonnements für die erneute Initialisierung in der **Abonnements erneut initialisieren** Dialogfeld, das zur Verfügung steht die **lokale Publikationen** Ordner und die **Lokale Abonnements** im Ordner [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]. Abonnements können darüber hinaus auch auf der Registerkarte **Alle Abonnements** und über den Veröffentlichungsknoten im Replikationsmonitor als erneut zu initialisieren gekennzeichnet werden. Informationen zum Starten des Replikationsmonitors finden Sie unter [Starten des Replikationsmonitors](../../relational-databases/replication/monitor/start-the-replication-monitor.md). Beim Kennzeichnen eines Abonnements für die erneute Initialisierung können Sie zwischen den folgenden Optionen auswählen:  
  
     **Aktuelle Momentaufnahme verwenden**  
     Wählen Sie diese Option aus, wenn die aktuelle Momentaufnahme beim nächsten Ausführen des Verteilungs- oder Merge-Agents auf den Abonnenten angewendet werden soll. Wenn keine gültige Momentaufnahme verfügbar ist, kann diese Option nicht ausgewählt werden.  
  
     **Neue Momentaufnahme verwenden**  
     Wählen Sie diese Option aus, wenn das Abonnement mithilfe einer neuen Momentaufnahme erneut initialisiert werden soll. Die Momentaufnahme kann erst auf den Abonnenten angewendet werden, nachdem sie vom Momentaufnahme-Agent generiert wurde. Wenn die Ausführung des Momentaufnahme-Agents auf einem Zeitplan basiert, wird das Abonnement erst nach der nächsten zeitplangesteuerten Ausführung des Momentaufnahme-Agents initialisiert. Wählen Sie die Option **Neue Momentaufnahme jetzt generieren** , um den Momentaufnahme-Agent sofort zu starten.  
  
     **Unsynchronisierte Änderungen am Abonnenten vor der erneuten Initialisierung hochladen**  
     Nur für Mergereplikationen zulässig. Wählen Sie diese Option aus, um alle ausstehenden Änderungen aus der Abonnementdatenbank herunterzuladen, bevor die Daten des Abonnenten durch eine Momentaufnahme überschrieben werden.  
  
     Wenn Sie einen parametrisierten Filter hinzufügen, löschen oder ändern, können ausstehende Änderungen auf dem Abonnenten während der erneuten Initialisierung nicht auf den Verleger hochgeladen werden. Wenn Sie ausstehende Änderungen hochladen möchten, sollten Sie vor dem Ändern des Filters alle Abonnements synchronisieren.  
  
2.  Ein Abonnement wird erneut initialisiert, sobald es wieder synchronisiert wird: Der Verteilungs-Agent (bei einer Transaktionsreplikation) bzw. der Merge-Agent (bei einer Mergereplikation) wendet auf alle Abonnenten mit einem Abonnement, das für eine erneute Initialisierung gekennzeichnet ist, die jeweils neueste Momentaufnahme an. Weitere Informationen zum Synchronisieren von Abonnements finden Sie unter [Synchronisieren eines Abonnements Push](../../relational-databases/replication/synchronize-a-push-subscription.md) und [synchronisieren Sie ein Pullabonnement](../../relational-databases/replication/synchronize-a-pull-subscription.md).  
  
#### So kennzeichnen Sie ein einzelnes Push- oder Pullabonnement für die erneute Initialisierung in SQL Server Management Studio (auf dem Verleger)  
  
1.  Stellen Sie in [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)]eine Verbindung mit dem Verleger her, und erweitern Sie dann den Serverknoten.  
  
2.  Erweitern Sie den Ordner **Replikation** , und erweitern Sie dann den Ordner **Lokale Veröffentlichungen** .  
  
3.  Erweitern Sie die Veröffentlichung mit dem Abonnement, das erneut initialisiert werden soll.  
  
4.  Maustaste auf das Abonnement, und klicken Sie dann auf **erneut initialisieren**.  
  
5.  In der **Abonnements erneut initialisieren** Klicken Sie im Dialogfeld Wählen Sie Optionen aus, und klicken Sie dann auf **für die erneute Initialisierung kennzeichnen**.  
  
#### So kennzeichnen Sie ein einzelnes Pullabonnement für die erneute Initialisierung in SQL Server Management Studio (auf dem Abonnenten)  
  
1.  Stellen Sie in [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)]eine Verbindung mit dem Abonnenten her, und erweitern Sie dann den Serverknoten.  
  
2.  Erweitern Sie den Ordner **Replikation** , und erweitern Sie dann den Ordner **Lokale Abonnements** .  
  
3.  Maustaste auf das Abonnement, und klicken Sie dann auf **erneut initialisieren**.  
  
4.  Klicken Sie im angezeigten Bestätigungsdialogfeld auf **Ja**.  
  
#### So kennzeichnen Sie alle Abonnements für die erneute Initialisierung in SQL Server Management Studio  
  
1.  Stellen Sie in [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)]eine Verbindung mit dem Verleger her, und erweitern Sie dann den Serverknoten.  
  
2.  Erweitern Sie den Ordner **Replikation** , und erweitern Sie dann den Ordner **Lokale Veröffentlichungen** .  
  
3.  Mit der rechten Maustaste in der Veröffentlichung mit Abonnements, die Sie verwenden möchten, erneut initialisiert, und klicken Sie dann auf **alle Abonnements erneut initialisieren**.  
  
4.  In der **Abonnements erneut initialisieren** Klicken Sie im Dialogfeld Wählen Sie Optionen aus, und klicken Sie dann auf **für die erneute Initialisierung kennzeichnen**.  
  
#### So kennzeichnen Sie ein einzelnes Push- oder Pullabonnement für die erneute Initialisierung im Replikationsmonitor  
  
1.  Erweitern Sie im Replikationsmonitor im linken Bereich eine Verlegergruppe, erweitern Sie einen Verleger, und klicken Sie dann auf eine Veröffentlichung.  
  
2.  Klicken Sie auf die Registerkarte **Alle Abonnements** .  
  
3.  Mit der rechten Maustaste des Abonnements erneut zu initialisieren, und klicken Sie auf soll **Abonnement erneut initialisieren**.  
  
4.  In der **Abonnements erneut initialisieren** Klicken Sie im Dialogfeld Wählen Sie Optionen aus, und klicken Sie dann auf **für die erneute Initialisierung kennzeichnen**.  
  
#### So kennzeichnen Sie alle Abonnements für die erneute Initialisierung im Replikationsmonitor  
  
1.  Erweitern Sie im Replikationsmonitor im linken Bereich eine Verlegergruppe, und erweitern Sie dann einen Verleger.  
  
2.  Mit der rechten Maustaste in der Veröffentlichung mit Abonnements, die Sie verwenden möchten, erneut initialisiert, und klicken Sie dann auf **alle Abonnements erneut initialisieren**.  
  
3.  In der **Abonnements erneut initialisieren** Klicken Sie im Dialogfeld Wählen Sie Optionen aus, und klicken Sie dann auf **für die erneute Initialisierung kennzeichnen**.  
  
##  <a name="TsqlProcedure"></a> Verwenden von Transact-SQL  
 Abonnements können mithilfe von gespeicherten Replikationsprozeduren programmgesteuert erneut initialisiert werden. Welche gespeicherte Prozedur verwendet wird, hängt dem Typ des Abonnements (d. h. Push- oder Pullabonnement) und vom Typ der Veröffentlichung ab, zu der das Abonnement gehört.  
  
#### So initialisieren Sie ein Pullabonnement für eine Transaktionsveröffentlichung erneut  
  
1.  Führen Sie auf dem Abonnenten für die Abonnementdatenbank [Sp_reinitpullsubscription & #40; Transact-SQL & #41;](../../relational-databases/system-stored-procedures/sp-reinitpullsubscription-transact-sql.md). Geben Sie **@publisher**, **@publisher_db**, und **@publication**. Damit wird das Abonnement für die Neuinitialisierung bei der nächsten Ausführung des Verteilungs-Agents markiert.  
  
2.  (Optional) Starten Sie den Verteilungs-Agent auf dem Abonnenten, um das Abonnement zu synchronisieren. Weitere Informationen finden Sie unter [Synchronize a Pull Subscription](../../relational-databases/replication/synchronize-a-pull-subscription.md).  
  
#### So initialisieren Sie ein Pushabonnement für eine Transaktionsveröffentlichung erneut  
  
1.  Führen Sie auf dem Verleger [Sp_reinitsubscription & #40; Transact-SQL & #41;](../../relational-databases/system-stored-procedures/sp-reinitsubscription-transact-sql.md). Geben Sie **@publication**, **@subscriber**, und **@destination_db**. Damit wird das Abonnement für die Neuinitialisierung bei der nächsten Ausführung des Verteilungs-Agents markiert.  
  
2.  (Optional) Starten Sie den Verteilungs-Agent auf dem Verteiler, um das Abonnement zu synchronisieren. Weitere Informationen finden Sie unter [Synchronize a Push Subscription](../../relational-databases/replication/synchronize-a-push-subscription.md).  
  
#### So initialisieren Sie ein Pullabonnement mit einer Mergeveröffentlichung erneut  
  
1.  Führen Sie auf dem Abonnenten für die Abonnementdatenbank [Sp_reinitmergepullsubscription & #40; Transact-SQL & #41;](../../relational-databases/system-stored-procedures/sp-reinitmergepullsubscription-transact-sql.md). Geben Sie **@publisher**, **@publisher_db**, und **@publication**. Geben Sie den Wert, um die Änderungen vom Abonnenten vor der erneuten Initialisierung hochladen **true** für **@upload_first**. Damit wird das Abonnement für die Neuinitialisierung bei der nächsten Ausführung des Merge-Agents markiert.  
  
    > [!IMPORTANT]  
    >  Wenn Sie einen parametrisierten Filter hinzufügen, löschen oder ändern, können ausstehende Änderungen auf dem Abonnenten während der erneuten Initialisierung nicht auf den Verleger hochgeladen werden. Wenn Sie ausstehende Änderungen hochladen möchten, sollten Sie vor dem Ändern des Filters alle Abonnements synchronisieren.  
  
2.  (Optional) Starten Sie den Merge-Agent auf dem Abonnenten, um das Abonnement zu synchronisieren. Weitere Informationen finden Sie unter [Synchronize a Pull Subscription](../../relational-databases/replication/synchronize-a-pull-subscription.md).  
  
#### So initialisieren Sie ein Pushabonnement mit einer Mergeveröffentlichung erneut  
  
1.  Führen Sie auf dem Verleger [Sp_reinitmergesubscription & #40; Transact-SQL & #41;](../../relational-databases/system-stored-procedures/sp-reinitmergesubscription-transact-sql.md). Geben Sie **@publication**, **@subscriber**, und **@subscriber_db**. Geben Sie den Wert, um die Änderungen vom Abonnenten vor der erneuten Initialisierung hochladen **true** für **@upload_first**. Damit wird das Abonnement für die Neuinitialisierung bei der nächsten Ausführung des Verteilungs-Agents markiert.  
  
    > [!IMPORTANT]  
    >  Wenn Sie einen parametrisierten Filter hinzufügen, löschen oder ändern, können ausstehende Änderungen auf dem Abonnenten während der erneuten Initialisierung nicht auf den Verleger hochgeladen werden. Wenn Sie ausstehende Änderungen hochladen möchten, sollten Sie vor dem Ändern des Filters alle Abonnements synchronisieren.  
  
2.  (Optional) Starten Sie den Merge-Agent auf dem Verteiler, um das Abonnement zu synchronisieren. Weitere Informationen finden Sie unter [Synchronize a Push Subscription](../../relational-databases/replication/synchronize-a-push-subscription.md).  
  
#### So legen Sie die Neuinitialisierungsrichtlinie während der Erstellung einer neuen Mergeveröffentlichung fest  
  
1.  Führen Sie auf dem Verleger für die Veröffentlichungsdatenbank [Sp_addmergepublication](../../relational-databases/system-stored-procedures/sp-addmergepublication-transact-sql.md), angeben, einen der folgenden für Werte **@automatic_reinitialization_policy**:  
  
    -   **1** -Änderungen werden vom Abonnenten hochgeladen, bevor Sie automatisch ein Abonnement reinitialisiert wird je nach Bedarf durch eine Änderung an der Veröffentlichung.  
  
    -   **0** -Änderungen auf dem Abonnenten werden verworfen, wenn automatisch ein Abonnement reinitialisiert wird je nach Bedarf durch eine Änderung an der Veröffentlichung.  
  
    > [!IMPORTANT]  
    >  Wenn Sie einen parametrisierten Filter hinzufügen, löschen oder ändern, können ausstehende Änderungen auf dem Abonnenten während der erneuten Initialisierung nicht auf den Verleger hochgeladen werden. Wenn Sie ausstehende Änderungen hochladen möchten, sollten Sie vor dem Ändern des Filters alle Abonnements synchronisieren.  
  
     Weitere Informationen finden Sie unter [Create a Publication](../../relational-databases/replication/publish/create-a-publication.md).  
  
#### So ändern Sie die Neuinitialisierungsrichtlinie für eine vorhandene Mergeveröffentlichung  
  
1.  Führen Sie auf dem Verleger für die Veröffentlichungsdatenbank [Sp_changemergepublication](../../relational-databases/system-stored-procedures/sp-changemergepublication-transact-sql.md), wobei **Automatic_reinitialization_policy** für **@property** und einen der folgenden Werte für **@value**:  
  
    -   **1** -Änderungen werden vom Abonnenten hochgeladen, bevor Sie automatisch ein Abonnement reinitialisiert wird je nach Bedarf durch eine Änderung an der Veröffentlichung.  
  
    -   **0** -Änderungen auf dem Abonnenten werden verworfen, wenn automatisch ein Abonnement reinitialisiert wird je nach Bedarf durch eine Änderung an der Veröffentlichung.  
  
    > [!IMPORTANT]  
    >  Wenn Sie einen parametrisierten Filter hinzufügen, löschen oder ändern, können ausstehende Änderungen auf dem Abonnenten während der erneuten Initialisierung nicht auf den Verleger hochgeladen werden. Wenn Sie ausstehende Änderungen hochladen möchten, sollten Sie vor dem Ändern des Filters alle Abonnements synchronisieren.  
  
     Weitere Informationen finden Sie unter [View and Modify Publication Properties](../../relational-databases/replication/publish/view-and-modify-publication-properties.md).  
  
##  <a name="RMOProcedure"></a> Verwenden von Replikationsverwaltungsobjekten (RMO)  
 Einzelne Abonnements können für die erneute Initialisierung markiert werden, sodass während der nächsten Synchronisierung eine neue Momentaufnahme angewendet wird. Abonnements können mithilfe von Replikationsverwaltungsobjekten (RMO) programmgesteuert erneut initialisiert werden. Die zu verwendenden Klassen hängen Typ der Veröffentlichung, zu der das Abonnement gehört, und dem Typ des Abonnements ab (d. h. Push- oder Pullabonnement).  
  
#### So initialisieren Sie ein Pullabonnement für eine Transaktionsveröffentlichung erneut  
  
1.  Erstellen Sie eine Verbindung mit dem Abonnenten mithilfe der <xref:Microsoft.SqlServer.Management.Common.ServerConnection> Klasse.  
  
2.  Erstellen Sie eine Instanz der <xref:Microsoft.SqlServer.Replication.TransPullSubscription> Klasse, und legen <xref:Microsoft.SqlServer.Replication.PullSubscription.PublicationName%2A>, <xref:Microsoft.SqlServer.Replication.PullSubscription.DatabaseName%2A>, <xref:Microsoft.SqlServer.Replication.PullSubscription.PublisherName%2A>, <xref:Microsoft.SqlServer.Replication.PullSubscription.PublicationDBName%2A>, und die Verbindung aus Schritt 1 für <xref:Microsoft.SqlServer.Replication.ReplicationObject.ConnectionContext%2A>.  
  
3.  Rufen Sie die <xref:Microsoft.SqlServer.Replication.ReplicationObject.LoadProperties%2A> Methode zum Abrufen der Eigenschaften des Objekts.  
  
    > [!NOTE]  
    >  Wenn diese Methode zurückgibt **false**, entweder die Abonnementeigenschaften in Schritt 2 falsch definiert, oder das Pullabonnement ist nicht vorhanden.  
  
4.  Rufen Sie die <xref:Microsoft.SqlServer.Replication.TransPullSubscription.Reinitialize%2A> Methode. Diese Methode markiert das Abonnement für die erneute Initialisierung.  
  
5.  Synchronisieren Sie das Pullabonnement. Weitere Informationen finden Sie unter [Synchronize a Pull Subscription](../../relational-databases/replication/synchronize-a-pull-subscription.md).  
  
#### So initialisieren Sie ein Pushabonnement für eine Transaktionsveröffentlichung erneut  
  
1.  Erstellen Sie eine Verbindung mit dem Verleger mithilfe der <xref:Microsoft.SqlServer.Management.Common.ServerConnection> Klasse.  
  
2.  Erstellen Sie eine Instanz der <xref:Microsoft.SqlServer.Replication.TransSubscription> Klasse, und legen <xref:Microsoft.SqlServer.Replication.Subscription.PublicationName%2A>, <xref:Microsoft.SqlServer.Replication.Subscription.DatabaseName%2A>, <xref:Microsoft.SqlServer.Replication.Subscription.SubscriberName%2A>, <xref:Microsoft.SqlServer.Replication.Subscription.SubscriptionDBName%2A>, und die Verbindung aus Schritt 1 für <xref:Microsoft.SqlServer.Replication.ReplicationObject.ConnectionContext%2A>.  
  
3.  Rufen Sie die <xref:Microsoft.SqlServer.Replication.ReplicationObject.LoadProperties%2A> Methode zum Abrufen der Eigenschaften des Objekts.  
  
    > [!NOTE]  
    >  Wenn diese Methode zurückgibt **false**, entweder die Abonnementeigenschaften in Schritt 2 falsch definiert, oder das Pushabonnement ist nicht vorhanden.  
  
4.  Rufen Sie die <xref:Microsoft.SqlServer.Replication.TransSubscription.Reinitialize%2A> Methode. Diese Methode markiert das Abonnement für die erneute Initialisierung.  
  
5.  Synchronisieren Sie das Pushabonnement. Weitere Informationen finden Sie unter [Synchronize a Push Subscription](../../relational-databases/replication/synchronize-a-push-subscription.md).  
  
#### So initialisieren Sie ein Pullabonnement mit einer Mergeveröffentlichung erneut  
  
1.  Erstellen Sie eine Verbindung mit dem Abonnenten mithilfe der <xref:Microsoft.SqlServer.Management.Common.ServerConnection> Klasse.  
  
2.  Erstellen Sie eine Instanz der <xref:Microsoft.SqlServer.Replication.MergePullSubscription> Klasse, und legen <xref:Microsoft.SqlServer.Replication.PullSubscription.PublicationName%2A>, <xref:Microsoft.SqlServer.Replication.PullSubscription.DatabaseName%2A>, <xref:Microsoft.SqlServer.Replication.PullSubscription.PublisherName%2A>, <xref:Microsoft.SqlServer.Replication.PullSubscription.PublicationDBName%2A>, und die Verbindung aus Schritt 1 für <xref:Microsoft.SqlServer.Replication.ReplicationObject.ConnectionContext%2A>.  
  
3.  Rufen Sie die <xref:Microsoft.SqlServer.Replication.ReplicationObject.LoadProperties%2A> Methode zum Abrufen der Eigenschaften des Objekts.  
  
    > [!NOTE]  
    >  Wenn diese Methode zurückgibt **false**, entweder die Abonnementeigenschaften in Schritt 2 falsch definiert, oder das Pullabonnement ist nicht vorhanden.  
  
4.  Rufen Sie die <xref:Microsoft.SqlServer.Replication.MergePullSubscription.Reinitialize%2A> Methode. Übergeben Sie den Wert **true** , wenn vor der erneuten Initialisierung Änderungen beim Abonnenten hochgeladen werden sollen, oder übergeben Sie den Wert **false** , wenn sofort erneut initialisiert und Änderungen beim Abonnenten nicht gespeichert werden sollen. Diese Methode markiert das Abonnement für die erneute Initialisierung.  
  
    > [!NOTE]  
    >  Änderungen können nicht hochgeladen werden, wenn das Abonnement abgelaufen ist. Weitere Informationen finden Sie unter [Set the Expiration Period for Subscriptions](../../relational-databases/replication/publish/set-the-expiration-period-for-subscriptions.md).  
  
5.  Synchronisieren Sie das Pullabonnement. Weitere Informationen finden Sie unter [Synchronize a Pull Subscription](../../relational-databases/replication/synchronize-a-pull-subscription.md).  
  
#### So initialisieren Sie ein Pushabonnement mit einer Mergeveröffentlichung erneut  
  
1.  Erstellen Sie eine Verbindung mit dem Verleger mithilfe der <xref:Microsoft.SqlServer.Management.Common.ServerConnection> Klasse.  
  
2.  Erstellen Sie eine Instanz der <xref:Microsoft.SqlServer.Replication.MergeSubscription> Klasse, und legen <xref:Microsoft.SqlServer.Replication.Subscription.PublicationName%2A>, <xref:Microsoft.SqlServer.Replication.Subscription.DatabaseName%2A>, <xref:Microsoft.SqlServer.Replication.Subscription.SubscriberName%2A>, <xref:Microsoft.SqlServer.Replication.Subscription.SubscriptionDBName%2A>, und die Verbindung aus Schritt 1 für <xref:Microsoft.SqlServer.Replication.ReplicationObject.ConnectionContext%2A>.  
  
3.  Rufen Sie die <xref:Microsoft.SqlServer.Replication.ReplicationObject.LoadProperties%2A> Methode zum Abrufen der Eigenschaften des Objekts.  
  
    > [!NOTE]  
    >  Wenn diese Methode zurückgibt **false**, entweder die Abonnementeigenschaften in Schritt 2 falsch definiert, oder das Pushabonnement ist nicht vorhanden.  
  
4.  Rufen Sie die <xref:Microsoft.SqlServer.Replication.MergeSubscription.Reinitialize%2A> Methode. Übergeben Sie den Wert **true** , wenn vor der erneuten Initialisierung Änderungen beim Abonnenten hochgeladen werden sollen, oder übergeben Sie den Wert **false** , wenn sofort erneut initialisiert und Änderungen beim Abonnenten nicht gespeichert werden sollen. Diese Methode markiert das Abonnement für die erneute Initialisierung.  
  
    > [!NOTE]  
    >  Änderungen können nicht hochgeladen werden, wenn das Abonnement abgelaufen ist. Weitere Informationen finden Sie unter [Set the Expiration Period for Subscriptions](../../relational-databases/replication/publish/set-the-expiration-period-for-subscriptions.md).  
  
5.  Synchronisieren Sie das Pushabonnement. Weitere Informationen finden Sie unter [Synchronize a Push Subscription](../../relational-databases/replication/synchronize-a-push-subscription.md).  
  
###  <a name="PShellExample"></a> Beispiele (RMO)  
 Im folgenden Beispiel wird ein Pullabonnement für eine Transaktionsveröffentlichung erneut initialisiert.  
  
 [!code-csharp[HowTo#rmo_ReinitTranPullSub](../../relational-databases/replication/codesnippet/csharp/rmohowto/rmotestevelope.cs#rmo_reinittranpullsub)]  
  
 [!code-vb[HowTo#rmo_vb_ReinitTranPullSub](../../relational-databases/replication/codesnippet/visualbasic/rmohowtovb/rmotestenv.vb#rmo_vb_reinittranpullsub)]  
  
 In diesem Beispiel wird ein Pullabonnement für eine Transaktionsveröffentlichung erneut initialisiert, nachdem Änderungen beim Abonnenten hochgeladen wurden.  
  
 [!code-csharp[HowTo#rmo_ReinitMergePullSub_WithUpload](../../relational-databases/replication/codesnippet/csharp/rmohowto/rmotestevelope.cs#rmo_reinitmergepullsub_withupload)]  
  
 [!code-vb[HowTo#rmo_vb_ReinitMergePullSub_WithUpload](../../relational-databases/replication/codesnippet/visualbasic/rmohowtovb/rmotestenv.vb#rmo_vb_reinitmergepullsub_withupload)]  
  
## Siehe auch  
 [Erneutes Initialisieren von Abonnements](../../relational-databases/replication/reinitialize-subscriptions.md)   
 [Konzepte für Replikationsverwaltungsobjekte (RMO)](../../relational-databases/replication/concepts/replication-management-objects-concepts.md)   
 [Bewährte Methoden für die Replikationssicherheit](../../relational-databases/replication/security/replication-security-best-practices.md)  
  
  