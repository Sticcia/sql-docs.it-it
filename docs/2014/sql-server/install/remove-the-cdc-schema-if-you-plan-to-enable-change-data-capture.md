---
title: Rimuovere lo schema cdc se si intende abilitare change data capture | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- database-engine
ms.topic: conceptual
helpviewer_keywords:
- cdc schema
- change data capture
ms.assetid: 6a84aa25-0f31-4be3-b2dd-4f249b8254ae
author: mashamsft
ms.author: mathoma
manager: craigg
ms.openlocfilehash: a5d162635a9162871e51fe0664198302804aa487
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62855749"
---
# <a name="remove-the-cdc-schema-if-you-plan-to-enable-change-data-capture"></a>Rimuovere lo schema cdc se si intende attivare Change Data Capture
  Un database contiene già uno schema cdc. Se si intende abilitare change data capture dopo l'aggiornamento, è prima necessario eliminare questo schema cdc. Quando si attiva un database per Change Data Capture, il [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] creerà un nuovo schema denominato cdc.  
  
  
