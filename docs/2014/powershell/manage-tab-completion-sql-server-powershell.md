---
title: Gestire il completamento alla pressione del tasto TAB (SQL Server PowerShell) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: scripting
ms.topic: conceptual
ms.assetid: 6296848a-890f-4ad3-8d9f-92ed6a79aa00
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: ec946a26c898c4ed66bd60e1ad71e69c008766df
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62922952"
---
# <a name="manage-tab-completion-sql-server-powershell"></a>Gestione del completamento alla pressione del tasto TAB (SQL Server PowerShell)
  Gli snap-in di PowerShell per [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] introducono tre variabili (`$SqlServerMaximumTabCompletion`, `$SqlServerMaximumChildItems` e `$SqlServerIncludeSystemObjects`) per controllare il completamento alla pressione del tasto TAB di Windows PowerShell. Il completamento alla pressione del tasto TAB consente di ridurre la digitazione restituendo tabelle di elementi i cui nomi iniziano con la stringa che si sta digitando.  
  
## <a name="before-you-begin"></a>Prima di iniziare  
 Con il completamento alla pressione del tasto TAB di Windows PowerShell, dopo aver digitato parte del nome di un percorso o di un cmdlet, è possibile premere il tasto TAB per ottenere un elenco degli elementi il cui nome corrisponde a quanto già digitato. È quindi possibile selezionare l'elemento desiderato dall'elenco senza digitare il resto del nome.  
  
 Se si utilizza un database che contiene molti oggetti, l'elenco di completamento alla pressione del tasto TAB può risultare molto lungo. Anche alcuni tipi di oggetto di [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] , ad esempio le viste, includono numerosi oggetti di sistema.  
  
 Gli snap-in di [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] introducono tre variabili di sistema che possono essere usate per controllare la quantità di informazioni generata dal completamento alla pressione del tasto TAB e da **Get-ChildItem**.  
  
 **$SqlServerMaximumTabCompletion =** *n*  
 Specifica il numero massimo di oggetti da includere in un elenco di completamento alla pressione del tasto TAB. Se si seleziona il tasto TAB in un nodo del percorso con più di *n* oggetti, l'elenco di completamento alla pressione del tasto TAB viene troncato in corrispondenza di *n*. *n* è un numero intero. L'impostazione predefinita è 0, che indica che non esiste alcun limite al numero di oggetti elencati.  
  
 **$SqlServerMaximumChildItems =** *n*  
 Specifica il numero massimo di oggetti visualizzati da **Get-ChildItem**. Se **Get-ChildItem** viene eseguito in un nodo del percorso con più di *n* oggetti, l'elenco viene troncato in corrispondenza di *n*. *n* è un numero intero. L'impostazione predefinita è 0, che indica che non esiste alcun limite al numero di oggetti elencati.  
  
 **$SqlServerIncludeSystemObjects =** { **$True** | **$False** }  
 Se **$True**, gli oggetti di sistema vengono visualizzati dal completamento alla pressione del tasto TAB e da **Get-ChildItem**. Se **$False**, non viene visualizzato alcun oggetto di sistema. L'impostazione predefinita è **$False**.  
  
## <a name="set-the-sql-server-tab-completion-variables"></a>Impostazione delle variabili per il completamento alla pressione del tasto TAB  
 Per tutte le variabile di cui si desidera modificare il valore predefinito, impostare la variabile sul nuovo valore.  
  
### <a name="example-powershell"></a>Esempio (PowerShell)  
 Nell'esempio seguente vengono impostate tutte e tre le variabili e vengono elencate le relative impostazioni:  
  
```  
$SqlServerMaximumTabCompletion = 20  
$SqlServerMaximumChildItems = 10  
$SqlServerIncludeSystemObjects = $False  
dir variable:sqlserver*  
```  
  
## <a name="see-also"></a>Vedere anche  
 [SQL Server PowerShell](sql-server-powershell.md)  
  
  
