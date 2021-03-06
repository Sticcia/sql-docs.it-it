---
title: Accedere ad archivi dati e condivisioni file con l'autenticazione di Windows | Microsoft Docs
description: Informazioni su come configurare il catalogo SSIS nel database SQL di Azure e in Azure-SSIS Integration Runtime in Azure Data Factory per eseguire pacchetti che usano l'autenticazione di Windows per accedere ad archivi dati e condivisioni file.
ms.date: 3/22/2018
ms.topic: conceptual
ms.prod: sql
ms.prod_service: integration-services
ms.custom: ''
ms.technology: integration-services
author: swinarko
ms.author: sawinark
ms.reviewer: douglasl
manager: craigg
ms.openlocfilehash: 94002a79d53c008249836541fc84f7e9ff06a6ae
ms.sourcegitcommit: fd71d04a9d30a9927cbfff645750ac9d5d5e5ee7
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/16/2019
ms.locfileid: "65720728"
---
# <a name="access-data-stores-and-file-shares-with-windows-authentication-from-ssis-packages-in-azure"></a>Accedere ad archivi dati e condivisioni file con l'autenticazione di Windows da pacchetti SSIS in Azure

[!INCLUDE[ssis-appliesto](../../includes/ssis-appliesto-ssvrpluslinux-asdb-asdw-xxx.md)]


È possibile usare l'autenticazione di Windows per accedere ad archivi dati, ad esempio SQL Server, condivisioni file, File di Azure e così via da pacchetti SSIS eseguiti in Azure-SSIS Integration Runtime in Azure Data Factory. Gli archivi dati possono essere locali, ospitati in macchine virtuali di Azure o in esecuzione in Azure come servizi gestiti. Se sono in locale, è necessario aggiungere Azure-SSIS Integration Runtime a una rete virtuale (VNet) connessa alla rete locale. Vedere [Aggiungere Azure-SSIS Integration Runtime a una rete virtuale](https://docs.microsoft.com/azure/data-factory/join-azure-ssis-integration-runtime-virtual-network). Sono disponibili quattro metodi per accedere ad archivi dati con l'autenticazione di Windows da pacchetti SSIS in esecuzione in Azure-SSIS Integration Runtime:

