---
title: Berechtigungen (Datenbank-Engine) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 10/14/2015
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: security
ms.topic: conceptual
f1_keywords:
- sql12.swb.databaseuser.permissions.database.f1--May use common.permissions
- sql12.swb.databaseuser.permissions.object.f1--May use common.permissions
helpviewer_keywords:
- REFERENCES permission
- permissions [SQL Server]
- security [SQL Server], permissions
- naming conventions [SQL Server]
ms.assetid: f28e3dea-24e6-4a81-877b-02ec4c7e36b9
author: VanMSFT
ms.author: vanto
manager: craigg
ms.openlocfilehash: 746d547b680817868de33759983dc908e9806bb6
ms.sourcegitcommit: 334cae1925fa5ac6c140e0b2c38c844c477e3ffb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/13/2018
ms.locfileid: "53355012"
---
# <a name="permissions-database-engine"></a>Berechtigungen (Datenbank-Engine)
  Jedes sicherungsfähige [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Element hat zugeordnete Berechtigungen, die einem Prinzipal erteilt werden können. Dieses Thema enthält die folgenden Informationen:  
  
-   [Benennungskonventionen für Berechtigungen](#_conventions)  
  
-   [Berechtigungen für bestimmte sicherungsfähige Elemente](#_securables)  
  
-   [SQL Server-Berechtigungen](#_permissions)  
  
-   [Algorithmus zur berechtigungsprüfung](#_algorithm)  
  
-   [Beispiele](#_examples)  
  
##  <a name="_conventions"></a> Benennungskonventionen für Berechtigungen  
 Im Folgenden werden die allgemeinen Konventionen beschrieben, die beim Benennen von Berechtigungen befolgt werden:  
  
-   CONTROL  
  
     Überträgt besitzähnliche Funktionen an den Empfänger. Der Empfänger verfügt über alle definierten Berechtigungen für das sicherungsfähige Element. Ein Prinzipal, dem die Berechtigung CONTROL erteilt wurde, kann auch Berechtigungen für das sicherungsfähige Element erteilen. Da es sich bei dem [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Sicherheitsmodell um ein hierarchisches Modell handelt, beinhaltet CONTROL für einen bestimmten Gültigkeitsbereich implizit auch CONTROL für alle sicherungsfähigen Elemente in diesem Gültigkeitsbereich. CONTROL für eine Datenbank impliziert alle Berechtigungen für die Datenbank, alle Berechtigungen für alle Assemblys in der Datenbank, alle Berechtigungen für alle Schemas in der Datenbank sowie alle Berechtigungen für Objekte innerhalb aller Schemas in der Datenbank.  
  
-   ALTER  
  
     Überträgt die Berechtigung, die Eigenschaften, mit Ausnahme des Besitzes, eines bestimmten sicherungsfähigen Elements zu ändern. Wenn ALTER für einen Gültigkeitsbereich erteilt wird, wird damit auch die Berechtigung zum Ändern, Erstellen oder Löschen eines sicherungsfähigen Elements erteilt, das in diesen Bereich fällt. So beinhaltet die Berechtigung ALTER für ein Schema auch die Berechtigung zum Erstellen, Ändern und Löschen von Objekten aus dem Schema.  
  
-   ALTER ANY \<*Server Securable*>, wobei es sich bei *Server Securable* um jeden beliebigen sicherungsfähigen Server handeln kann.  
  
     Überträgt die Berechtigung zum Erstellen, Ändern oder Löschen einzelner Instanzen des *Server Securable*. So überträgt z. B. ALTER ANY LOGIN die Berechtigung zum Erstellen, Ändern oder Löschen einer beliebigen Anmeldung in der Instanz.  
  
-   ALTER ANY \<*Database Securable*>, wobei *Database Securable* jedes beliebige sicherungsfähige Element auf Datenbankebene sein kann.  
  
     Überträgt die Berechtigung zum Erstellen, Ändern oder Löschen (CREATE, ALTER oder DROP) einzelner Instanzen des *Database Securable*. So überträgt z. B. ALTER ANY SCHEMA die Berechtigung zum Erstellen, Ändern oder Löschen eines beliebigen Schemas in der Datenbank.  
  
-   TAKE OWNERSHIP  
  
     Ermöglicht dem Empfänger, Besitzer des sicherungsfähigen Elements zu werden, für das die Berechtigung erteilt wird.  
  
-   IMPERSONATE \<*Anmeldung*>  
  
     Ermöglicht dem Empfänger, die Identität des Anmeldenamens anzunehmen.  
  
-   IMPERSONATE \<*Benutzer*>  
  
     Ermöglicht dem Empfänger, die Identität des Benutzers anzunehmen.  
  
-   CREATE \<*Server Securable*>  
  
     Überträgt dem Empfänger die Berechtigung zum Erstellen des *Server Securable*.  
  
-   CREATE \<*Database Securable*>  
  
     Überträgt dem Berechtigten die Berechtigung zum Erstellen des *Database Securable*.  
  
-   CREATE \<*Schema-contained Securable*>  
  
     Überträgt die Berechtigung zum Erstellen des im Schema enthaltenen sicherungsfähigen Elements. Es wird jedoch die Berechtigung ALTER für das Schema benötigt, um das sicherungsfähige Element in einem bestimmten Schema zu erstellen.  
  
-   VIEW DEFINITION  
  
     Gewährt dem Empfänger Zugriff auf Metadaten.  
  
-   REFERENCES  
  
     Die REFERENCES-Berechtigung für eine Tabelle ist erforderlich, um eine FOREIGN KEY-Einschränkung zu erstellen, die auf die betreffende Tabelle verweist.  
  
     Die REFERENCES-Berechtigung ist für ein Objekt erforderlich, um eine FUNCTION oder VIEW mit der `WITH SCHEMABINDING` -Klausel zu erstellen, die auf das betreffende Objekt verweist.  
  
## <a name="chart-of-sql-server-permissions"></a>Diagramm der SQL Server-Berechtigungen  
 Navigieren Sie zu [https://go.microsoft.com/fwlink/?LinkId=229142](https://go.microsoft.com/fwlink/?LinkId=229142), um ein Diagramm aller [!INCLUDE[ssDE](../../includes/ssde-md.md)]-Berechtigungen im PDF-Format abzurufen.  
  
##  <a name="_securables"></a> Berechtigungen anwendbar für bestimmte sicherungsfähige Elemente  
 Die folgende Tabelle enthält eine Liste der wichtigsten Berechtigungsklassen und der sicherungsfähigen Elemente, für die sie erteilt werden können.  
  
|Berechtigung|Betrifft|  
|----------------|----------------|  
|SELECT|Synonyme<br /><br /> Tabellen und Spalten<br /><br /> Tabellenwertfunktionen, [!INCLUDE[tsql](../../includes/tsql-md.md)] und CLR (Common Language Runtime) sowie Spalten<br /><br /> Sichten und Spalten|  
|VIEW CHANGE TRACKING|Tabellen<br /><br /> Schemas|  
|UPDATE|Synonyme<br /><br /> Tabellen und Spalten<br /><br /> Sichten und Spalten<br /><br /> Sequenzobjekte|  
|REFERENCES|Skalar- und Aggregatfunktionen ([!INCLUDE[tsql](../../includes/tsql-md.md)] und CLR)<br /><br /> [!INCLUDE[ssSB](../../includes/sssb-md.md)] -Warteschlangen<br /><br /> Tabellen und Spalten<br /><br /> Tabellenwertfunktionen ([!INCLUDE[tsql](../../includes/tsql-md.md)] und CLR) sowie Spalten<br /><br /> Typen<br /><br /> Sichten und Spalten<br /><br /> Sequenzobjekte|  
|INSERT|Synonyme<br /><br /> Tabellen und Spalten<br /><br /> Sichten und Spalten|  
|DELETE|Synonyme<br /><br /> Tabellen und Spalten<br /><br /> Sichten und Spalten|  
|Führen Sie|Prozeduren ([!INCLUDE[tsql](../../includes/tsql-md.md)] und CLR)<br /><br /> Skalar- und Aggregatfunktionen ([!INCLUDE[tsql](../../includes/tsql-md.md)] und CLR)<br /><br /> Synonyme<br /><br /> CLR-Typen|  
|RECEIVE|[!INCLUDE[ssSB](../../includes/sssb-md.md)] -Warteschlangen|  
|VIEW DEFINITION|Verfügbarkeitsgruppen<br /><br /> Prozeduren ([!INCLUDE[tsql](../../includes/tsql-md.md)] und CLR)<br /><br /> [!INCLUDE[ssSB](../../includes/sssb-md.md)] -Warteschlangen<br /><br /> Skalar- und Aggregatfunktionen ([!INCLUDE[tsql](../../includes/tsql-md.md)] und CLR)<br /><br /> Anmeldungen, Benutzer und Rollen<br /><br /> Synonyme<br /><br /> Tabellen<br /><br /> Tabellenwertfunktionen ([!INCLUDE[tsql](../../includes/tsql-md.md)] und CLR)<br /><br /> Ansichten<br /><br /> Sequenzobjekte|  
|ALTER|Verfügbarkeitsgruppen<br /><br /> Prozeduren ([!INCLUDE[tsql](../../includes/tsql-md.md)] und CLR)<br /><br /> Skalar- und Aggregatfunktionen ([!INCLUDE[tsql](../../includes/tsql-md.md)] und CLR)<br /><br /> Sequenzobjekte<br /><br /> Anmeldungen, Benutzer und Rollen<br /><br /> [!INCLUDE[ssSB](../../includes/sssb-md.md)] -Warteschlangen<br /><br /> Tabellen<br /><br /> Tabellenwertfunktionen ([!INCLUDE[tsql](../../includes/tsql-md.md)] und CLR)<br /><br /> Ansichten|  
|TAKE OWNERSHIP|Verfügbarkeitsgruppen<br /><br /> Rollen<br /><br /> Prozeduren ([!INCLUDE[tsql](../../includes/tsql-md.md)] und CLR)<br /><br /> Skalar- und Aggregatfunktionen ([!INCLUDE[tsql](../../includes/tsql-md.md)] und CLR)<br /><br /> Serverrollen<br /><br /> Synonyme<br /><br /> Tabellen<br /><br /> Tabellenwertfunktionen ([!INCLUDE[tsql](../../includes/tsql-md.md)] und CLR)<br /><br /> Ansichten<br /><br /> Sequenzobjekte|  
|CONTROL|Verfügbarkeitsgruppen<br /><br /> Prozeduren ([!INCLUDE[tsql](../../includes/tsql-md.md)] und CLR)<br /><br /> Skalar- und Aggregatfunktionen ([!INCLUDE[tsql](../../includes/tsql-md.md)] und CLR)<br /><br /> Anmeldungen, Benutzer und Rollen<br /><br /> [!INCLUDE[ssSB](../../includes/sssb-md.md)] -Warteschlangen<br /><br /> Synonyme<br /><br /> Tabellen<br /><br /> Tabellenwertfunktionen ([!INCLUDE[tsql](../../includes/tsql-md.md)] und CLR)<br /><br /> Ansichten<br /><br /> Sequenzobjekte|  
|IMPERSONATE|Anmeldungen und Benutzer|  
  
> [!CAUTION]  
>  Die Standardberechtigungen, die Systemobjekten zum Zeitpunkt der Installation erteilt wurden, werden sorgfältig bezüglich möglicher Bedrohungen ausgewertet und müssen nicht im Rahmen der Härtung der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Installation geändert werden. Alle Änderungen an den Berechtigungen für Systemobjekte können die Funktionalität einschränken oder unterbrechen und potenziell dazu führen, dass Ihre [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Installation einen nicht unterstützten Zustand aufweist.  
  
##  <a name="_permissions"></a> SQLServer und SQL Database-Berechtigungen  
 Die folgende Tabelle enthält eine vollständige Liste der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Berechtigungen. [!INCLUDE[ssSDS](../../includes/sssds-md.md)] -Berechtigungen sind nur für unterstützte sicherungsfähige Basiselemente verfügbar. Berechtigungen auf Serverebene können in [!INCLUDE[ssSDS](../../includes/sssds-md.md)]nicht gewährt werden, in einigen Fällen sind jedoch stattdessen Datenbankberechtigungen verfügbar.  
  
|Sicherungsfähiges Basiselement|Spezifische Berechtigungen für sicherungsfähiges Basiselement|Berechtigungstypcode|Sicherungsfähiges Element, das sicherungsfähiges Basiselement enthält|Berechtigung für sicherungsfähiges Containerelement mit spezifischer Berechtigung für sicherungsfähiges Basiselement|  
|--------------------|--------------------------------------------|--------------------------|--------------------------------------------|------------------------------------------------------------------------------------------|  
|APPLICATION ROLE|ALTER|AL|DATABASE|ALTER ANY APPLICATION ROLE|  
|APPLICATION ROLE|CONTROL|CL|DATABASE|CONTROL|  
|APPLICATION ROLE|VIEW DEFINITION|VW|DATABASE|VIEW DEFINITION|  
|ASSEMBLY|ALTER|AL|DATABASE|ALTER ANY ASSEMBLY|  
|ASSEMBLY|CONTROL|CL|DATABASE|CONTROL|  
|ASSEMBLY|REFERENCES|RF|DATABASE|REFERENCES|  
|ASSEMBLY|TAKE OWNERSHIP|TO|DATABASE|CONTROL|  
|ASSEMBLY|VIEW DEFINITION|VW|DATABASE|VIEW DEFINITION|  
|ASYMMETRIC KEY|ALTER|AL|DATABASE|ALTER ANY ASYMMETRIC KEY|  
|ASYMMETRIC KEY|CONTROL|CL|DATABASE|CONTROL|  
|ASYMMETRIC KEY|REFERENCES|RF|DATABASE|REFERENCES|  
|ASYMMETRIC KEY|TAKE OWNERSHIP|TO|DATABASE|CONTROL|  
|ASYMMETRIC KEY|VIEW DEFINITION|VW|DATABASE|VIEW DEFINITION|  
|AVAILABILITY GROUP|ALTER|AL|SERVER|ALTER ANY AVAILABILITY GROUP|  
|AVAILABILITY GROUP|CONTROL|CL|SERVER|CONTROL SERVER|  
|AVAILABILITY GROUP|TAKE OWNERSHIP|TO|SERVER|CONTROL SERVER|  
|AVAILABILITY GROUP|VIEW DEFINITION|VW|SERVER|VIEW ANY DEFINITION|  
|CERTIFICATE|ALTER|AL|DATABASE|ALTER ANY CERTIFICATE|  
|CERTIFICATE|CONTROL|CL|DATABASE|CONTROL|  
|CERTIFICATE|REFERENCES|RF|DATABASE|REFERENCES|  
|CERTIFICATE|TAKE OWNERSHIP|TO|DATABASE|CONTROL|  
|CERTIFICATE|VIEW DEFINITION|VW|DATABASE|VIEW DEFINITION|  
|CONTRACT|ALTER|AL|DATABASE|ALTER ANY CONTRACT|  
|CONTRACT|CONTROL|CL|DATABASE|CONTROL|  
|CONTRACT|REFERENCES|RF|DATABASE|REFERENCES|  
|CONTRACT|TAKE OWNERSHIP|TO|DATABASE|CONTROL|  
|CONTRACT|VIEW DEFINITION|VW|DATABASE|VIEW DEFINITION|  
|DATABASE|ALTER|AL|SERVER|ALTER ANY DATABASE|  
|DATABASE|ALTER ANY APPLICATION ROLE|ALAR|SERVER|CONTROL SERVER|  
|DATABASE|ALTER ANY ASSEMBLY|ALAS|SERVER|CONTROL SERVER|  
|DATABASE|ALTER ANY ASYMMETRIC KEY|ALAK|SERVER|CONTROL SERVER|  
|DATABASE|ALTER ANY CERTIFICATE|ALCF|SERVER|CONTROL SERVER|  
|DATABASE|ALTER ANY CONTRACT|ALSC|SERVER|CONTROL SERVER|  
|DATABASE|ALTER ANY DATABASE AUDIT|ALDA|SERVER|ALTER ANY SERVER AUDIT|  
|DATABASE|ALTER ANY DATABASE DDL TRIGGER|ALTG|SERVER|CONTROL SERVER|  
|DATABASE|ALTER ANY DATABASE EVENT NOTIFICATION|ALED|SERVER|ALTER ANY EVENT NOTIFICATION|  
|DATABASE|ALTER ANY DATABASE EVENT SESSION|AADS<br /><br /> Hinweis: Gilt nur für [!INCLUDE[ssSDS](../../includes/sssds-md.md)].|SERVER|ALTER ANY EVENT SESSION|  
|DATABASE|ALTER ANY DATASPACE|ALDS|SERVER|CONTROL SERVER|  
|DATABASE|ALTER ANY FULLTEXT CATALOG|ALFT|SERVER|CONTROL SERVER|  
|DATABASE|ALTER ANY MESSAGE TYPE|ALMT|SERVER|CONTROL SERVER|  
|DATABASE|ALTER ANY REMOTE SERVICE BINDING|ALSB|SERVER|CONTROL SERVER|  
|DATABASE|ALTER ANY ROLE|ALRL|SERVER|CONTROL SERVER|  
|DATABASE|ALTER ANY ROUTE|ALRT|SERVER|CONTROL SERVER|  
|DATABASE|ALTER ANY SCHEMA|ALSM|SERVER|CONTROL SERVER|  
|DATABASE|ALTER ANY SECURITY POLICY|ALSP<br /><br /> Hinweis: Gilt nur für [!INCLUDE[ssSDS](../../includes/sssds-md.md)].|SERVER|CONTROL SERVER|  
|DATABASE|ALTER ANY SERVICE|ALSV|SERVER|CONTROL SERVER|  
|DATABASE|ALTER ANY SYMMETRIC KEY|ALSK|SERVER|CONTROL SERVER|  
|DATABASE|ALTER ANY USER|ALUS|SERVER|CONTROL SERVER|  
|DATABASE|AUTHENTICATE|AUTH|SERVER|AUTHENTICATE SERVER|  
|DATABASE|BACKUP DATABASE|BADB|SERVER|CONTROL SERVER|  
|DATABASE|BACKUP LOG|BALO|SERVER|CONTROL SERVER|  
|DATABASE|CHECKPOINT|CP|SERVER|CONTROL SERVER|  
|DATABASE|CONNECT|CO|SERVER|CONTROL SERVER|  
|DATABASE|CONNECT REPLICATION|CORP|SERVER|CONTROL SERVER|  
|DATABASE|CONTROL|CL|SERVER|CONTROL SERVER|  
|DATABASE|CREATE AGGREGATE|CRAG|SERVER|CONTROL SERVER|  
|DATABASE|CREATE ASSEMBLY|CRAS|SERVER|CONTROL SERVER|  
|DATABASE|CREATE ASYMMETRIC KEY|CRAK|SERVER|CONTROL SERVER|  
|DATABASE|CREATE CERTIFICATE|CRCF|SERVER|CONTROL SERVER|  
|DATABASE|CREATE CONTRACT|CRSC|SERVER|CONTROL SERVER|  
|DATABASE|CREATE DATABASE|CRDB|SERVER|CREATE ANY DATABASE|  
|DATABASE|CREATE DATABASE DDL EVENT NOTIFICATION|CRED|SERVER|CREATE DDL EVENT NOTIFICATION|  
|DATABASE|CREATE DEFAULT|CRDF|SERVER|CONTROL SERVER|  
|DATABASE|CREATE FULLTEXT CATALOG|CRFT|SERVER|CONTROL SERVER|  
|DATABASE|CREATE FUNCTION|CRFN|SERVER|CONTROL SERVER|  
|DATABASE|CREATE MESSAGE TYPE|CRMT|SERVER|CONTROL SERVER|  
|DATABASE|CREATE PROCEDURE|CRPR|SERVER|CONTROL SERVER|  
|DATABASE|CREATE QUEUE|CRQU|SERVER|CONTROL SERVER|  
|DATABASE|CREATE REMOTE SERVICE BINDING|CRSB|SERVER|CONTROL SERVER|  
|DATABASE|CREATE ROLE|CRRL|SERVER|CONTROL SERVER|  
|DATABASE|CREATE ROUTE|CRRT|SERVER|CONTROL SERVER|  
|DATABASE|CREATE RULE|CRRU|SERVER|CONTROL SERVER|  
|DATABASE|CREATE SCHEMA|CRSM|SERVER|CONTROL SERVER|  
|DATABASE|CREATE SERVICE|CRSV|SERVER|CONTROL SERVER|  
|DATABASE|CREATE SYMMETRIC KEY|CRSK|SERVER|CONTROL SERVER|  
|DATABASE|CREATE SYNONYM|CRSN|SERVER|CONTROL SERVER|  
|DATABASE|CREATE TABLE|CRTB|SERVER|CONTROL SERVER|  
|DATABASE|CREATE TYPE|CRTY|SERVER|CONTROL SERVER|  
|DATABASE|CREATE VIEW|CRVW|SERVER|CONTROL SERVER|  
|DATABASE|CREATE XML SCHEMA COLLECTION|CRXS|SERVER|CONTROL SERVER|  
|DATABASE|DELETE|DL|SERVER|CONTROL SERVER|  
|DATABASE|Führen Sie|EX|SERVER|CONTROL SERVER|  
|DATABASE|INSERT|IN|SERVER|CONTROL SERVER|  
|DATABASE|KILL DATABASE CONNECTION|KIDC<br /><br /> Hinweis: Gilt nur für [!INCLUDE[ssSDS](../../includes/sssds-md.md)]. Verwenden Sie ALTER ANY CONNECTION in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].|SERVER|ALTER ANY CONNECTION|  
|DATABASE|REFERENCES|RF|SERVER|CONTROL SERVER|  
|DATABASE|SELECT|SL|SERVER|CONTROL SERVER|  
|DATABASE|SHOWPLAN|SPLN|SERVER|ALTER TRACE|  
|DATABASE|SUBSCRIBE QUERY NOTIFICATIONS|SUQN|SERVER|CONTROL SERVER|  
|DATABASE|TAKE OWNERSHIP|TO|SERVER|CONTROL SERVER|  
|DATABASE|UPDATE|UP|SERVER|CONTROL SERVER|  
|DATABASE|VIEW DATABASE STATE|VWDS|SERVER|VIEW SERVER STATE|  
|DATABASE|VIEW DEFINITION|VW|SERVER|VIEW ANY DEFINITION|  
|ENDPOINT|ALTER|AL|SERVER|ALTER ANY ENDPOINT|  
|ENDPOINT|CONNECT|CO|SERVER|CONTROL SERVER|  
|ENDPOINT|CONTROL|CL|SERVER|CONTROL SERVER|  
|ENDPOINT|TAKE OWNERSHIP|TO|SERVER|CONTROL SERVER|  
|ENDPOINT|VIEW DEFINITION|VW|SERVER|VIEW ANY DEFINITION|  
|FULLTEXT CATALOG|ALTER|AL|DATABASE|ALTER ANY FULLTEXT CATALOG|  
|FULLTEXT CATALOG|CONTROL|CL|DATABASE|CONTROL|  
|FULLTEXT CATALOG|REFERENCES|RF|DATABASE|REFERENCES|  
|FULLTEXT CATALOG|TAKE OWNERSHIP|TO|DATABASE|CONTROL|  
|FULLTEXT CATALOG|VIEW DEFINITION|VW|DATABASE|VIEW DEFINITION|  
|FULLTEXT STOPLIST|ALTER|AL|DATABASE|ALTER ANY FULLTEXT CATALOG|  
|FULLTEXT STOPLIST|CONTROL|CL|DATABASE|CONTROL|  
|FULLTEXT STOPLIST|REFERENCES|RF|DATABASE|REFERENCES|  
|FULLTEXT STOPLIST|TAKE OWNERSHIP|TO|DATABASE|CONTROL|  
|FULLTEXT STOPLIST|VIEW DEFINITION|VW|DATABASE|VIEW DEFINITION|  
|Anmeldung|ALTER|AL|SERVER|ALTER ANY LOGIN|  
|Anmeldung|CONTROL|CL|SERVER|CONTROL SERVER|  
|Anmeldung|IMPERSONATE|IM|SERVER|CONTROL SERVER|  
|Anmeldung|VIEW DEFINITION|VW|SERVER|VIEW ANY DEFINITION|  
|MESSAGE TYPE|ALTER|AL|DATABASE|ALTER ANY MESSAGE TYPE|  
|MESSAGE TYPE|CONTROL|CL|DATABASE|CONTROL|  
|MESSAGE TYPE|REFERENCES|RF|DATABASE|REFERENCES|  
|MESSAGE TYPE|TAKE OWNERSHIP|TO|DATABASE|CONTROL|  
|MESSAGE TYPE|VIEW DEFINITION|VW|DATABASE|VIEW DEFINITION|  
|OBJECT|ALTER|AL|SCHEMA|ALTER|  
|OBJECT|CONTROL|CL|SCHEMA|CONTROL|  
|OBJECT|DELETE|DL|SCHEMA|DELETE|  
|OBJECT|Führen Sie|EX|SCHEMA|Führen Sie|  
|OBJECT|INSERT|IN|SCHEMA|INSERT|  
|OBJECT|RECEIVE|RC|SCHEMA|CONTROL|  
|OBJECT|REFERENCES|RF|SCHEMA|REFERENCES|  
|OBJECT|SELECT|SL|SCHEMA|SELECT|  
|OBJECT|TAKE OWNERSHIP|TO|SCHEMA|CONTROL|  
|OBJECT|UPDATE|UP|SCHEMA|UPDATE|  
|OBJECT|VIEW CHANGE TRACKING|VWCT|SCHEMA|VIEW CHANGE TRACKING|  
|OBJECT|VIEW DEFINITION|VW|SCHEMA|VIEW DEFINITION|  
|REMOTE SERVICE BINDING|ALTER|AL|DATABASE|ALTER ANY REMOTE SERVICE BINDING|  
|REMOTE SERVICE BINDING|CONTROL|CL|DATABASE|CONTROL|  
|REMOTE SERVICE BINDING|TAKE OWNERSHIP|TO|DATABASE|CONTROL|  
|REMOTE SERVICE BINDING|VIEW DEFINITION|VW|DATABASE|VIEW DEFINITION|  
|ROLE|ALTER|AL|DATABASE|ALTER ANY ROLE|  
|ROLE|CONTROL|CL|DATABASE|CONTROL|  
|ROLE|TAKE OWNERSHIP|TO|DATABASE|CONTROL|  
|ROLE|VIEW DEFINITION|VW|DATABASE|VIEW DEFINITION|  
|ROUTE|ALTER|AL|DATABASE|ALTER ANY ROUTE|  
|ROUTE|CONTROL|CL|DATABASE|CONTROL|  
|ROUTE|TAKE OWNERSHIP|TO|DATABASE|CONTROL|  
|ROUTE|VIEW DEFINITION|VW|DATABASE|VIEW DEFINITION|  
|SEARCH PROPERTY LIST|ALTER|AL|SERVER|ALTER ANY FULLTEXT CATALOG|  
|SEARCH PROPERTY LIST|CONTROL|CL|SERVER|CONTROL|  
|SEARCH PROPERTY LIST|REFERENCES|RF|SERVER|REFERENCES|  
|SEARCH PROPERTY LIST|TAKE OWNERSHIP|TO|SERVER|CONTROL|  
|SEARCH PROPERTY LIST|VIEW DEFINITION|VW|SERVER|VIEW DEFINITION|  
|SCHEMA|ALTER|AL|DATABASE|ALTER ANY SCHEMA|  
|SCHEMA|CONTROL|CL|DATABASE|CONTROL|  
|SCHEMA|CREATE SEQUENCE|CRSO|DATABASE|CONTROL|  
|SCHEMA|DELETE|DL|DATABASE|DELETE|  
|SCHEMA|Führen Sie|EX|DATABASE|Führen Sie|  
|SCHEMA|INSERT|IN|DATABASE|INSERT|  
|SCHEMA|REFERENCES|RF|DATABASE|REFERENCES|  
|SCHEMA|SELECT|SL|DATABASE|SELECT|  
|SCHEMA|TAKE OWNERSHIP|TO|DATABASE|CONTROL|  
|SCHEMA|UPDATE|UP|DATABASE|UPDATE|  
|SCHEMA|VIEW CHANGE TRACKING|VWCT|DATABASE|VIEW CHANGE TRACKING|  
|SCHEMA|VIEW DEFINITION|VW|DATABASE|VIEW DEFINITION|  
|SERVER|ADMINISTER BULK OPERATIONS|ADBO|Nicht verfügbar|Nicht verfügbar|  
|SERVER|ALTER ANY CONNECTION|ALCO|Nicht verfügbar|Nicht verfügbar|  
|SERVER|ALTER ANY CREDENTIAL|ALCD|Nicht verfügbar|Nicht verfügbar|  
|SERVER|ALTER ANY DATABASE|ALDB|Nicht verfügbar|Nicht verfügbar|  
|SERVER|ALTER ANY ENDPOINT|ALHE|Nicht verfügbar|Nicht verfügbar|  
|SERVER|ALTER ANY EVENT NOTIFICATION|ALES|Nicht verfügbar|Nicht verfügbar|  
|SERVER|ALTER ANY EVENT SESSION|AAES|Nicht verfügbar|Nicht verfügbar|  
|SERVER|ALTER ANY LINKED SERVER|ALLS|Nicht verfügbar|Nicht verfügbar|  
|SERVER|ALTER ANY LOGIN|ALLG|Nicht verfügbar|Nicht verfügbar|  
|SERVER|ALTER ANY SERVER AUDIT|ALAA|Nicht verfügbar|Nicht verfügbar|  
|SERVER|ALTER ANY SERVER ROLE|ALSR|Nicht verfügbar|Nicht verfügbar|  
|SERVER|ALTER AVAILABILITY GROUP|ALAG|Nicht verfügbar|Nicht verfügbar|  
|SERVER|ALTER RESOURCES|ALRS|Nicht verfügbar|Nicht verfügbar|  
|SERVER|ALTER SERVER STATE|ALSS|Nicht verfügbar|Nicht verfügbar|  
|SERVER|ALTER SETTINGS|ALST|Nicht verfügbar|Nicht verfügbar|  
|SERVER|ALTER TRACE|ALTR|Nicht verfügbar|Nicht verfügbar|  
|SERVER|AUTHENTICATE SERVER|AUTH|Nicht verfügbar|Nicht verfügbar|  
|SERVER|CONNECT ANY DATABASE|CADB|Nicht verfügbar|Nicht verfügbar|  
|SERVER|CONNECT SQL|COSQ|Nicht verfügbar|Nicht verfügbar|  
|SERVER|CONTROL SERVER|CL|Nicht verfügbar|Nicht verfügbar|  
|SERVER|CREATE ANY DATABASE|CRDB|Nicht verfügbar|Nicht verfügbar|  
|SERVER|CREATE AVAILABILTITY GROUP|CRAC|Nicht verfügbar|Nicht verfügbar|  
|SERVER|CREATE DDL EVENT NOTIFICATION|CRDE|Nicht verfügbar|Nicht verfügbar|  
|SERVER|CREATE ENDPOINT|CRHE|Nicht verfügbar|Nicht verfügbar|  
|SERVER|CREATE SERVER ROLE|CRSR|Nicht verfügbar|Nicht verfügbar|  
|SERVER|CREATE TRACE EVENT NOTIFICATION|CRTE|Nicht verfügbar|Nicht verfügbar|  
|SERVER|EXTERNAL ACCESS ASSEMBLY|XA|Nicht verfügbar|Nicht verfügbar|  
|SERVER|IMPERSONATE ANY LOGIN|IAL|Nicht verfügbar|Nicht verfügbar|  
|SERVER|SELECT ALL USER SECURABLES|SUS|Nicht verfügbar|Nicht verfügbar|  
|SERVER|SHUTDOWN|SHDN|Nicht verfügbar|Nicht verfügbar|  
|SERVER|UNSAFE ASSEMBLY|XU|Nicht verfügbar|Nicht verfügbar|  
|SERVER|VIEW ANY DATABASE|VWDB|Nicht verfügbar|Nicht verfügbar|  
|SERVER|VIEW ANY DEFINITION|VWAD|Nicht verfügbar|Nicht verfügbar|  
|SERVER|VIEW SERVER STATE|VWSS|Nicht verfügbar|Nicht verfügbar|  
|SERVER ROLE|ALTER|AL|SERVER|ALTER ANY SERVER ROLE|  
|SERVER ROLE|CONTROL|CL|SERVER|CONTROL SERVER|  
|SERVER ROLE|TAKE OWNERSHIP|TO|SERVER|CONTROL SERVER|  
|SERVER ROLE|VIEW DEFINITION|VW|SERVER|VIEW ANY DEFINITION|  
|SERVICE|ALTER|AL|DATABASE|ALTER ANY SERVICE|  
|SERVICE|CONTROL|CL|DATABASE|CONTROL|  
|SERVICE|SEND|SN|DATABASE|CONTROL|  
|SERVICE|TAKE OWNERSHIP|TO|DATABASE|CONTROL|  
|SERVICE|VIEW DEFINITION|VW|DATABASE|VIEW DEFINITION|  
|SYMMETRIC KEY|ALTER|AL|DATABASE|ALTER ANY SYMMETRIC KEY|  
|SYMMETRIC KEY|CONTROL|CL|DATABASE|CONTROL|  
|SYMMETRIC KEY|REFERENCES|RF|DATABASE|REFERENCES|  
|SYMMETRIC KEY|TAKE OWNERSHIP|TO|DATABASE|CONTROL|  
|SYMMETRIC KEY|VIEW DEFINITION|VW|DATABASE|VIEW DEFINITION|  
|TYPE|CONTROL|CL|SCHEMA|CONTROL|  
|TYPE|Führen Sie|EX|SCHEMA|Führen Sie|  
|TYPE|REFERENCES|RF|SCHEMA|REFERENCES|  
|TYPE|TAKE OWNERSHIP|TO|SCHEMA|CONTROL|  
|TYPE|VIEW DEFINITION|VW|SCHEMA|VIEW DEFINITION|  
|Benutzer|ALTER|AL|DATABASE|ALTER ANY USER|  
|Benutzer|CONTROL|CL|DATABASE|CONTROL|  
|Benutzer|IMPERSONATE|IM|DATABASE|CONTROL|  
|Benutzer|VIEW DEFINITION|VW|DATABASE|VIEW DEFINITION|  
|XML SCHEMA COLLECTION|ALTER|AL|SCHEMA|ALTER|  
|XML SCHEMA COLLECTION|CONTROL|CL|SCHEMA|CONTROL|  
|XML SCHEMA COLLECTION|Führen Sie|EX|SCHEMA|Führen Sie|  
|XML SCHEMA COLLECTION|REFERENCES|RF|SCHEMA|REFERENCES|  
|XML SCHEMA COLLECTION|TAKE OWNERSHIP|TO|SCHEMA|CONTROL|  
|XML SCHEMA COLLECTION|VIEW DEFINITION|VW|SCHEMA|VIEW DEFINITION|  
  
##  <a name="_algorithm"></a> Zusammenfassung des Algorithmus zur Berechtigungsprüfung  
 Die Prüfung von Berechtigungen kann sehr komplex sein. Der Algorithmus für die Berechtigungsprüfung umfasst überlappende Gruppenmitgliedschaften und Besitzverkettung, explizite und implizite Berechtigungen und kann von den Berechtigungen für sicherungsfähige Klassen, in denen die sicherungsfähige Entität enthalten ist, beeinflusst werden. Die allgemeine Vorgehensweise des Algorithmus besteht darin, alle relevanten Berechtigungen zu sammeln. Wenn keine blockierende DENY-Anweisung gefunden wird, sucht der Algorithmus nach einer GRANT-Anweisung mit ausreichenden Zugriffsberechtigungen. Der Algorithmus enthält drei wesentliche Elemente, den **Sicherheitskontext**, den **Berechtigungsbereich**und die **erforderliche Berechtigung**.  
  
> [!NOTE]  
>  Berechtigungen können nicht für sa, dbo, den Entitätsbesitzer, information_schema, sys oder für den Benutzer selbst erteilt, verweigert oder aufgehoben werden.  
  
-   **Sicherheitskontext**  
  
     Dies ist die Gruppe von Prinzipalen, die Berechtigungen für die Zugriffsüberprüfung einbringen. Diese Berechtigungen beziehen sich auf den aktuellen Anmeldenamen oder Benutzer, es sei denn, der Sicherheitskontext wurde mithilfe der EXECUTE AS-Anweisung in einen anderen Anmeldenamen oder Benutzer geändert. Der Sicherheitskontext schließt die folgenden Prinzipale ein:  
  
    -   Anmeldenamen  
  
    -   Benutzer  
  
    -   Rollenmitgliedschaften  
  
    -   Windows-Gruppenmitgliedschaften  
  
    -   Bei Verwendung der Modulsignierung sind dies ein beliebiger Anmeldename oder ein beliebiges Benutzerkonto für das Zertifikat, das zum Signieren des vom Benutzer derzeit ausgeführten Moduls verwendet wird, und die zugehörigen Rollenmitgliedschaften dieses Prinzipals.  
  
-   **Berechtigungsbereich**  
  
     Dies sind die sicherungsfähige Entität und alle sicherungsfähigen Klassen, in denen das sicherungsfähige Element enthalten ist. Eine Tabelle (eine sicherungsfähige Entität) ist z. B. in der sicherungsfähigen Klasse des Schemas und in der sicherungsfähigen Klasse der Datenbank enthalten. Berechtigungen auf Tabellen-, Schema-, Datenbank- und Serverebene können sich auf den Zugriff auswirken. Weitere Informationen finden Sie unter [Berechtigungshierarchie &amp;#40;Datenbank-Engine&amp;#41;](permissions-hierarchy-database-engine.md).  
  
-   **Erforderliche Berechtigung**  
  
     Die Art der erforderlichen Berechtigung. Beispielsweise INSERT, UPDATE, DELETE, SELECT, EXECUTE, ALTER, CONTROL usw.  
  
     Für den Zugriff können wie in den folgenden Beispielen mehrere Berechtigungen erforderlich sein:  
  
    -   Eine gespeicherte Prozedur kann sowohl die EXECUTE-Berechtigung für die gespeicherte Prozedur als auch die INSERT-Berechtigung für mehrere Tabellen erfordern, auf die von der gespeicherten Prozedur verwiesen wird.  
  
    -   Eine dynamische Verwaltungssicht kann sowohl die VIEW SERVER STATE-Berechtigung als auch SELECT-Berechtigung für die Sicht erfordern.  
  
### <a name="general-steps-of-the-algorithm"></a>Allgemeine Schritte des Algorithmus  
 Wenn der Algorithmus ermittelt, ob Zugriff auf das sicherungsfähige Element erteilt werden soll, können die in diesem Zusammenhang ausgeführten Schritte sehr unterschiedlich sein. Dies hängt von den jeweiligen Prinzipalen und sicherungsfähigen Elementen ab. Der Algorithmus führt jedoch die folgenden allgemeinen Schritte aus:  
  
1.  Umgehen der Berechtigungsprüfung, wenn der Anmeldename ein Mitglied der festen Serverrolle sysadmin oder der Benutzer der dbo-Benutzer der aktuellen Datenbank ist.  
  
2.  Erteilen des Zugriffs, wenn die Besitzverkettung anwendbar ist und die Zugriffsprüfung für das Objekt an früherer Stelle in der Kette die Sicherheitsprüfung erfolgreich war.  
  
3.  Aggregieren der Identitäten, die dem Aufrufer zum Erstellen des **Sicherheitskontexts**zugeordnet sind, auf Server- und Datenbankebene sowie auf Ebene des signierten Moduls.  
  
4.  Sammeln aller Berechtigungen, die für diesen **Berechtigungsbereich**erteilt oder verweigert wurden, in diesem **Sicherheitskontext**. Die Berechtigung kann explizit als GRANT, GRANT WITH GRANT oder DENY angegeben werden; oder die Berechtigungen können als implizite oder abdeckende GRANT-Berechtigung oder DENY-Berechtigung angegeben werden. Die CONTROL-Berechtigung für ein Schema impliziert z. B. CONTROL für eine Tabelle. CONTROL für eine Tabelle impliziert SELECT. Wenn CONTROL für das Schema erteilt wurde, wird folglich SELECT für die Tabelle erteilt. Wenn CONTROL für die Tabelle verweigert wurde, wird SELECT für die Tabelle verweigert.  
  
    > [!NOTE]  
    >  Durch eine GRANT-Berechtigung auf Spaltenebene wird eine DENY-Berechtigung auf Objektebene überschrieben.  
  
5.  Identifizieren Sie die **erforderliche Berechtigung**.  
  
6.  Die Berechtigungsprüfung ist nicht bestanden, wenn die **erforderlichen Berechtigung** für eine der Identitäten im **Sicherheitskontext** der Objekte im **Berechtigungsbereich** direkt oder implizit verweigert werden.  
  
7.  Die Berechtigungsprüfung ist bestanden, wenn die **erforderlichen Berechtigung** nicht verweigert wurde, und die **erforderlichen Berechtigung** für eine der Identitäten im **Sicherheitskontext** eines beliebigen Objekts im **Berechtigungsbereich**direkt oder implizit eine GRANT-Berechtigung oder GRANT WITH GRANT-Berechtigung enthält.  
  
##  <a name="_examples"></a> Beispiele  
 In den Beispielen dieses Abschnitts wird veranschaulicht, wie Berechtigungsinformationen abgerufen werden.  
  
### <a name="a-returning-the-complete-list-of-grantable-permissions"></a>A. Zurückgeben der vollständigen Liste erteilbarer Berechtigungen  
 Die folgende Anweisung gibt mithilfe der [!INCLUDE[ssDE](../../includes/ssde-md.md)] -Funktion alle `fn_builtin_permissions` -Berechtigungen zurück. Weitere Informationen finden Sie unter [sys.fn_builtin_permissions &#40;Transact-SQL&#41;](/sql/relational-databases/system-functions/sys-fn-builtin-permissions-transact-sql).  
  
```  
SELECT * FROM fn_builtin_permissions(default);  
GO  
```  
  
### <a name="b-returning-the-permissions-on-a-particular-class-of-objects"></a>B. Zurückgeben der Berechtigungen für eine bestimmte Objektklasse  
 Im folgenden Beispiel wird `fn_builtin_permissions` verwendet, um alle Berechtigungen anzuzeigen, die für eine Kategorie des sicherungsfähigen Elements verfügbar sind. Im Beispiel werden Berechtigungen für Assemblys zurückgegeben.  
  
```  
SELECT * FROM fn_builtin_permissions('assembly');  
GO    
```  
  
### <a name="c-returning-the-permissions-granted-to-the-executing-principal-on-an-object"></a>C. Zurückgeben der Berechtigungen, die dem ausführenden Prinzipal für ein Objekt erteilt wurden  
 Im folgenden Beispiel wird mithilfe von `fn_my_permissions` eine Liste der effektiven Berechtigungen zurückgegeben, die vom aufrufenden Prinzipal für ein bestimmtes sicherungsfähiges Element gespeichert werden. Im Beispiel werden Berechtigungen für ein Objekt mit dem Namen `Orders55` zurückgegeben. Weitere Informationen finden Sie unter [sys.fn_my_permissions &#40;Transact-SQL&#41;](/sql/relational-databases/system-functions/sys-fn-my-permissions-transact-sql).  
  
```  
SELECT * FROM fn_my_permissions('Orders55', 'object');  
GO  
```  
  
### <a name="d-returning-the-permissions-applicable-to-a-specified-object"></a>D. Zurückgeben von Berechtigungen, die auf ein angegebenes Objekt angewendet werden können  
 Im folgenden Beispiel werden Berechtigungen für ein Objekt namens `Yttrium`zurückgegeben. Beachten Sie, dass die integrierte `OBJECT_ID` -Funktion zum Abrufen der ID des `Yttrium`-Objekts verwendet wird.  
  
```  
SELECT * FROM sys.database_permissions   
    WHERE major_id = OBJECT_ID('Yttrium');  
GO  
```  
  
## <a name="see-also"></a>Siehe auch  
 [Berechtigungshierarchie &amp;amp;#40;Datenbank-Engine &amp;amp;#41;](permissions-hierarchy-database-engine.md)   
 [sys.database_permissions &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-database-permissions-transact-sql)  
  
  
