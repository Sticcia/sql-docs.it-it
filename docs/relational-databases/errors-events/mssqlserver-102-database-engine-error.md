---
title: MSSQLSERVER_102 | Microsoft Docs
ms.custom: ''
ms.date: 04/04/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: supportability
ms.topic: language-reference
helpviewer_keywords:
- 102 (Database Engine error)
ms.assetid: 264dc1a2-c8a0-4c89-b5f6-951baf950299
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 795923370e39fa44b6ddf22321255d9480388925
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 10/01/2018
ms.locfileid: "47677314"
---
# <a name="mssqlserver102"></a>MSSQLSERVER_102
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  
## <a name="details"></a>Dettagli  
  
|||  
|-|-|  
|Nome prodotto|SQL Server|  
|ID evento|102|  
|Origine evento|MSSQLSERVER|  
|Componente|SQLEngine|  
|Nome simbolico|P_SYNTAXERR2|  
|Testo del messaggio|Sintassi non corretta in prossimità di '%.*ls'.|  
  
## <a name="explanation"></a>Spiegazione  
Indica un errore di sintassi. Le informazioni aggiuntive non sono disponibili perché l'errore non consente l'elaborazione dell'istruzione da parte di [!INCLUDE[ssDE](../../includes/ssde-md.md)].  
  
Questa situazione può essere causata dal tentativo di creare una chiave simmetrica utilizzando la crittografia deprecata RC4 o RC4_128 quando la modalità di compatibilità non è 90 o 100.  
  
## <a name="user-action"></a>Azione dell'utente  
Ricercare errori di sintassi nell'istruzione [!INCLUDE[tsql](../../includes/tsql-md.md)].  
  
Se si crea una chiave simmetrica utilizzando RC4 o RC4_128, selezionare un metodo di crittografia più recente, ad esempio uno degli algoritmi AES (opzione consigliata). Se è necessario utilizzare RC4, eseguire ALTER DATABASE SET COMPATIBILITY_LEVEL per impostare il database sul livello di compatibilità 90 o 100. (Non consigliato.)  
  
