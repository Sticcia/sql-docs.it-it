---
title: SandDance per Studio dei dati di Azure
titleSuffix: Azure Data Studio
description: Come usare SandDance in Azure Data Studio
ms.custom: seodec18
ms.date: 04/18/2019
ms.prod: sql
ms.technology: azure-data-studio
ms.reviewer: alayu; sstein
ms.topic: conceptual
author: yualan
ms.author: alayu
manager: craigg
ms.openlocfilehash: 8fe968185f05c7a48415e5e158a20f4dc61b28c1
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "63142193"
---
# <a name="sanddance-for-azure-data-studio-preview"></a>SandDance per Studio dei dati di Azure (anteprima)
Azure Data Studio offre ora un modo per creare visualizzazioni rapide per i file con estensione csv e tsv che si siano lavorando. Sono incluse in file locali o i file in HDFS in Big Data Cluster di SQL Server 2019. Questa estensione è utile quando si tenta di avere una rapida esaminare i dati e comprendere cosa sta succedendo. Usiamo una tecnologia denominata SandDance da Microsoft Research, che può generare visualizzazioni sul posto dei dati.

![animazione di sanddance](https://user-images.githubusercontent.com/11507384/54236654-52d42800-44d1-11e9-859e-6c5d297a46d2.gif)

Viste di facile comprensione, consente di SandDance trovare informazioni dettagliate sui dati, che nella Guida di attivazione raccontare storie supportate dai dati, compilare in base all'evidenza i casi, testare le ipotesi, un'analisi più approfondita in superficie spiegazioni, supportare le decisioni per gli acquisti, o creare relazioni tra dati in un contesto più ampio e realistici.

SandDance utilizza visualizzazioni unit, che applicano un mapping uno a uno tra le righe nel database e i segni sullo schermo.
Le transizioni animate uniforme tra le visualizzazioni consentono di mantenere contesto durante l'interazione con i dati.

## <a name="usage"></a>Uso

A partire dal menu File, usare aprire cartelle o [Ctrl + K, Ctrl + O] per aprire la directory contenente il. File CSV.  Successivamente, all'interno del Pannello di Esplora, pulsante destro del mouse sul file con estensione csv o TSV e scegliere *visualizzazione SandDance*.

Pulsante destro del mouse su un file con estensione csv o tsv in HDFS, se si è connessi a SQL Server 2019 Big Data Cluster e si sceglie *visualizzazione SandDance*.

## <a name="known-issues"></a>Problemi noti

Attualmente un identificatore univoco devono essere la prima colonna dei dati.

Attualmente non calcoliamo il conteggio delle righe che verrà visualizzato. Tuttavia, il consumo di memoria aumenta proporzionalmente al numero di righe, pertanto è consigliabile che il set di dati o visualizzazione è limitata a circa 100K righe.

Vedere [problemi noti](https://microsoft.github.io/SandDance/#known-issues)

## <a name="release-notes"></a>Note sulla versione

### <a name="100"></a>1.0.0

Versione iniziale di azdata sanddance

## <a name="next-steps"></a>Passaggi successivi
Per altre informazioni, [visitare il repository GitHub.](https://github.com/Microsoft/SandDance)
