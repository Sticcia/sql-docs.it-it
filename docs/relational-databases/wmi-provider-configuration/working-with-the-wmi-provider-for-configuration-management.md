---
title: Uso del Provider WMI per Gestione configurazione | Microsoft Docs
ms.custom: ''
ms.date: 04/12/2019
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: wmi
ms.topic: reference
helpviewer_keywords:
- permissions [WMI]
- connection strings [WMI]
- security [WMI]
- WMI Provider for Configuration Management, connection strings
- WMI Provider for Configuration Management, security
- late binding [WMI]
- WMI Provider for Configuration Management, late binding
- binding [WMI]
ms.assetid: 34daa922-7074-41d0-9077-042bb18c222a
author: CarlRabeler
ms.author: carlrab
manager: craigg
ms.openlocfilehash: 20a34f01908333650a4c5b566ccab2221a4e07c2
ms.sourcegitcommit: acb5de9f493238180d13baa302552fdcc30d83c0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/12/2019
ms.locfileid: "59542121"
---
# <a name="working-with-the-wmi-provider-for-configuration-management"></a>Utilizzo del provider WMI per Gestione configurazione

[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

Questo articolo fornisce indicazioni su come programmare con il Provider WMI per Gestione Computer.

## <a name="binding"></a>Associazione  
 Il provider WMI per Gestione configurazione è un modello a oggetti COM che supporta l'associazione anticipata e tardiva. Con l'associazione tardiva è possibile utilizzare linguaggi di scripting, come VBScript, per modificare a livello di codice gli alias, le impostazioni di rete e i servizi di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
## <a name="specifying-a-connection-string"></a>Definizione di una stringa di connessione

Le applicazioni indirizzano il provider WMI per Gestione configurazione a un'istanza di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] connettendosi a uno spazio dei nomi WMI definito dal provider. Il servizio Windows WMI esegue il mapping di questo spazio dei nomi alla DLL del provider e carica la DLL in memoria. Tutte le istanze di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] vengono rappresentate con un solo spazio dei nomi WMI.

Lo spazio dei nomi predefinito è il formato seguente. Il formato, `VV` è il numero di versione principale di SQL Server. Il numero è individuabile eseguendo `SELECT @@VERSION;`.

```console
\\.\root\Microsoft\SqlServer\ComputerManagementVV
```

Quando ci si connette tramite PowerShell, il leader `\\.\` devono essere rimossi. Ad esempio, il codice di PowerShell seguente elenca tutte le classi WMI per SQL Server 2016, che è la versione principale 13.

```powershell
Get-WmiObject -Namespace 'root\Microsoft\SqlServer\ComputerManagement13' -List
```

<!--
Updated this on 2019-04-12, per:
   ~ https://github.com/MicrosoftDocs/sql-docs/issues/1817
   ~ https://github.com/rrg92/sql-docs/commit/3d518bfc0d55f819c762abc3e5c5c9eed85abe94?diff=unified

Thus from here I (GeneMi = MightyPen) removed the following text about 'instance_name':

'root\Microsoft\SqlServer\ComputerManagement13\instance_name'

where `instance_name` defaults to `MSSQLSERVER` in a default installation of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].
-->

È possibile usare il codice di PowerShell seguente per eseguire una query tutti spazi dei nomi WMI ComputerManagement disponibili.

```powershell
gwmi -ns 'root\Microsoft\SqlServer' __NAMESPACE | ? {$_.name -match 'ComputerManagement' } | select name
```

 **Nota:** Se ci si connette tramite Windows Firewall è necessario assicurarsi che i computer sono configurati in modo appropriato. Vedere l'articolo "Connecting Through Windows Firewall" nella documentazione di Strumentazione gestione Windows sul [!INCLUDE[msCoName](../../includes/msconame-md.md)] MSDN [sito Web](https://go.microsoft.com/fwlink/?linkid=15426).  
  
## <a name="permissions-and-server-authentication"></a>Autorizzazioni e autenticazione del server  
 Per accedere al provider WMI per Gestione configurazione, è necessario che lo script di gestione WMI del client sia in esecuzione nel contesto di un amministratore nel computer di destinazione. È necessario essere membro del gruppo locale Administrators di Windows nel computer da gestire.  
  
 L'amministratore può impostare i criteri di gruppo per controllare l'accesso utente ai provider WMI. Per ulteriori informazioni sull'impostazione dei criteri di gruppo, vedere l'argomento relativo ai criteri di gruppo e a MMC nella Guida di Gestione configurazione di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
 Lo script di gestione WMI può essere utilizzato per aggiornare l'account con cui vengono eseguiti i servizi [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
 I certificati di sicurezza sono supportati dal provider WMI per Gestione configurazione. Per altre informazioni sui certificati, vedere [gerarchia di crittografia](../../relational-databases/security/encryption/encryption-hierarchy.md).  
  
## <a name="see-also"></a>Vedere anche  
 [Gestione configurazione SQL Server](../../relational-databases/sql-server-configuration-manager.md)  
  
  
