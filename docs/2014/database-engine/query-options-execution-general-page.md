---
title: Opzioni di query esecuzione (pagina generale) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- database-engine
ms.topic: conceptual
f1_keywords:
- sql12.swb.query.general.f1
ms.assetid: 858a0263-2f04-4692-b8bf-63e93c998ead
author: craigg-msft
ms.author: craigg
manager: craigg
ms.openlocfilehash: 955dcff3399f6936fb5b1f8042dae4658a55a11f
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62844775"
---
# <a name="query-options-execution-general-page"></a>Opzioni query - Esecuzione (pagina Generale)
  Utilizzare questa pagina per specificare le opzioni per l'esecuzione di query di [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] . Per accedere a questa finestra di dialogo, fare clic con il pulsante destro del mouse su una finestra dell'editor di query e quindi scegliere **Opzioni query**.  
  
## <a name="uielement-list"></a>Elenco degli elementi di interfaccia  
 **SET ROWCOUNT**  
 Il valore predefinito 0 indica che [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] rimarrà in attesa di risultati fino a quando non verranno ricevuti tutti i risultati. Specificare un valore maggiore di 0 se si desidera che [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] interrompa la query dopo aver ottenuto il numero di righe specificato. Per disabilitare questa opzione in modo che vengano restituite tutte le righe, specificare SET ROWCOUNT 0.  
  
 **SET TEXTSIZE**  
 Il valore predefinito di 2.147.483.647 byte indica che [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] fornirà un campo dati completo fino al limite dei campi dati `text`, `ntext`, `nvarchar(max)` e `varchar(max)`. Ciò non ha alcun effetto sul tipo di dati XML. Specificare un numero più piccolo per limitare i risultati in caso di valori elevati. Le colonne le cui dimensioni sono maggiori del numero specificato verranno troncate.  
  
 **Timeout esecuzione**  
 Consente di indicare il numero di secondi di attesa prima dell'annullamento della query. Il valore 0 indica un'attesa infinita, ovvero nessun timeout.  
  
 **Separatore di batch**  
 Consente di digitare una parola che verrà utilizzata per separare le istruzioni Transact-SQL in batch. Il valore predefinito è GO.  
  
 **Per impostazione predefinita, apri le nuove query in modalità SQLCMD**  
 Selezionare questa casella di controllo per aprire le nuove query in modalità SQLCMD. Questa casella di controllo è disponibile solo se la finestra di dialogo è stata aperta tramite il menu **Strumenti** .  
  
 Quando si seleziona questa opzione, tenere presente le limitazioni seguenti:  
  
-   Nell'editor di query del [!INCLUDE[ssDE](../includes/ssde-md.md)] , IntelliSense è disattivata.  
  
-   Poiché l'editor di query non è in esecuzione dalla riga di comando, non è possibile passare parametri della riga di comando, ad esempio variabili.  
  
-   Poiché l'editor di query non può rispondere ai prompt del sistema operativo, è necessario prestare attenzione a non eseguire istruzioni interattive.  
  
 **Ripristina predefiniti**  
 Reimposta le impostazioni predefinite originali per tutti i valori nella pagina.  
  
  
