---
title: Usare cmdlet del motore di database | Microsoft Docs
ms.custom: 
ms.date: 08/04/2016
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Cmdlets [SQL Server], Encode-Sqlname
- Encode-Sqlname cmdlet
- PowerShell [SQL Server], Encode-Sqlname
- Convert-UrnToPath cmdlet
- PowerShell [SQL Server], cmdlets
- Cmdlets [SQL Server]
- PowerShell [SQL Server], Convert-UrnToPath
- Cmdlets [SQL Server], Convert-UrnToPath
- Decode-Sqlname cmdlet
- PowerShell [SQL Server], Decode-Sqlname
- Cmdlets [SQL Server], Decode-Sqlname
ms.assetid: 720aa982-09ae-41a3-b603-a91004cfbe3e
caps.latest.revision: 25
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.translationtype: Human Translation
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: 457781b7e16a5722f4d232cff14b8f20c7651972
ms.contentlocale: it-it
ms.lasthandoff: 06/22/2017

---
# <a name="use-the-database-engine-cmdlets"></a>Utilizzo di cmdlet del motore di database
  I cmdlet di Windows PowerShell sono comandi a una sola funzione che in genere presentano una convenzione di denominazione verbo-nome, ad esempio **Get-Help** o **Set-MachineName**. Il provider [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] per Windows PowerShell fornisce cmdlet specifici di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
## <a name="database-engine-cmdlets"></a>Cmdlet del motore di database  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] implementa un numero ridotto di cmdlet per [!INCLUDE[ssDE](../../includes/ssde-md.md)]. Questi cmdlet vengono utilizzati principalmente per eseguire script Transact-SQL esistenti dai nuovi script di PowerShell, valutare criteri di gestione basata su criteri e aiutare nella specifica degli identificatori di SQL Server nei percorsi del provider SQL Server.  
  
 La maggior parte degli script di Windows PowerShell funzionano con [!INCLUDE[ssDE](../../includes/ssde-md.md)] tramite il provider SQL Server PowerShell e i modelli a oggetti di facilità di gestione di SQL Server. Per altre informazioni, vedere [SQL Server PowerShell](../../relational-databases/scripting/sql-server-powershell.md).  
  
### <a name="get-cmdlet-help"></a>Ottenere la Guida sui cmdlet  
 Nell'ambiente di Windows PowerShell il cmdlet **Get-Help** offre informazioni della Guida su ogni cmdlet. Il cmdlet**Get-Help** restituisce informazioni come la sintassi, le definizioni dei parametri, i tipi di input e di output e una descrizione dell'azione eseguita dal cmdlet. Per altre informazioni, vedere [Get Help SQL Server PowerShell](../../relational-databases/scripting/get-help-sql-server-powershell.md).  
  
### <a name="partial-parameter-names"></a>Nomi di parametri parziali  
 Non è necessario specificare il nome completo di un parametro di un cmdlet. Basta specificare una parte del nome sufficiente a identificarlo in modo univoco rispetto agli altri parametri che sono supportati dal cmdlet. Negli esempi che seguono vengono illustrati tre modi di specificare il parametro **Invoke-Sqlcmd -QueryTimeout** :  
  
```  
Invoke-Sqlcmd -Query "SELECT @@VERSION;" -QueryTimeout 3  
Invoke-Sqlcmd -Query "SELECT @@VERSION;" -QueryTime 3  
Invoke-Sqlcmd -Query "SELECT @@VERSION;" -QueryT 3  
```  
  
## <a name="database-engine-cmdlet-tasks"></a>Attività del cmdlet del motore di database  
  
|Descrizione dell'attività|Argomento|  
|----------------------|-----------|  
|Descrive l'uso di **Invoke-Sqlcmd** per eseguire script o comandi di **sqlcmd** che contengono le istruzioni [!INCLUDE[tsql](../../includes/tsql-md.md)] o XQuery. Può accettare l'input di **sqlcmd** come parametro di input della stringa di caratteri o come nome di un file script da aprire.|[Cmdlet Invoke-Sqlcmd](../../powershell/invoke-sqlcmd-cmdlet.md)|  
|Descrive l'uso di **Invoke-PolicyEvaluation** per indicare se un set di destinazioni di oggetti [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] è conforme alle condizioni definite nei criteri di gestione basata su criteri. Facoltativamente, il cmdlet può essere utilizzato per riconfigurare qualsiasi opzione impostabile negli oggetti di destinazione che non sono conformi alle condizioni dei criteri.|[cmdlet Invoke-PolicyEvaluation](../../powershell/invoke-policyevaluation-cmdlet.md)|  
|Descrive l'uso di **Encode-Sqlname** e di **Decode-Sqlname** per gestire identificatori di SQL Server che contengono caratteri non supportati nei percorsi di Windows PowerShell.|[Codificare e decodificare identificatori di SLQ Server](../../relational-databases/scripting/encode-and-decode-sql-server-identifiers.md)|  
|Descrive l'uso di **Convert-UrnToPath** per convertire un Uniform Resource Name (URN) dell'oggetto di facilità di gestione di SQL Server nel percorso del provider SQL Server equivalente.|[Conversione di URN in percorsi di provider di SQL Server](../../relational-databases/scripting/convert-urns-to-sql-server-provider-paths.md)|  
  
## <a name="see-also"></a>Vedere anche  
 [Provider PowerShell per SQL Server](../../relational-databases/scripting/sql-server-powershell-provider.md)   
 [SQL Server PowerShell](../../relational-databases/scripting/sql-server-powershell.md)   
[Panoramica dei cmdlet di PowerShell per Gruppi di disponibilità Always On (SQL Server)](../../database-engine/availability-groups/windows/overview-of-powershell-cmdlets-for-always-on-availability-groups-sql-server.md)
  
  
