---
title: LOCALDB_ERROR_INSTANCE_FOLDER_PATH_TOO_LONG | Microsoft Docs
ms.custom: ''
ms.date: 03/04/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: performance
ms.topic: reference
ms.assetid: c178a308-8d99-47fc-8a49-5a480dc592f6
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 94439a6981a2cf891a55bcbda7498db83e1fa52e
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62990575"
---
# <a name="localdberrorinstancefolderpathtoolong"></a>LOCALDB_ERROR_INSTANCE_FOLDER_PATH_TOO_LONG
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
    
## <a name="details"></a>Dettagli  
  
|||  
|-|-|  
|Nome prodotto|SQL Server|  
|ID evento|260|  
|Origine evento|Runtime database locale di SQL Server 12.0|  
|Componente|API di Runtime database locale|  
|Testo del messaggio|La lunghezza del percorso completo della cartella di istanze del database locale è superiore a MAX_PATH. L'istanza deve essere archiviata nella cartella: SQL Server locale DB\Instances %%LOCALAPPDATA%%\Microsoft\Microsoft\\< nome istanza\>.|  
  
## <a name="explanation"></a>Spiegazione  
 Percorso di archiviazione richiesto per l'istanza più lungo di MAX_PATH.  
  
## <a name="user-action"></a>Azione dell'utente  
 Creare un nuovo percorso più corto di MAX_PATH.  
  
  
