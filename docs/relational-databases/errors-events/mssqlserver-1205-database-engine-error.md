---
title: MSSQLSERVER_1205 | Microsoft Docs
ms.custom: ''
ms.date: 04/04/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: supportability
ms.topic: language-reference
helpviewer_keywords:
- 1205 (Database Engine error)
ms.assetid: 9fe3f67c-df3c-4642-a3a4-ccc0e138b632
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: c1c42e2e64a0ff43c34d4d928d75ae091702d7db
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 10/01/2018
ms.locfileid: "47724600"
---
# <a name="mssqlserver1205"></a>MSSQLSERVER_1205
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  
## <a name="details"></a>Dettagli  
  
|||  
|-|-|  
|Nome prodotto|SQL Server|  
|ID evento|1205|  
|Origine evento|MSSQLSERVER|  
|Componente|SQLEngine|  
|Nome simbolico|LK_VICTIM|  
|Testo del messaggio|La transazione (ID di processo %d) è stata interrotta a causa di un deadlock delle risorse %.*ls con un altro processo. Ripetere la transazione.|  
  
## <a name="explanation"></a>Spiegazione  
Si è tentato di accedere a risorse in ordine conflittuale in transazioni distinte, causando un deadlock. Ad esempio  
  
-   Transaction1 aggiorna **Table1.Row1**, mentre Transaction2 aggiorna **Table2.Row2**.  
  
-   Transaction1 tenta di aggiornare **Table2.Row2** ma viene bloccata perché non è ancora stato eseguito il commit di Transaction2.  
  
-   Transaction2 tenta quindi di aggiornare **Table1.Row1** ma viene bloccata perché non è stato eseguito il commit di Transaction1.  
  
-   Si verifica un deadlock perché Transaction1 è in attesa del completamento di Transaction2 e Transaction2 è in attesa a sua volta del completamento di Transaction1.  
  
Il sistema rileva il deadlock e sceglie una delle due transazioni interessate come "vittima". Genera quindi il messaggio ed esegue il rollback della transazione della vittima.  
  
## <a name="user-action"></a>Azione dell'utente  
Eseguire nuovamente la transazione. È inoltre possibile modificare l'applicazione per evitare i deadlock. È possibile tentare di eseguire nuovamente la transazione scelta come vittima. In base alle operazioni che verranno eseguite simultaneamente, è probabile che la transazione abbia esito positivo.  
  
Per impedire che si verifichino deadlock, è consigliabile che tutte le transazioni accedano alle righe nello stesso ordine (**Table1**, quindi **Table2**). In questo modo, sebbene sia possibile che si verifichi un blocco, non si verificherà un deadlock.  
  
