# Migrating to Azure SQL Database Managed Instance

Alpine Ski House (ASH) is leading manufacturer of skis, snowboards, and alpine apparel, serving a global customer-base. Since launching their online retail store 8 years ago, and their growth has quickly outpaced their ability to scale their database to meet their online sales needs. They are looking for a proof-of-concept (PoC) of a solution that enables them to migrate their on-premises web application and SQL Server 2012 database to fully-managed PaaS services in Azure.

ASH is using the Service Broker feature of SQL Server within their database. Service Broker is a feature of SQL Server used for sending and receiving guaranteed, asynchronous messages by using extensions to the Transact-SQL Data Manipulation Language (DML). This functionality is being used for several critical business processes, and they cannot afford to lose this capability when migrating their operations database to the cloud. They have also stated that, at this time, they do not have the resources to rearchitect the solution to use an alternative message broker.

In addition, they have read about some of the advanced security and performance tuning options that are available only in Azure and are interested in understanding how they can leverage these features. Due to their rapid growth, and limited database resources as they grew, they have a heavy reporting workload on their online transaction processing database. They are very interested in learning if there are any options to move this reporting workload off their primary server, but don't have the time or resources to make any architectural changes to the database or application at this time.

## Target audience

- Database Administrators
- Application Developers
- SQL/Database Developers

## Abstract

### Workshop

In this workshop, you will learn to develop a plan for migrating an on-premises web application and SQL Server 2012 database into PaaS services in Azure. You will perform assessments to reveal any feature parity and compatibility issues between the customer's SQL Server 2012 database and the managed database offerings in Azure. You will then provide a solution to migration the web application and database into Azure services, with zero down-time. You will then enable some of the advanced SQL features available in Azure to improve security and performance in the customer's application.

At the end of this workshop, you will be better able to design and implement a cloud migration solution for applications and database that cannot experience downtime, and with features that are incompatible with Azure SQL Database.

#### Outline: Key concerns for customer situation

- They cannot afford to experience down time during their cloud migration. Is it possible for their application and database remain online during a migration to the cloud?
- With a migration to the cloud, they are looking for a solution that offers build-in high availability and high performance.
- They are using Service broker in the SQL Server 2012 database, and have heard that feature is not supported in Azure SQL Database.
  - Are there any options outside of migrating to a VM for hosting the database in Azure?
  - Are there any tools that can help them better understand any feature parity and compatibility issues they might not be aware that could prevent them from migrating to a managed database service in Azure?
- In their current system, they run a lot of reports directly from the application database. Is there any way that can alleviate the performance impacts on the system, without having to completely re-architect the application and database?
- They do not have a dedicated DBA, so they know there are security features available that they have not had a chance to turn on. They are interested in learning more about any advanced SQL features that could help improve their security posture.
- ASH has a global customer base, and must meet GDPR requirements. They are interested in learning about any tools that might help them to better understand their database, and the data it contains, and any compliance-related policies that may apply to the data.

### Whiteboard design session

In this whiteboard design session, you will work in a group to develop a plan for migrating an on-premises web application and SQL Server 2012 database into PaaS services in Azure. You will provide guidance on performing assessments to reveal any feature parity and compatibility issues between the customer's SQL Server 2012 database and the managed database offerings in Azure. You will then provide a solution to migration the web application and database into Azure services, with zero down-time. You will also provide guidance on how to enable some of the advanced SQL features available in Azure to improve security and performance in the customer's application.

At the end of this workshop, you will be better able to design a cloud migration solution for applications and database that cannot experience downtime, and with features that are incompatible with Azure SQL Database.

### Hands-on lab

In this hands-on lab, you will implement a proof-of-concept (PoC) for migrating an on-premises web application and SQL Server 2012 database into PaaS services in Azure. You will perform assessments to reveal any feature parity and compatibility issues between the customer's SQL Server 2012 database and the managed database offerings in Azure. You will then migrate the web application and database into Azure services, with zero down-time. Once the application and database are migrated, you will enable some of the advanced SQL features available in Azure to improve security and performance in the customer's application.

At the end of this workshop, you will be better able to implement a cloud migration solution for applications and database that cannot experience downtime, and with features that are incompatible with Azure SQL Database.

#### Outline: Hands-on lab exercises

- Before the hands-on lab
  - Task 1: Provision SQL MI
  - Task 2: Provision Lab VM in same VNet as SQL MI
  - Task 3: Configure Lab VM
    - Install SSMS
    - Download and install Data Migration Assistant (DMA)
  - Task 4: Provision SQL Server 2012 on Windows Server 2016 VM
    - Open firewall for port 1433 on server and in the Azure portal
    - Restore database onto server
    - Enable Service Broker on the database
    - Reset `sa` password
  - Task 5: Create App Service (Web App) in Azure portal
    - Configure network connection to SQL MI VNet Gateway subnet
  - Task 6: Provision Azure Database Migration Assistant in the Azure portal
- Exercise 1: Deploy web app
  - Task 1: Deploy web app to App Service
  - Task 2: Configure connection string to point to SQL 2012 database
- Exercise 2: Perform assessments on SQL 2012 database
  - Task 1: Perform assessment using DMA against Azure SQL Database
  - Task 2: Perform assessment using DMA against Azure SQL Database Managed Instance
- Exercise 3: Migrate the database to SQL MI using DMS
  - Task 1: Set up DMS project for online migration
  - Task 2: Enable transactional replication to allow online migration
- Exercise 4: Update application to point to SQL MI database
  - Task 1: Update the application settings connection string
  - Task 2: Connect your app to SQL MI.
    - Create a gateway subnet in your SQL MI VNet.
    - Create a VPN gateway.
    - Set the point to site addresses.
    - Configure VNet integration with the App Service.
  - Task 3: Launch the app
- Exercise 5: Enable Advanced Data Security.
  - Review Vulnerability Assessment.
  - Enable Transparent Data Encryption.
- Exercise 6: Enable SQL Data Discovery and Classification feature in SSMS
- Exercise 7: Enable Dynamic Data Masking
  - Task 1: Review database tables, and sensitive values being displayed in clear text.
  - Task 2: Apply masks to fields in tables (Credit card numbers, email address, etc.) Demonstrate various functions for adding masks using DDM.
- Exercise 8: Use online secondary for read-only queries.
  - Task 1: Create read-only connection string in web application code
  - Task 2: Add read-only connection string to Web App application settings, using `ApplicationIntent=ReadOnly` settings in connection string.
  - Task 3: Simulate heavy transactional load on the primary SQL MI database
  - Task 4: Demonstrate how read-only replica can be accessed for reporting with minimal impact on the primary instance

## Azure services and related products

- Azure SQL Database Managed Instance
- Azure SQL Database
- Azure Database Migration Service
- Microsoft Data Migration Assistant
- Azure App Service
- SQL Server Management Studio
- SQL Server

## Azure solutions

*This is an internal reference and will be updated by project PM.*

## Related references

*This should be a list of links to prerequisites, architectural diagrams, supporting docs, or briefing decks related to the material.*

- [MCW](https://github.com/Microsoft/MCW)