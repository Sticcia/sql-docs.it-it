---
title: MSSQLSERVER_1793 | Microsoft Docs
ms.custom: ''
ms.date: 04/04/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: supportability
ms.topic: language-reference
ms.assetid: 808db1d0-acc1-41d0-9287-8a5455001a02
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: fdddf626aa081138d58387b9562327964d600074
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62869454"
---
# <a name="mssqlserver1793"></a>MSSQLSERVER_1793
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  
## <a name="details"></a>Dettagli  
  
|||  
|-|-|  
|Nome prodotto|SQL Server|  
|ID evento|1793|  
|Origine evento|MSSQLSERVER|  
|Componente|SQLEngine|  
|Nome simbolico|FILESTREAM_BASEDATA_NEED_SAME_PARTITION|  
|Testo del messaggio|Impossibile eliminare l'indice '%.*ls'. Schema di partizione non specificato per i dati FILESTREAM.|  
  
## <a name="explanation"></a>Spiegazione  
Questo messaggio viene visualizzato quando si tenta di eliminare un indice cluster in una tabella che contiene dati FILESTREAM e si specifica una clausola **MOVE TO** per i dati di base, ma non si specifica una clausola **FILESTREAM_ON** per i dati FILESTREAM.  
  
## <a name="user-action"></a>Azione dell'utente  
Quando si elimina un indice cluster in una tabella che contiene dati FILESTREAM, utilizzare una delle opzioni seguenti:  
  
-   Specificare sia una clausola **MOVE TO** per i dati di base sia una clausola **FILESTREAM_ON** per i dati FILESTREAM.  
  
-   Non specificare una clausola **MOVE TO** per i dati di base né una clausola **FILESTREAM_ON** per i dati FILESTREAM.  
  
L'esempio seguente ha esito negativo in quanto viene specificato uno schema di partizione per i dati di base, ma non per i dati FILESTREAM.  
  
```Transact-SQL  
DROP INDEX [<clustered_index_name>] ON [<table_name>]   
WITH ( ONLINE = OFF, MOVE TO [PRIMARY] )  
GO  
```  
  
L'esempio seguente ha esito positivo in quanto viene specificata sia una clausola **MOVE TO** per i dati di base sia una clausola **FILESTREAM_ON** per i dati FILESTREAM.  
  
```Transact-SQL  
DROP INDEX [<clustered_index_name>] ON [<table_name>]   
WITH ( ONLINE = OFF, MOVE TO [PRIMARY], filestream_on 'default' )  
GO  
```  
  
L'esempio seguente ha anch'esso esito positivo in quanto non viene specificata né una clausola **MOVE TO** per i dati di base né una clausola **FILESTREAM_ON** per i dati FILESTREAM.  
  
```Transact-SQL  
DROP INDEX [<clustered_index_name>] ON [<table_name>]   
WITH ( ONLINE = OFF )  
GO  
```  
  
