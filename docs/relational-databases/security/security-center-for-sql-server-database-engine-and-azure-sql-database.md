---
title: "Sicherheitscenter f&#252;r SQL Server-Datenbankmodul und Azure SQL-Datenbank | Microsoft Docs"
ms.custom: 
  - "MSDN content"
  - "MSDN - SQL DB"
ms.date: "01/31/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.service: "sql-database"
ms.suite: ""
ms.technology: 
  - "database-engine"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "Security [SQL Server]"
helpviewer_keywords: 
  - "SQL Server-Sicherheit"
  - "Sicherheit [SQL Server]"
  - "Datenbanksicherheit [SQL Server]"
  - "Datenbanken [SQL Server], Sicherheit"
ms.assetid: dfb39d16-722a-4734-94bb-98e61e014ee7
caps.latest.revision: 55
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 54
---
# Sicherheitscenter f&#252;r SQL Server-Datenbankmodul und Azure SQL-Datenbank
[!INCLUDE[tsql-appliesto-ss2008-all_md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  Diese Seite enthält Links, mit deren Hilfe Sie die erforderlichen Informationen zur Sicherheit und zum Schutz in [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] und [!INCLUDE[ssSDSFull](../../includes/sssdsfull-md.md)] finden.  
  
 **Legende**  
  
 ![security-center-legend](../../relational-databases/performance/media/security-center-legend.PNG "security-center-legend")  
  
##  <a name="Who"></a> Authentifizierung: Wer sind Sie?  
  
|||  
|-|-|  
|**Wer authentifiziert?**<br /><br /> ![security-center-both](../../relational-databases/performance/media/security-center-both.png "security-center-both") Windows-Authentifizierung<br /><br /> ![security-center-both](../../relational-databases/performance/media/security-center-both.png "security-center-both") [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Authentifizierung|Wer authentifiziert? (Windows oder [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)])<br /><br /> [Auswählen eines Authentifizierungsmodus](../../relational-databases/security/choose-an-authentication-mode.md)<br /><br /> [Herstellen einer Verbindung mit SQL-Datenbank unter Verwendung der Azure Active Directory-Authentifizierung](https://azure.microsoft.com/documentation/articles/sql-database-aad-authentication/)|  
|**Wo authentifiziert?**<br /><br /> ![security-center-both](../../relational-databases/performance/media/security-center-both.png "security-center-both") In der Masterdatenbank: Anmeldenamen und Datenbankbenutzer<br /><br /> ![security-center-both](../../relational-databases/performance/media/security-center-both.png "security-center-both") In der Benutzerdatenbank: Eigenständige Datenbankbenutzer|Authentifizierung bei der Masterdatenbank (Anmeldenamen und Datenbankbenutzer)<br /><br /> [Erstellen eines SQL Server-Anmeldenamens](../../relational-databases/security/authentication-access/create-a-login.md)<br /><br /> [Verwalten von Datenbanken und Anmeldenamen in Azure SQL-Datenbank](http://msdn.microsoft.com/library/ee336235.aspx)<br /><br /> [Erstellen eines Datenbankbenutzers](../../relational-databases/security/authentication-access/create-a-database-user.md)<br /><br /> <br /><br /> Authentifizierung bei einer Benutzerdatenbank<br /><br /> [Eigenständige Datenbankbenutzer - machen Sie Ihre Datenbank portabel](../../relational-databases/security/contained-database-users-making-your-database-portable.md)|  
|**Verwenden anderer Identitäten**<br /><br /> ![security-center-both](../../relational-databases/performance/media/security-center-both.png "security-center-both") Anmeldeinformationen<br /><br /> ![security-center-sqlserver](../../relational-databases/performance/media/security-center-sqlserver.png "security-center-sqlserver") Ausführen unter anderem Anmeldenamen<br /><br /> ![security-center-both](../../relational-databases/performance/media/security-center-both.png "security-center-both") Ausführen als anderer Datenbankbenutzer|[Anmeldeinformationen &#40;Datenbankmodul&#41;](../../relational-databases/security/authentication-access/credentials-database-engine.md)<br /><br /> [Ausführen unter anderem Anmeldenamen](../../t-sql/statements/execute-as-transact-sql.md)<br /><br /> [Ausführen als anderer Datenbankbenutzer](../../t-sql/statements/execute-as-transact-sql.md)|  
  
##  <a name="What"></a> Autorisierung: Was können Sie tun?  
  
|||  
|-|-|  
|**Gewährung, Widerrufen und Verweigern von Berechtigungen**<br /><br /> ![security-center-both](../../relational-databases/performance/media/security-center-both.png "security-center-both") Sicherungsfähige Klassen<br /><br /> ![security-center-sqlserver](../../relational-databases/performance/media/security-center-sqlserver.png "security-center-sqlserver") Granulare Serverberechtigungen<br /><br /> ![security-center-both](../../relational-databases/performance/media/security-center-both.png "security-center-both") Granulare Datenbankberechtigungen|[Berechtigungshierarchie &#40;Datenbankmodul&#41;](../../relational-databases/security/permissions-hierarchy-database-engine.md)<br /><br /> [Berechtigungen](../../relational-databases/security/permissions-database-engine.md)<br /><br /> [Sicherungsfähige Elemente](../../relational-databases/security/securables.md)<br /><br /> [Erste Schritte mit Berechtigungen für das Datenbankmodul](../../relational-databases/security/authentication-access/getting-started-with-database-engine-permissions.md)|  
|**Sicherheit durch Rollen**<br /><br /> ![security-center-sqlserver](../../relational-databases/performance/media/security-center-sqlserver.png "security-center-sqlserver") Rollen auf Serverebene<br /><br /> ![security-center-both](../../relational-databases/performance/media/security-center-both.png "security-center-both") Rollen auf Datenbankebene|[Rollen auf Serverebene](../../relational-databases/security/authentication-access/server-level-roles.md)<br /><br /> [Rollen auf Datenbankebene](../../relational-databases/security/authentication-access/database-level-roles.md)|  
|**Einschränken des Datenzugriffs auf ausgewählte Datenelemente**<br /><br /> ![security-center-both](../../relational-databases/performance/media/security-center-both.png "security-center-both") Einschränken des Datenzugriffs mit Ansichten/Verfahren<br /><br /> ![security-center-both](../../relational-databases/performance/media/security-center-both.png "security-center-both") Sicherheit auf Zeilenebene<br /><br /> ![security-center-both](../../relational-databases/performance/media/security-center-both.png "security-center-both") Dynamische Datenmaskierung<br /><br /> ![security-center-both](../../relational-databases/performance/media/security-center-both.png "security-center-both") Signierte Objekte|Einschränken des Datenzugriffs mit [Ansichten](../../relational-databases/views/views.md) und [Verfahren](../../relational-databases/stored-procedures/stored-procedures-database-engine.md)<br /><br /> [Sicherheit auf Zeilenebene (SQL Server)](../../relational-databases/security/row-level-security.md)<br /><br /> [Sicherheit auf Zeilenebene (Azure SQL-Datenbank)](http://msdn.microsoft.com/library/azure/dn765131.aspx)<br /><br /> [Dynamische Datenmaskierung (SQL Server)](../../relational-databases/security/dynamic-data-masking.md)<br /><br /> [Dynamische Datenmaskierung (Azure SQL-Datenbank)](http://azure.microsoft.com/documentation/articles/sql-database-dynamic-data-masking-get-started/)<br /><br /> [Signierte Objekte](../../t-sql/statements/add-signature-transact-sql.md)|  
  
##  <a name="Encrypt"></a> Verschlüsselung: Speichern geheimer Schlüssel  
  
|||  
|-|-|  
|**Verschlüsseln von Dateien**<br /><br /> ![security-center-sqlserver](../../relational-databases/performance/media/security-center-sqlserver.png "security-center-sqlserver") BitLocker-Verschlüsselung (Laufwerksebene)<br /><br /> ![security-center-sqlserver](../../relational-databases/performance/media/security-center-sqlserver.png "security-center-sqlserver") NTFS-Verschlüsselung (Ordnerebene)<br /><br /> ![security-center-both](../../relational-databases/performance/media/security-center-both.png "security-center-both") Transparente Datenverschlüsselung (Dateiebene)<br /><br /> ![security-center-both](../../relational-databases/performance/media/security-center-both.png "security-center-both") Sicherungsverschlüsselung (Dateiebene)|[BitLocker (Laufwerksebene)](http://support.microsoft.com/kb/2855131)<br /><br /> [NTFS-Verschlüsselung (Ordnerebene)](http://msdn.microsoft.com/library/dd163562.aspx)<br /><br /> [Transparente Datenverschlüsselung (Dateiebene)](../../relational-databases/security/encryption/transparent-data-encryption-tde.md)<br /><br /> [Sicherungsverschlüsselung (Dateiebene)](../../relational-databases/backup-restore/backup-encryption.md)|  
|**Verschlüsseln von Quellen**<br /><br /> ![security-center-sqlserver](../../relational-databases/performance/media/security-center-sqlserver.png "security-center-sqlserver") Erweiterbares Schlüsselverwaltungsmodul<br /><br /> ![security-center-sqlserver](../../relational-databases/performance/media/security-center-sqlserver.png "security-center-sqlserver") Im Azure Schlüsseltresor gespeicherte Schlüssel<br /><br /> ![security-center-both](../../relational-databases/performance/media/security-center-both.png "security-center-both") Always Encrypted|[Erweiterbares Schlüsselverwaltungsmodul](../../relational-databases/security/encryption/extensible-key-management-ekm.md)<br /><br /> [Im Azure Schlüsseltresor gespeicherte Schlüssel](../../relational-databases/security/encryption/extensible-key-management-using-azure-key-vault-sql-server.md)<br /><br /> [Always Encrypted](../../relational-databases/security/encryption/always-encrypted-database-engine.md)|  
|**Spalte, Daten und Schlüsselverschlüsselung**<br /><br /> ![security-center-both](../../relational-databases/performance/media/security-center-both.png "security-center-both") Verschlüsseln durch Zertifikat<br /><br /> ![security-center-both](../../relational-databases/performance/media/security-center-both.png "security-center-both") Verschlüsseln mit symmetrischem Schlüssel<br /><br /> ![security-center-both](../../relational-databases/performance/media/security-center-both.png "security-center-both") Verschlüsseln mit asymmetrischem Schlüssel<br /><br /> ![security-center-both](../../relational-databases/performance/media/security-center-both.png "security-center-both") Verschlüsseln durch Passphrase|[Verschlüsseln durch Zertifikat](../../t-sql/functions/encryptbycert-transact-sql.md)<br /><br /> [Verschlüsseln mit asymmetrischem Schlüssel](../../t-sql/functions/encryptbyasymkey-transact-sql.md)<br /><br /> [Verschlüsseln mit symmetrischem Schlüssel](../../t-sql/functions/encryptbykey-transact-sql.md)<br /><br /> [Verschlüsseln durch Passphrase](../../t-sql/functions/encryptbypassphrase-transact-sql.md)<br /><br /> [Verschlüsseln einer Datenspalte](../../relational-databases/security/encryption/encrypt-a-column-of-data.md)|  
  
##  <a name="Connect"></a> Verbindungssicherheit: Einschränken und Schützen  
  
|||  
|-|-|  
|**Firewallschutz**<br /><br /> ![security-center-sqlserver](../../relational-databases/performance/media/security-center-sqlserver.png "security-center-sqlserver") Windows-Firewalleinstellungen<br /><br /> ![security-center-sqldb](../../relational-databases/security/media/security-center-sqldb.png "security-center-sqldb") Azure Service-Firewalleinstellungen<br /><br /> ![security-center-sqldb](../../relational-databases/security/media/security-center-sqldb.png "security-center-sqldb") Datenbank-Firewalleinstellungen|[Konfigurieren einer Windows-Firewall für Datenbankmodulzugriff](../../database-engine/configure-windows/configure-a-windows-firewall-for-database-engine-access.md)<br /><br /> [Azure SQL-Datenbank-Firewalleinstellungen](../../relational-databases/system-stored-procedures/sp-set-database-firewall-rule-azure-sql-database.md)<br /><br /> [Azure Service-Firewalleinstellungen](../../relational-databases/system-stored-procedures/sp-set-firewall-rule-azure-sql-database.md)|  
|**Verschlüsseln von Daten in Transit**<br /><br /> ![security-center-both](../../relational-databases/performance/media/security-center-both.png "security-center-both") Erzwungene SSL-Verbindungen<br /><br /> ![security-center-sqlserver](../../relational-databases/performance/media/security-center-sqlserver.png "security-center-sqlserver") Optionale SSL-Verbindungen|[Secure Sockets Layer für das Datenbankmodul](../../database-engine/configure-windows/enable encrypted connections to the database engine.md)<br /><br /> [Secure Sockets Layer für SQL-Datenbank](https://msdn.microsoft.com/library/azure/ff394108.aspx)<br /><br /> [TLS 1.2-Unterstützung für Microsoft SQL Server](https://support.microsoft.com/kb/3135244)|  
  
##  <a name="Audit"></a> Überwachung: Aufzeichnen des Zugriffs  
  
|||  
|-|-|  
|**Automatisierte Überwachung**<br /><br /> ![security-center-sqlserver](../../relational-databases/performance/media/security-center-sqlserver.png "security-center-sqlserver") [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Überwachung (Server- und Datenbankebene)<br /><br /> ![security-center-sqldb](../../relational-databases/security/media/security-center-sqldb.png "security-center-sqldb") [!INCLUDE[ssSDS](../../includes/sssds-md.md)] Überwachung (Datenbankebene)<br /><br /> ![security-center-sqldb](../../relational-databases/security/media/security-center-sqldb.png "security-center-sqldb") Bedrohungserkennung|[SQL Server Audit &#40;Datenbankmodul&#41;](../../relational-databases/security/auditing/sql-server-audit-database-engine.md)<br /><br /> [SQL-Datenbanküberwachung](http://azure.microsoft.com/documentation/articles/sql-database-auditing-get-started/)<br /><br /> [Erste Schritte mit der SQL-Datenbanküberwachung](https://azure.microsoft.com/documentation/articles/sql-database-threat-detection-get-started/)|  
|**Benutzerdefinierte Überwachung**<br /><br /> ![security-center-both](../../relational-databases/performance/media/security-center-both.png "security-center-both") Trigger|Benutzerdefinierte Überwachungsimplementierung: Erstellen von [DDL-Triggern](../../relational-databases/triggers/ddl-triggers.md) und [DML-Triggern](../../relational-databases/triggers/dml-triggers.md)|  
|**Kompatibilität**<br /><br /> ![security-center-both](../../relational-databases/performance/media/security-center-both.png "security-center-both") Kompatibilität|SQL Server:<br />                        [Common Criteria](http://go.microsoft.com/fwlink/?LinkId=616319)<br /><br /> SQL-Datenbank:<br />                        [Microsoft Azure Trust Center: Compliance nach Features](http://azure.microsoft.com/support/trust-center/services/)|  
  
##  <a name="SQLInjection"></a> SQL Injection  
 Bei der Einschleusung von SQL-Befehlen wird ein bösartiger Code in Zeichenfolgen eingefügt, die später zur Analyse und Ausführung an [!INCLUDE[ssDE](../../includes/ssde-md.md)] übergeben werden. Sie sollten jede Prozedur, die SQL-Anweisungen erstellt, nach Injection-Anfälligkeiten überprüfen, denn [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] führt alle empfangenen gültigen Abfragen aus. Alle Datenbanksysteme unterliegen einem gewissen Risiko für die Einschleusung von SQL-Befehlen, und viele der Sicherheitslücken entstehen in der Anwendung, die [!INCLUDE[ssDE](../../includes/ssde-md.md)] abfragt. Sie können Angriffe, die das Ziel haben, SQL-Befehle einzuschleusen, abwehren, indem Sie gespeicherte Prozeduren und parametrisierte Befehle verwenden, dynamisches SQL vermeiden und die Berechtigungen aller Benutzer einschränken.  Weitere Informationen finden Sie unter [Einschleusung von SQL-Befehlen](../../relational-databases/security/sql-injection.md).  
  
 Zusätzliche Links für Anwendungsprogrammierer:  
  
-   [Anwendungssicherheitsszenarios in SQL Server](https://msdn.microsoft.com/library/bb669057.aspx)  
  
-   [Schreiben von sicherem dynamischem SQL in SQL Server](https://msdn.microsoft.com/library/bb669091.aspx)  
  
-   [Gewusst wie: Schutz vor Einschleusung von SQL-Befehlen in ASP.NET](https://msdn.microsoft.com/library/ff648339.aspx)  
  
## Siehe auch  
 [Erste Schritte mit Berechtigungen für das Datenbankmodul](../../relational-databases/security/authentication-access/getting-started-with-database-engine-permissions.md)   
 [Sichern von SQL Server](../../relational-databases/security/securing-sql-server.md)   
 [Prinzipale &#40;Datenbankmodul&#41;](../../relational-databases/security/authentication-access/principals-database-engine.md)   
 [SQL Server-Zertifikate und asymmetrische Schlüssel](../../relational-databases/security/sql-server-certificates-and-asymmetric-keys.md)   
 [SQL Server-Verschlüsselung](../../relational-databases/security/encryption/sql-server-encryption.md)   
 [Oberflächenkonfiguration](../../relational-databases/security/surface-area-configuration.md)   
 [Sichere Kennwörter](../../relational-databases/security/strong-passwords.md)   
 [TRUSTWORTHY-Datenbankeigenschaft](../../relational-databases/security/trustworthy-database-property.md)   
 [Datenbankmodulfunktionen und Tasks](../Topic/Database%20Engine%20Features%20and%20Tasks.md)  
  
  