---
title: "Anzeigen und &#196;ndern von Ver&#246;ffentlichungseigenschaften | Microsoft Docs"
ms.custom: ""
ms.date: "03/17/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "replication"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Anzeigen von Replikationseigenschaften"
  - "Ändern von Replikationseigenschaften, Artikel"
  - "Artikel [SQL Server-Replikation], ändern"
  - "Veröffentlichungen [SQL Server-Replikation], Eigenschaften"
  - "Artikel [SQL Server-Replikation], Eigenschaften"
  - "Ändern von Replikationseigenschaften, Veröffentlichungen"
  - "Veröffentlichungen [SQL Server-Replikation], ändern"
ms.assetid: 27d72ea4-bcb6-48f2-b4aa-eb1410da7efc
caps.latest.revision: 44
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 44
---
# Anzeigen und &#196;ndern von Ver&#246;ffentlichungseigenschaften
  In diesem Thema wird beschrieben, wie die Veröffentlichungseigenschaften in [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] mit [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)], [!INCLUDE[tsql](../../../includes/tsql-md.md)] oder Replikationsverwaltungsobjekten (RMO) angezeigt und geändert werden.  
  
 **In diesem Thema**  
  
-   **Vorbereitungen:**  
  
     [Einschränkungen](#Restrictions)  
  
     [Empfehlungen](#Recommendations)  
  
-   **So zeigen Sie Veröffentlichungseigenschaften an und ändern sie mit:**  
  
     [SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
     [Replikationsverwaltungsobjekte (RMO)](#RMOProcedure)  
  
##  <a name="BeforeYouBegin"></a> Vorbereitungen  
  
###  <a name="Restrictions"></a> Einschränkungen  
  
-   Einige Eigenschaften können nicht geändert werden, nachdem eine Veröffentlichung erstellt wurde. Andere Eigenschaften können nicht geändert werden, wenn Abonnements für die Veröffentlichung vorhanden sind. Eigenschaften, die nicht geändert werden können, werden als schreibgeschützt angezeigt.  
  
###  <a name="Recommendations"></a> Empfehlungen  
  
-   Nachdem eine Veröffentlichung erstellt wurde, ist für bestimmte Eigenschaftsänderungen eine neue Momentaufnahme erforderlich. Wenn für eine Veröffentlichung Abonnements erstellt wurden, müssen bei bestimmten Änderungen alle Abonnements erneut initialisiert werden. Weitere Informationen finden Sie unter [Ändern von Veröffentlichungs- und Artikeleigenschaften](../../../relational-databases/replication/publish/change-publication-and-article-properties.md) und [Hinzufügen und löschen Artikeln aus vorhandenen Veröffentlichungen](../../../relational-databases/replication/publish/add-articles-to-and-drop-articles-from-existing-publications.md).  
  
##  <a name="SSMSProcedure"></a> Verwendung von SQL Server Management Studio  
 Anzeigen und Ändern von Eigenschaften in der **Veröffentlichungseigenschaften - \< Veröffentlichung>** verfügbar im Dialogfeld [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] und Replikationsmonitor. Informationen zum Starten des Replikationsmonitors finden Sie unter [Starten des Replikationsmonitors](../../../relational-databases/replication/monitor/start-the-replication-monitor.md).  
  
 Die **Veröffentlichungseigenschaften - \< Veröffentlichung>** Dialogfeld umfasst die folgenden Seiten:  
  
-   Die Seite **Allgemein** enthält den Namen und die Beschreibung der Veröffentlichung, den Datenbanknamen, den Typ der Veröffentlichung und die Einstellungen für den Abonnementablauf.  
  
-   Die Seite **Artikel** entspricht der Seite **Artikel** des Assistenten für neue Veröffentlichung. Verwenden Sie diese Seite, um Artikel hinzuzufügen und zu löschen und um Eigenschaften sowie die Spaltenfilterung für Artikel zu ändern.  
  
-   Die Seite **Zeilen filtern** entspricht der Seite **Tabellenzeilen filtern** des Assistenten für neue Veröffentlichung. Mithilfe dieser Seite können Sie statische Zeilenfilter für sämtliche Veröffentlichungstypen hinzufügen, bearbeiten und löschen sowie parametrisierte Zeilenfilter und Joinfilter für Mergeveröffentlichungen hinzufügen, bearbeiten und löschen.  
  
-   Auf der Seite **Momentaufnahme** können Sie das Format und den Speicherort der Momentaufnahme angeben und zudem angeben, ob die Momentaufnahme komprimiert werden soll und ob Skripts ausgeführt werden sollen, bevor und nachdem die Momentaufnahme angewendet wird.  
  
-   Die **FTP-Momentaufnahme** auf der Seite (für Momentaufnahme- und transaktionsveröffentlichungen und mergeveröffentlichungen für Verleger, auf denen Versionen vor SQL Server 2005) können Sie angeben, ob Abonnenten momentaufnahmedateien über FTP File Transfer Protocol () herunterladen können.  
  
-   Die **FTP-Momentaufnahme und Internet** (für mergeveröffentlichungen von Verlegern mit SQLServer 2005 oder höher) auf der Seite können Sie angeben, ob Abonnenten momentaufnahmedateien per FTP herunterladen können und ob Abonnenten Abonnements über HTTPS synchronisieren können.  
  
-   Auf der Seite **Abonnementoptionen** können Sie eine Reihe von Optionen festlegen, die auf alle Abonnements angewendet werden. Die Optionen hängen vom Veröffentlichungstyp ab.  
  
-   Auf der Seite **Veröffentlichungszugriffsliste** können Sie angeben, welche Anmeldungen und Gruppen auf eine Veröffentlichung zugreifen können.  
  
-   Über die Seite **Agentsicherheit** können Sie auf die Einstellungen für die Konten zugreifen, unter denen folgende Agents ausgeführt werden. Sie können außerdem Verbindungen mit den Computern in einer Replikationstopologie herstellen: Momentaufnahme-Agent für alle Veröffentlichungen, Protokolllese-Agent für alle Transaktionsveröffentlichungen und Warteschlangenlese-Agent für Transaktionsveröffentlichungen, die Abonnements mit verzögertem Update über eine Warteschlange zulassen.  
  
-   Die **Datenpartitionen** (für mergeveröffentlichungen von Verlegern mit SQLServer 2005 oder höher) auf der Seite können Sie angeben, ob Abonnenten von Veröffentlichungen mit parametrisierten Filtern eine Momentaufnahme anfordern können, wenn eine nicht verfügbar ist. Sie haben zudem die Möglichkeit, Momentaufnahmen für eine oder mehrere Partitionen entweder einmalig oder wiederkehrend gemäß einem Zeitplan zu generieren.  
  
#### So zeigen Sie Veröffentlichungseigenschaften in Management Studio an und ändern sie  
  
1.  Stellen Sie in [!INCLUDE[ssManStudio](../../../includes/ssmanstudio-md.md)]eine Verbindung mit dem Verleger her, und erweitern Sie dann den Serverknoten.  
  
2.  Erweitern Sie den Ordner **Replikation** , und erweitern Sie dann den Ordner **Lokale Veröffentlichungen** .  
  
3.  Mit der rechten Maustaste einer Veröffentlichung, und klicken Sie dann auf **Eigenschaften**.  
  
4.  Ändern Sie die Eigenschaften nach Bedarf, und klicken Sie dann auf **OK**.  
  
#### So zeigen Sie Veröffentlichungseigenschaften im Replikationsmonitor an und ändern sie  
  
1.  Erweitern Sie im linken Bereich des Replikationsmonitors eine Verlegergruppe, und erweitern Sie dann einen Verleger.  
  
2.  Mit der rechten Maustaste einer Veröffentlichung, und klicken Sie dann auf **Eigenschaften**.  
  
3.  Ändern Sie die Eigenschaften nach Bedarf, und klicken Sie dann auf **OK**.  
  
##  <a name="TsqlProcedure"></a> Verwenden von Transact-SQL  
 Veröffentlichungen können mithilfe gespeicherter Replikationsprozeduren programmgesteuert geändert und ihre Eigenschaften zurückgegeben werden. Welche gespeicherten Prozeduren Sie verwenden, hängt vom Typ der Veröffentlichung ab.  
  
#### So zeigen Sie die Eigenschaften einer Momentaufnahme oder einer Transaktionsveröffentlichung an  
  
1.  Führen Sie [Sp_helppublication](../../../relational-databases/system-stored-procedures/sp-helppublication-transact-sql.md), gibt den Namen der Veröffentlichung für die **@publication** Parameter. Wenn Sie diesen Parameter nicht angeben, werden Informationen über alle Veröffentlichungen beim Verleger zurückgegeben.  
  
#### So ändern Sie die Eigenschaften einer Momentaufnahme oder einer Transaktionsveröffentlichung  
  
1.  Führen Sie [Sp_changepublication](../../../relational-databases/system-stored-procedures/sp-changepublication-transact-sql.md), angeben-Eigenschaft der Veröffentlichung zu ändern, in der **@property** Parameter und den neuen Wert dieser Eigenschaft in der **@value** Parameter.  
  
    > [!NOTE]  
    >  Wenn die Änderung das Generieren einer neuen Momentaufnahme erfordert, müssen Sie auch angeben, auf den Wert **1** für **@force_invalidate_snapshot**, und wenn die Änderung erfordert, dass Abonnenten erneut initialisiert werden, geben Sie einen Wert von **1** für **@force_reinit_subscription**. Weitere Informationen zu den Eigenschaften, die bei Änderung erfordern eine neue Momentaufnahme oder eine erneute Initialisierung, finden Sie unter [Ändern von Veröffentlichungs- und Artikeleigenschaften](../../../relational-databases/replication/publish/change-publication-and-article-properties.md).  
  
#### So zeigen Sie die Eigenschaften einer Mergeveröffentlichung an  
  
1.  Führen Sie [Sp_helpmergepublication](../../../relational-databases/system-stored-procedures/sp-helpmergepublication-transact-sql.md), gibt den Namen der Veröffentlichung für die **@publication** Parameter. Wenn Sie diesen Parameter nicht angeben, werden Informationen über alle Veröffentlichungen beim Verleger zurückgegeben.  
  
#### So ändern Sie die Eigenschaften einer Mergeveröffentlichung  
  
1.  Ausführen [Sp_changemergepublication](../../../relational-databases/system-stored-procedures/sp-changemergepublication-transact-sql.md), Angeben der veröffentlichungseigenschaft geändert wird, der **@property** Parameter und den neuen Wert dieser Eigenschaft in der **@value** Parameter.  
  
    > [!NOTE]  
    >  Wenn die Änderung das Generieren einer neuen Momentaufnahme erfordert, müssen Sie auch angeben, auf den Wert **1** für **@force_invalidate_snapshot**, und wenn die Änderung erfordert, dass Abonnenten erneut initialisiert werden, geben Sie einen Wert von **1** für **@force_reinit_subscription** für Weitere Informationen zu den Eigenschaften, die bei Änderung erfordern eine neue Momentaufnahme oder eine erneute Initialisierung, finden Sie unter [Ändern Veröffentlichungs- und Artikeleigenschaften](../../../relational-databases/replication/publish/change-publication-and-article-properties.md).  
  
#### So zeigen Sie die Eigenschaften einer Momentaufnahme an  
  
1.  Führen Sie [Sp_helppublication_snapshot](../../../relational-databases/system-stored-procedures/sp-helppublication-snapshot-transact-sql.md), gibt den Namen der Veröffentlichung für die **@publication** Parameter.  
  
#### So ändern Sie die Eigenschaften einer Momentaufnahme  
  
1.  Führen Sie [Sp_changepublication_snapshot](../../../relational-databases/system-stored-procedures/sp-changepublication-snapshot-transact-sql.md), eines oder mehrere der neuen momentaufnahmeeigenschaften für die entsprechenden momentaufnahmeparameter angeben.  
  
###  <a name="TsqlExample"></a> Beispiele (Transact-SQL)  
 In diesem Beispiel für Transaktionsreplikation werden die Eigenschaften der Veröffentlichung zurückgegeben.  
  
 [!code-sql[HowTo#sp_helppublication](../../../relational-databases/replication/codesnippet/tsql/view-and-modify-publicat_1.sql)]  
  
 In diesem Beispiel für Transaktionsreplikation wird die Schemareplikation für die Veröffentlichung deaktiviert.  
  
 [!code-sql[HowTo#sp_changepublication](../../../relational-databases/replication/codesnippet/tsql/view-and-modify-publicat_2.sql)]  
  
 In diesem Beispiel für Mergereplikation werden die Eigenschaften der Veröffentlichung zurückgegeben.  
  
 [!code-sql[HowTo#sp_helpmergepublication](../../../relational-databases/replication/codesnippet/tsql/view-and-modify-publicat_3.sql)]  
  
 In diesem Beispiel für Mergereplikation wird die Schemareplikation für die Veröffentlichung deaktiviert.  
  
 [!code-sql[HowTo#sp_changemergepublication](../../../relational-databases/replication/codesnippet/tsql/view-and-modify-publicat_4.sql)]  
  
##  <a name="RMOProcedure"></a> Verwenden von Replikationsverwaltungsobjekten (RMO)  
 Sie können Veröffentlichungen ändern und mithilfe von Replikationsverwaltungsobjekten (RMO) programmgesteuert auf ihre Eigenschaften zugreifen. Welche RMO-Klassen zum Anzeigen oder Ändern von Veröffentlichungseigenschaften verwendet werden, hängt vom Typ der Veröffentlichung ab.  
  
#### So zeigen Sie die Eigenschaften einer Momentaufnahme- oder einer Transaktionsveröffentlichung an oder ändern diese  
  
1.  Erstellen Sie eine Verbindung mit dem Verleger mithilfe der <xref:Microsoft.SqlServer.Management.Common.ServerConnection> Klasse.  
  
2.  Erstellen Sie eine Instanz von der <xref:Microsoft.SqlServer.Replication.TransPublication> Klasse, legen die <xref:Microsoft.SqlServer.Replication.Publication.Name%2A> und <xref:Microsoft.SqlServer.Replication.Publication.DatabaseName%2A> Eigenschaften für die Veröffentlichung, und legen die <xref:Microsoft.SqlServer.Replication.ReplicationObject.ConnectionContext%2A> -Eigenschaft auf die in Schritt 1 erstellte Verbindung.  
  
3.  Rufen Sie die <xref:Microsoft.SqlServer.Replication.ReplicationObject.LoadProperties%2A> Methode zum Abrufen der Eigenschaften des Objekts. Wenn diese Methode **false**zurückgibt, sind die Veröffentlichungseigenschaften in Schritt 2 falsch definiert, oder die Veröffentlichung ist nicht vorhanden.  
  
4.  (Optional) Um Eigenschaften zu ändern, legen Sie einen neuen Wert für eine oder mehrere festlegbaren Eigenschaften fest. Verwenden Sie den logischen Operator (**&** in Microsoft Visual c# und **und** in Microsoft Visual Basic) bestimmt, ob eine bestimmte <xref:Microsoft.SqlServer.Replication.PublicationAttributes> Wert wird festgelegt, für die <xref:Microsoft.SqlServer.Replication.Publication.Attributes%2A> Eigenschaft. Verwenden Sie den inklusiven logischen OR-Operator (**|** in Visual c# und **oder** in Visual Basic) und den exklusiven logischen OR-Operator (**^** in Visual c# und **Xor** in Visual Basic) so ändern Sie die <xref:Microsoft.SqlServer.Replication.PublicationAttributes> Werte für die <xref:Microsoft.SqlServer.Replication.Publication.Attributes%2A> Eigenschaft.  
  
5.  (Optional) Wenn Sie einen Wert von angegeben **true** für <xref:Microsoft.SqlServer.Replication.ReplicationObject.CachePropertyChanges%2A>, rufen Sie die <xref:Microsoft.SqlServer.Replication.ReplicationObject.CommitPropertyChanges%2A> Methode, um die Änderungen auf dem Server. Wenn Sie einen Wert von angegeben **false** für <xref:Microsoft.SqlServer.Replication.ReplicationObject.CachePropertyChanges%2A> (Standard), Änderungen werden an den Server sofort gesendet.  
  
#### So zeigen Sie die Eigenschaften einer Mergeveröffentlichung an oder ändern diese  
  
1.  Erstellen Sie eine Verbindung mit dem Verleger mithilfe der <xref:Microsoft.SqlServer.Management.Common.ServerConnection> Klasse.  
  
2.  Erstellen Sie eine Instanz von der <xref:Microsoft.SqlServer.Replication.MergePublication> Klasse, legen die <xref:Microsoft.SqlServer.Replication.Publication.Name%2A> und <xref:Microsoft.SqlServer.Replication.Publication.DatabaseName%2A> Eigenschaften für die Veröffentlichung, und legen die <xref:Microsoft.SqlServer.Replication.ReplicationObject.ConnectionContext%2A> -Eigenschaft auf die in Schritt 1 erstellte Verbindung.  
  
3.  Rufen Sie die <xref:Microsoft.SqlServer.Replication.ReplicationObject.LoadProperties%2A> Methode zum Abrufen der Eigenschaften des Objekts. Wenn diese Methode **false**zurückgibt, sind die Veröffentlichungseigenschaften in Schritt 2 falsch definiert, oder die Veröffentlichung ist nicht vorhanden.  
  
4.  (Optional) Um Eigenschaften zu ändern, legen Sie einen neuen Wert für eine oder mehrere festlegbaren Eigenschaften fest. Verwenden Sie den logischen Operator (**&** in Visual c# und **und** in Visual Basic) bestimmt, ob eine bestimmte <xref:Microsoft.SqlServer.Replication.PublicationAttributes> Wert wird festgelegt, für die <xref:Microsoft.SqlServer.Replication.Publication.Attributes%2A> Eigenschaft. Verwenden Sie den inklusiven logischen OR-Operator (**|** in Visual c# und **oder** in Visual Basic) und den exklusiven logischen OR-Operator (**^** in Visual c# und **Xor** in Visual Basic) so ändern Sie die <xref:Microsoft.SqlServer.Replication.PublicationAttributes> Werte für die <xref:Microsoft.SqlServer.Replication.Publication.Attributes%2A> Eigenschaft.  
  
5.  (Optional) Wenn Sie einen Wert von angegeben **true** für <xref:Microsoft.SqlServer.Replication.ReplicationObject.CachePropertyChanges%2A>, rufen Sie die <xref:Microsoft.SqlServer.Replication.ReplicationObject.CommitPropertyChanges%2A> Methode, um die Änderungen auf dem Server. Wenn Sie einen Wert von angegeben **false** für <xref:Microsoft.SqlServer.Replication.ReplicationObject.CachePropertyChanges%2A> (Standard), Änderungen werden an den Server sofort gesendet.  
  
###  <a name="PShellExample"></a> Beispiele (RMO)  
 In diesem Beispiel werden Veröffentlichungsattribute einer Transaktionsveröffentlichung festgelegt. Die Änderungen werden zwischengespeichert, bis sie explizit zum Server gesendet werden.  
  
 [!code-csharp[HowTo#rmo_ChangeTranPub_cached](../../../relational-databases/replication/codesnippet/csharp/rmohowto/rmotestevelope.cs#rmo_changetranpub_cached)]  
  
 [!code-vb[HowTo#rmo_vb_ChangeTranPub_cached](../../../relational-databases/replication/codesnippet/visualbasic/rmohowtovb/rmotestenv.vb#rmo_vb_changetranpub_cached)]  
  
 In diesem Beispiel wird die DDL-Replikation für eine Mergeveröffentlichung deaktiviert.  
  
 [!code-csharp[HowTo#rmo_ChangeMergePub_ddl](../../../relational-databases/replication/codesnippet/csharp/rmohowto/rmotestevelope.cs#rmo_changemergepub_ddl)]  
  
 [!code-vb[HowTo#rmo_vb_ChangeMergePub_ddl](../../../relational-databases/replication/codesnippet/visualbasic/rmohowtovb/rmotestenv.vb#rmo_vb_changemergepub_ddl)]  
  
## Siehe auch  
 [Veröffentlichen von Daten und Datenbankobjekten](../../../relational-databases/replication/publish/publish-data-and-database-objects.md)   
 [Ändern von Veröffentlichungs- und Artikeleigenschaften](../../../relational-databases/replication/publish/change-publication-and-article-properties.md)   
 [Vornehmen von Schemaänderungen in Veröffentlichungsdatenbanken](../../../relational-databases/replication/publish/make-schema-changes-on-publication-databases.md)   
 [Konzepte für gespeicherte Systemprozeduren für die Replikation](../../../relational-databases/replication/concepts/replication-system-stored-procedures-concepts.md)   
 [Fügen Sie und Löschen von Artikeln aus einer Veröffentlichung & #40 hinzu; SQL Server Management Studio & #41;](../../../relational-databases/replication/publish/add-articles-to-and-drop-articles-from-a-publication.md)   
 [Anzeigen von Informationen und Ausführen von Aufgaben für eine Veröffentlichung & #40; Der Replikationsmonitor & #41;](../../../relational-databases/replication/monitor/view-information-and-perform-tasks-for-a-publication-replication-monitor.md)   
 [Anzeigen und Ändern von Artikeleigenschaften](../../../relational-databases/replication/publish/view-and-modify-article-properties.md)  
  
  