| Metodo di connessione | Ambito effettivo | Passaggio di configurazione | Metodo di accesso nei pacchetti | Numero di set di credenziali e risorse connesse | Tipo di risorse connesse | 
|---|---|---|---|---|---|
| Configurazione di un contesto di esecuzione a livello di attività | Attività Esegui pacchetto SSIS | Configurare la proprietà **Autenticazione di Windows** per impostare un contesto di "Esecuzione/Esegui come" durante l'esecuzione di pacchetti SSIS come attività Esegui pacchetto SSIS nelle pipeline di Azure Data Factory.<br/><br/> Per altre informazioni, vedere [Eseguire un pacchetto SSIS tramite l'attività Esegui pacchetto SSIS in Azure Data Factory](https://docs.microsoft.com/azure/data-factory/how-to-invoke-ssis-package-ssis-activity). | Accedere alle risorse direttamente nei pacchetti tramite un percorso UNC, ad esempio, se si usano condivisioni file o File di Azure: `\\YourFileShareServerName\YourFolderName` o `\\YourAzureStorageAccountName.file.core.windows.net\YourFolderName` | È supportato un solo set di credenziali per tutte le risorse connesse | - Condivisioni file in macchine virtuali locali/di Azure<br/><br/> - File di Azure, vedere [Montare una condivisione file di Azure](https://docs.microsoft.com/azure/storage/files/storage-how-to-use-files-windows) <br/><br/> - SQL Server in macchine virtuali locali/di Azure con l'autenticazione di Windows<br/><br/> - Altre risorse con l'autenticazione di Windows |
| Configurazione di un contesto di esecuzione a livello di catalogo | Azure-SSIS IR, ma verrà eseguito l'override quando si configura anche un contesto di esecuzione a livello di attività (vedere sopra) | Eseguire la stored procedure SSISDB `catalog.set_execution_credential` per configurare un contesto di "Esecuzione/Esegui come".<br/><br/> Per altre informazioni, vedere il resto di questo articolo. | Accedere alle risorse direttamente nei pacchetti tramite un percorso UNC, ad esempio, se si usano condivisioni file o File di Azure: `\\YourFileShareServerName\YourFolderName` o `\\YourAzureStorageAccountName.file.core.windows.net\YourFolderName` | È supportato un solo set di credenziali per tutte le risorse connesse | - Condivisioni file in macchine virtuali locali/di Azure<br/><br/> - File di Azure, vedere [Montare una condivisione file di Azure](https://docs.microsoft.com/azure/storage/files/storage-how-to-use-files-windows) <br/><br/> - SQL Server in macchine virtuali locali/di Azure con l'autenticazione di Windows<br/><br/> - Altre risorse con l'autenticazione di Windows |
| Rendere persistenti le credenziali tramite il comando `cmdkey` | Azure-SSIS IR, ma verrà eseguito l'override quando si configura anche un contesto di esecuzione a livello di attività/catalogo (vedere sopra) | Eseguire il comando `cmdkey` in uno script di installazione personalizzato (`main.cmd`) durante il provisioning o la riconfigurazione di Azure-SSIS IR, ad esempio se si usano condivisioni file o File di Azure: `cmdkey /add:YourFileShareServerName /user:YourDomainName\YourUsername /pass:YourPassword` o `cmdkey /add:YourAzureStorageAccountName.file.core.windows.net /user:azure\YourAzureStorageAccountName /pass:YourAccessKey`.<br/><br/> Per altre informazioni, vedere [Customize setup for Azure-SSIS IR](https://docs.microsoft.com/azure/data-factory/how-to-configure-azure-ssis-ir-custom-setup) (Personalizzare l'installazione per il runtime di integrazione Azure-SSIS). | Accedere alle risorse direttamente nei pacchetti tramite un percorso UNC, ad esempio, se si usano condivisioni file o File di Azure: `\\YourFileShareServerName\YourFolderName` o `\\YourAzureStorageAccountName.file.core.windows.net\YourFolderName` | Sono supportati più set di credenziali per risorse connesse diverse | - Condivisioni file in macchine virtuali locali/di Azure<br/><br/> - File di Azure, vedere [Montare una condivisione file di Azure](https://docs.microsoft.com/azure/storage/files/storage-how-to-use-files-windows) <br/><br/> - SQL Server in macchine virtuali locali/di Azure con l'autenticazione di Windows<br/><br/> - Altre risorse con l'autenticazione di Windows |
| Montaggio di unità in fase di esecuzione del pacchetto (non persistente) | Per pacchetto | Eseguire il comando `net use` nell'attività Esegui processo aggiunta all'inizio del flusso di controllo nei pacchetti, ad esempio, `net use D: \\YourFileShareServerName\YourFolderName` | Accedere alle condivisioni file tramite unità mappate | Sono supportate più unità per condivisioni file diverse | - Condivisioni file in macchine virtuali locali/di Azure<br/><br/> - File di Azure, vedere [Montare una condivisione file di Azure](https://docs.microsoft.com/azure/storage/files/storage-how-to-use-files-windows) |
|||||||

> [!WARNING]
> Se non si usa uno dei metodi sopra riportati per l'accesso ad archivi dati con l'autenticazione di Windows, i pacchetti che dipendono dall'autenticazione di Windows non saranno in grado di accedere e si verificheranno errori in fase di esecuzione. 

Il resto di questo articolo descrive come configurare il catalogo SSIS (SSISDB) ospitato in un server/un'istanza gestita di database SQL di Azure per eseguire pacchetti in Azure-SSIS IR, che usano l'autenticazione di Windows per accedere ad archivi dati. 

## <a name="you-can-only-use-one-set-of-credentials"></a>È possibile usare un solo set di credenziali
Quando si usa l'autenticazione di Windows in un pacchetto SSIS, è possibile usare un solo set di credenziali. Le credenziali del dominio specificate quando si esegue la procedura illustrata in questo articolo sono valide per tutte le esecuzioni di pacchetti interattive o pianificate in Azure-SSIS IR, finché non si modificano o rimuovono le credenziali. Se il pacchetto deve connettersi a più archivi dati con set di credenziali diversi, è consigliabile prendere in considerazione i metodi alternativi descritti in precedenza.

## <a name="provide-domain-credentials-for-windows-authentication"></a>Specificare le credenziali di dominio per l'autenticazione di Windows
Per specificare le credenziali del dominio che consentono ai pacchetti che usano l'autenticazione di Windows di accedere ad archivi dati locali, eseguire le operazioni seguenti:

1.  Con SQL Server Management Studio (SSMS) o un altro strumento, connettersi al server/all'istanza gestita di database SQL di Azure che ospita il database SSISDB. Per altre informazioni, vedere [Connettersi a SSISDB in Azure](ssis-azure-connect-to-catalog-database.md).

2.  Con SSISDB come database corrente, aprire una finestra di query.

3.  Eseguire la stored procedure seguente e specificare le credenziali del dominio appropriate:

    ```sql
    catalog.set_execution_credential @user='<your user name>', @domain='<your domain name>', @password='<your password>'
    ```

4.  Eseguire i pacchetti SSIS. I pacchetti useranno le credenziali specificate per accedere agli archivi dati locali con autenticazione di Windows.

### <a name="view-domain-credentials"></a>Visualizzare le credenziali del dominio
Per visualizzare le credenziali del dominio attive, eseguire queste operazioni:

1.  Con SSMS o un altro strumento, connettersi al server/all'istanza gestita di database SQL di Azure che ospita SSISDB. Per altre informazioni, vedere [Connettersi a SSISDB in Azure](ssis-azure-connect-to-catalog-database.md).

2.  Con SSISDB come database corrente, aprire una finestra di query.

3.  Eseguire la stored procedure seguente e controllare l'output:

    ```sql
    SELECT * 
    FROM catalog.master_properties
    WHERE property_name = 'EXECUTION_DOMAIN' OR property_name = 'EXECUTION_USER'
    ```

### <a name="clear-domain-credentials"></a>Cancellare le credenziali del dominio
Per cancellare e rimuovere le credenziali specificate come descritto in questo articolo, eseguire queste operazioni:

1.  Con SSMS o un altro strumento, connettersi al server/all'istanza gestita di database SQL di Azure che ospita SSISDB. Per altre informazioni, vedere [Connettersi a SSISDB in Azure](ssis-azure-connect-to-catalog-database.md).

2.  Con SSISDB come database corrente, aprire una finestra di query.

3.  Eseguire la stored procedure seguente:

    ```sql
    catalog.set_execution_credential @user='', @domain='', @password=''
    ```

## <a name="connect-to-a-sql-server-on-premises"></a>Connettersi a SQL Server in locale 
Per verificare se è possibile connettersi a SQL Server locale, eseguire le operazioni seguenti:

1.  Per eseguire questo test, cercare un computer non appartenente al dominio.

2.  Nel computer non appartenente al dominio eseguire il comando seguente per avviare SSMS con le credenziali del dominio che si vuole usare:

    ```cmd
    runas.exe /netonly /user:<domain>\<username> SSMS.exe
    ```

3.  Da SSMS controllare se è possibile connettersi a SQL Server in locale.

### <a name="prerequisites"></a>Prerequisites
Per accedere a Server SQL in locale da pacchetti in esecuzione in Azure, eseguire le operazioni seguenti:

1.  In Gestione configurazione SQL Server abilitare il protocollo TCP/IP.
2.  Consentire l'accesso attraverso Windows Firewall. Per altre informazioni, vedere [Configure Windows Firewall to access SQL Server](https://docs.microsoft.com/sql/sql-server/install/configure-the-windows-firewall-to-allow-sql-server-access) (Configurare Windows Firewall per accedere a SQL Server).
3.  Aggiungere Azure-SSIS IR a una rete virtuale connessa a SQL Server in locale.  Per altre informazioni, vedere [Aggiungere Azure-SSIS Integration Runtime a una rete virtuale](https://docs.microsoft.com/azure/data-factory/join-azure-ssis-integration-runtime-virtual-network).
4.  Usare la stored procedure `catalog.set_execution_credential` SSISDB per fornire le credenziali come descritto in questo articolo.

## <a name="connect-to-a-file-share-on-premises"></a>Connettersi a una condivisione file in locale 
Per verificare se è possibile connettersi a una condivisione file locale, eseguire le operazioni seguenti:

1.  Per eseguire questo test, cercare un computer non appartenente al dominio.

2.  Nel computer non appartenente al dominio eseguire i comandi seguenti. Questi comandi aprono una finestra del prompt dei comandi con le credenziali del dominio che si vuole usare, quindi verificano la connettività alla condivisione file in locale recuperando un elenco di directory.

    ```cmd
    runas.exe /netonly /user:<domain>\<username> cmd.exe
    dir \\fileshare
    ```

3.  Verificare se viene restituito l'elenco di directory per la condivisione file in locale.

### <a name="prerequisites"></a>Prerequisites
Per accedere a una condivisione file in locale dai pacchetti in esecuzione in Azure, eseguire le operazioni seguenti:

1.  Consentire l'accesso attraverso Windows Firewall.
2.  Aggiungere Azure-SSIS IR a una rete virtuale connessa alla condivisione file in locale.  Per altre informazioni, vedere [Aggiungere Azure-SSIS Integration Runtime a una rete virtuale](https://docs.microsoft.com/azure/data-factory/join-azure-ssis-integration-runtime-virtual-network).
3.  Usare la stored procedure `catalog.set_execution_credential` SSISDB per fornire le credenziali come descritto in questo articolo.

## <a name="connect-to-a-file-share-on-azure-vm"></a>Connettersi a una condivisione file in una macchina virtuale di Azure
Per accedere a una condivisione file nella macchina virtuale di Azure dai pacchetti in esecuzione in Azure, eseguire le operazioni seguenti:

1.  Con SSMS o un altro strumento, connettersi al server/all'istanza gestita di database SQL di Azure che ospita SSISDB. Per altre informazioni, vedere [Connettersi a SSISDB in Azure](ssis-azure-connect-to-catalog-database.md).

2.  Con SSISDB come database corrente, aprire una finestra di query.

3.  Eseguire la stored procedure seguente e specificare le credenziali del dominio appropriate:

    ```sql
    catalog.set_execution_credential @domain = N'.', @user = N'username of local account on Azure virtual machine', @password = N'password'
    ```

## <a name="connect-to-a-file-share-in-azure-files"></a>Connettersi a una condivisione file in File di Azure
Per altre informazioni sui file di Azure, vedere [File di Azure](https://azure.microsoft.com/services/storage/files/).

Per accedere a una condivisione file in File di Azure dai pacchetti in esecuzione in Azure, eseguire le operazioni seguenti:

1.  Con SSMS o un altro strumento, connettersi al server/all'istanza gestita di database SQL di Azure che ospita SSISDB. Per altre informazioni, vedere [Connettersi a SSISDB in Azure](ssis-azure-connect-to-catalog-database.md).

2.  Con SSISDB come database corrente, aprire una finestra di query.

3.  Eseguire la stored procedure seguente e specificare le credenziali del dominio appropriate:

    ```sql
    catalog.set_execution_credential @domain = N'Azure', @user = N'<storage-account-name>', @password = N'<storage-account-key>'
    ```

## <a name="next-steps"></a>Passaggi successivi
- Distribuire i pacchetti. Per altre informazioni, vedere [Distribuire un progetto SSIS con SQL Server Management Studio (SSMS)](../ssis-quickstart-deploy-ssms.md).
- Eseguire i pacchetti. Per altre informazioni, vedere [Eseguire pacchetti SSIS in Azure con SSMS](../ssis-quickstart-run-ssms.md).
- Pianificare i pacchetti. Per altre informazioni, vedere [Pianificare i pacchetti SSIS in Azure](ssis-azure-schedule-packages.md).
