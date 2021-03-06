---
title: Stato di sola lettura (Driver Excel) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- read-only status for Excel driver [ODBC]
- Excel driver [ODBC], read-only status
ms.assetid: ef5d773b-4f8f-4005-b985-84b53d8e9f9b
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 17425e76814a8397b9d2e6167248f35e52ac6cfa
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "63316743"
---
# <a name="read-only-status-excel-driver"></a>Stato di sola lettura (driver Excel)
Quando viene usato il driver di Microsoft Excel, origine dati le tabelle vengono aperti in sola lettura per impostazione predefinita e possono essere aperto da un solo utente alla volta. Anche se le tabelle hanno lo stato di sola lettura, tuttavia, le applicazioni possono eseguire gli inserimenti e aggiornamenti per le tabelle di Microsoft Excel.  
  
 Quando un'applicazione esegue un comando Salva con nome dei dati di Microsoft Excel tramite il driver di Microsoft Excel, l'applicazione deve creare una nuova tabella e inserire i dati da salvare nella nuova tabella. Gli inserimenti comportare un'aggiunta alla tabella. Altre operazioni non possono essere eseguite sulla tabella fino a quando non viene chiuso e riaperto. Una volta chiusa, la tabella non insert successivo può essere eseguita perché la tabella è quindi una tabella di sola lettura.  
  
 È possibile aggiornare i valori quando si usa il driver di Microsoft Excel, ma non può essere eliminata una riga da una tabella basata su un foglio di calcolo di Microsoft Excel, in modo che gli aggiornamenti non vengono considerati supportati ufficialmente dal driver per Microsoft Excel.
