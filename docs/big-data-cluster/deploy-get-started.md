---
title: Introduzione
titleSuffix: SQL Server big data clusters
description: Descrive i passaggi e le risorse per la distribuzione di cluster di big data 2019 Server SQL (anteprima).
author: rothja
ms.author: jroth
manager: craigg
ms.date: 04/23/2019
ms.topic: conceptual
ms.prod: sql
ms.technology: big-data-cluster
ms.openlocfilehash: 5aeb6f5f92eba1bad828455b472d25561570901a
ms.sourcegitcommit: d5cd4a5271df96804e9b1a27e440fb6fbfac1220
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/28/2019
ms.locfileid: "64774775"
---
# <a name="get-started-with-sql-server-big-data-clusters"></a>Introduzione ai cluster di SQL Server i big Data

[!INCLUDE[tsql-appliesto-ssver15-xxxx-xxxx-xxx](../includes/tsql-appliesto-ssver15-xxxx-xxxx-xxx.md)]

Questo articolo fornisce una panoramica su come distribuire un' [cluster di big data 2019 Server SQL (anteprima)](big-data-cluster-overview.md). Lo scopo è quello di acquisire i concetti e forniscono un framework per comprendere altri articoli sulla distribuzione in questa sezione. I passaggi di distribuzione specifici variano a seconda delle scelte effettuate piattaforma per il client e server.

## <a id="tools"></a> Strumenti client

I cluster di big data richiedono un set di strumenti client specifico. Prima di distribuire un cluster di big data in Kubernetes, è consigliabile installare gli strumenti seguenti:

| Strumento | Descrizione |
|---|---|
| **mssqlctl** | Distribuisce e gestisce i cluster di big data. |
| **kubectl** | Crea e gestisce il cluster Kubernetes sottostante. |
| **Azure Data Studio** | Interfaccia grafica per l'uso di cluster di big data. |
| **Estensione di SQL Server 2019** | Estensione di Azure Data Studio che abilita le funzionalità di cluster di big data. |

Altri strumenti sono necessari per scenari diversi. Ogni articolo deve spiegare gli strumenti dei prerequisiti per l'esecuzione di un'attività specifica. Per un elenco completo di strumenti e i collegamenti di installazione, vedere [strumenti di big data di installazione di SQL Server 2019](deploy-big-data-tools.md).

## <a name="kubernetes"></a>Kubernetes

I cluster di big data vengono distribuiti come una serie di contenitori correlati che vengono gestite nei [Kubernetes](https://kubernetes.io/docs/home). È possibile ospitare Kubernetes in diversi modi. Anche se si dispone già di un ambiente Kubernetes esistente, è consigliabile esaminare i requisiti correlati per i cluster di big data.

- **Azure Kubernetes Service (AKS)**: Servizio contenitore di AZURE consente di distribuire un cluster Kubernetes gestito in Azure. Solo gestire e mantenere i nodi agente. Con servizio contenitore di AZURE, si è autorizzati a eseguire il provisioning di un hardware per il cluster. È anche facile da usare un cluster di big data [script di distribuzione](quickstart-big-data-cluster-deploy.md) per creare il cluster AKS e distribuire il cluster di big data in un unico passaggio. Per altre informazioni sull'uso di servizio contenitore di AZURE con i cluster di big data, vedere [configurare Azure Kubernetes Service per le distribuzioni di cluster (anteprima) di SQL Server 2019 dei big data](deploy-on-aks.md).

- **Più macchine**: È anche possibile distribuire Kubernetes a più computer Linux, che può essere server fisici o macchine virtuali. Il [kubeadm](https://kubernetes.io/docs/setup/independent/create-cluster-kubeadm/) strumento può essere usato per creare il cluster Kubernetes. Questo metodo funziona bene se si dispone già di infrastruttura esistente che si desidera utilizzare per il cluster di big data. Per altre informazioni sull'uso **kubeadm** le distribuzioni con i cluster di big data, vedere [configurare su Kubernetes in più computer per le distribuzioni di cluster (anteprima) di SQL Server 2019 dei big data](deploy-with-kubeadm.md).

- **Minikube**: Minikube consente di eseguire Kubernetes in locale in un singolo server. È una scelta ottimale se si sta tentando di usare i cluster di big data o necessario utilizzarlo in uno scenario di test o sviluppo. Per altre informazioni sull'uso di Minikube, vedere la [Minikube documentazione](https://kubernetes.io/docs/setup/minikube/). Per requisiti specifici per l'uso di Minikube con i cluster di big data, vedere [configurare minikube per le distribuzioni di cluster di SQL Server 2019 dei big data](deploy-on-minikube.md).

## <a name="deploy-a-big-data-cluster"></a>Distribuire un cluster Big Data

Dopo la configurazione di Kubernetes, si distribuisce un cluster di big data con il `mssqlctl cluster create` comando. Quando si distribuisce, è possibile eseguire diversi approcci.

- Se si distribuisce in un ambiente di sviluppo e test, è possibile scegliere di usare uno dei [le configurazioni predefinite](deployment-guidance.md#deploy) disql **mssqlctl**.

- Per personalizzare la distribuzione, è possibile creare e usare la propria [i file di configurazione di distribuzione](deployment-guidance.md#configfile). 

- Per un'installazione completamente automatica, è possibile passare tutte le altre impostazioni nelle variabili di ambiente. Per altre informazioni, vedere [distribuzioni automatiche](deployment-guidance.md#unattended).

## <a name="deployment-scripts"></a>Script di distribuzione

Gli script di distribuzione per distribuzione di Kubernetes sia i cluster di big data in un unico passaggio. Offrono inoltre spesso valori predefiniti per le impostazioni del cluster di big data. Per un esempio di uno script di distribuzione per il cluster di big data in Azure Kubernetes Service (AKS), vedere l'articolo seguente:

[Distribuire un 2019 di Server SQL cluster dei big data con uno script di distribuzione (AKS)](quickstart-big-data-cluster-deploy.md).

È possibile personalizzare qualsiasi script di distribuzione tramite la creazione di una versione personalizzata che consente di configurare le variabili di ambiente cluster di big data in modo diverso.

## <a name="next-steps"></a>Passaggi successivi

Dopo aver correttamente distribuito un cluster di big data, [connettersi al cluster](connect-to-big-data-cluster.md) e prendere in considerazione [il caricamento dei dati di esempio](tutorial-load-sample-data.md) per l'uso con diverse procedure dettagliate.