---
title: Gestire l'autenticazione nel motore di database PowerShell | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: scripting
ms.topic: conceptual
ms.assetid: ab9212a6-6628-4f08-a38c-d3156e05ddea
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 0992e3a956a2b498d92186fa91c0ed4fbddf6102
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62762048"
---
# <a name="manage-authentication-in-database-engine-powershell"></a>Gestire l'autenticazione in motore di database PowerShell
  Per impostazione predefinita, i componenti PowerShell di [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] utilizzano l'autenticazione di Windows in caso di connessione a un'istanza del [!INCLUDE[ssDE](../includes/ssde-md.md)]. È possibile utilizzare l'autenticazione di SQL Server definendo un'unità virtuale PowerShell o specificando i parametri `-Username` e `-Password` per `Invoke-Sqlcmd`.  
  
1.  **Prima di iniziare:**  [Autorizzazioni](#Permissions)  
  
2.  **Per impostare l'autenticazione, usando:**  [Un'unità virtuale](#SQLAuthVirtDrv), [Invoke-Sqlcmd](#SQLAuthInvSqlCmd)  
  
##  <a name="Permissions"></a> Autorizzazioni  
 Tutte le azioni eseguibili in un'istanza del [!INCLUDE[ssDE](../includes/ssde-md.md)] vengono controllate dalle autorizzazioni concesse alle credenziali di autenticazione utilizzate per connettersi all'istanza. Per impostazione predefinita, il provider e i cmdlet di [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] utilizzano l'account di Windows in esecuzione per eseguire una connessione con autenticazione di Windows al [!INCLUDE[ssDE](../includes/ssde-md.md)].  
  
 Per effettuare una connessione con autenticazione di [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] è necessario fornire un ID di accesso per l'autenticazione di SQL Server e una password. Quando si usa la [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] provider, è necessario associare il [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] credenziali di accesso a un'unità virtuale e quindi usare il comando change directory (`cd`) per connettersi a tale unità. In Windows PowerShell le credenziali di sicurezza possono essere associate solo a unità virtuali.  
  
##  <a name="SQLAuthVirtDrv"></a> Autenticazione di SQL Server tramite un'unità virtuale  
 **Per creare un'unità virtuale associata a un accesso di autenticazione di SQL Server**  
  
1.  Creare una funzione che:  
  
    1.  Disponga di parametri per il nome da assegnare all'unità virtuale, l'ID di accesso e il percorso del provider da associare all'unità virtuale.  
  
    2.  Utilizzare `read-host` per richiedere l'utente la password.  
  
    3.  Utilizzare `new-object` per creare un oggetto delle credenziali.  
  
    4.  Utilizzare `new-psdrive` per creare un'unità virtuale con le credenziali fornite.  
  
2.  Richiamare la funzione per creare un'unità virtuale con le credenziali fornite.  
  
### <a name="example-virtual-drive"></a>Esempio (unità virtuale)  
 In questo esempio viene creata una funzione denominata **sqldrive** che può essere utilizzata per creare un'unità virtuale associata all'account di accesso con autenticazione di [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] e all'istanza specificati.  
  
 La funzione **sqldrive** richiede di immettere la password per effettuare l'accesso, mascherandola durante la digitazione. Quando si usa il comando change directory (`cd`) per connettersi a un percorso con il nome dell'unità virtuale, tutte le operazioni vengono eseguite tramite il [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] credenziali account di accesso di autenticazione specificato al momento della creazione dell'unità.  
  
```  
## Create a function that specifies the login and prompts for the password.  
  
function sqldrive  
{  
    param( [string]$name, [string]$login = "MyLogin", [string]$root = "SQLSERVER:\SQL\MyComputer\MyInstance" )  
    $pwd = read-host -AsSecureString -Prompt "Password"  
    $cred = new-object System.Management.Automation.PSCredential -argumentlist $login,$pwd  
    New-PSDrive $name -PSProvider SqlServer -Root $root -Credential $cred -Scope 1  
}  
  
## Use the sqldrive function to create a SQLAuth virtual drive.  
sqldrive SQLAuth  
  
## CD to the virtual drive, which invokes the supplied authentication credentials.  
cd SQLAuth  
```  
  
##  <a name="SQLAuthInvSqlCmd"></a> Autenticazione di SQL Server tramite Invoke-Sqlcmd  
 **Per utilizzare Invoke-Sqlcmd con l'autenticazione di SQL Server**  
  
1.  Utilizzare il parametro `-Username` per specificare un ID di accesso e il parametro `-Password` per specificare la password associata.  
  
### <a name="example-invoke-sqlcmd"></a>Esempio (Invoke-Sqlcmd)  
 In questo esempio viene utilizzato l'host della lettura cmdlet per la richiesta di una password all'utente, quindi viene stabilita la connessione tramite l'autenticazione di SQL Server.  
  
```  
## Prompt the user for their password.  
$pwd = read-host -AsSecureString -Prompt "Password"  
  
Invoke-Sqlcmd -Query "SELECT GETDATE() AS TimeOfQuery;" -ServerInstance "MyComputer\MyInstance" -Username "MyLogin" -Password $pwd  
```  
  
## <a name="see-also"></a>Vedere anche  
 [SQL Server PowerShell](sql-server-powershell.md)   
 [Provider PowerShell per SQL Server](sql-server-powershell-provider.md)   
 [Cmdlet Invoke-Sqlcmd](../database-engine/invoke-sqlcmd-cmdlet.md)  
  
  
