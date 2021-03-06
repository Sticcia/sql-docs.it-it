---
title: Quali sono i pool di calcolo?
titleSuffix: SQL Server big data clusters
description: Questo articolo descrive il pool di calcolo in un cluster di big data di SQL Server 2019 (anteprima).
author: rothja
ms.author: jroth
manager: craigg
ms.date: 02/28/2019
ms.topic: conceptual
ms.prod: sql
ms.technology: big-data-cluster
ms.custom: seodec18
ms.openlocfilehash: d7965ff1f29310f39fb5b8b5994b3967b928ecde
ms.sourcegitcommit: 323d2ea9cb812c688cfb7918ab651cce3246c296
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/18/2019
ms.locfileid: "58860243"
---
# <a name="what-are-compute-pools-in-a-sql-server-big-data-cluster"></a>Quali sono i pool di calcolo in un cluster di big data di SQL Server?

[!INCLUDE[tsql-appliesto-ssver15-xxxx-xxxx-xxx](../includes/tsql-appliesto-ssver15-xxxx-xxxx-xxx.md)]

Questo articolo descrive il ruolo del *pool di calcolo di SQL Server* in un cluster di big data anteprima di SQL Server 2019. I pool di calcolo offrono le risorse di calcolo a scalabilità orizzontale per un cluster di big data. Le sezioni seguenti descrivono l'architettura e la funzionalità di un pool di calcolo.

## <a name="compute-pool-architecture"></a>Architettura del pool di calcolo

Un pool di calcolo è costituito da uno o più POD in esecuzione in Kubernetes di calcolo. La creazione automatica e la gestione di questi POD è coordinata dal [istanza master di SQL Server](concept-master-instance.md). Ogni pod contiene un set di servizi di base e un'istanza del motore di database di SQL Server.

## <a name="scale-out-groups"></a>Gruppi con scalabilità orizzontale

Un pool di calcolo può fungere da un gruppo con scalabilità orizzontale PolyBase per le query distribuite su origini dati differenti, ad esempio HDFS, Oracle, MongoDB o Terradata. Usando i POD di calcolo in Kubernetes, è possono automatizzare i cluster di big data creazione e configurazione di calcolo POD per gruppi con scalabilità orizzontale di PolyBase.

## <a name="next-steps"></a>Passaggi successivi

Per altre informazioni sui cluster di big data di SQL Server, vedere le risorse seguenti:

- [Quali sono i cluster di SQL Server 2019 dei big Data?](big-data-cluster-overview.md)
- [Workshop: Cluster di big data Microsoft SQL Server architettura](https://github.com/Microsoft/sqlworkshops/tree/master/sqlserver2019bigdataclusters)
