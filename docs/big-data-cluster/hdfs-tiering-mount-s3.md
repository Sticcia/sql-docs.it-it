---
title: Montare S3 per la suddivisione in livelli HDFS
titleSuffix: SQL Server big data clusters
description: Questo articolo illustra come configurare la suddivisione in livelli per montare un file system di S3 esterni in HDFS in un cluster di big data (anteprima) di SQL Server 2019 HDFS.
author: nelgson
ms.author: negust
ms.reviewer: jroth
manager: craigg
ms.date: 05/22/2019
ms.topic: conceptual
ms.prod: sql
ms.technology: big-data-cluster
ms.openlocfilehash: 4254c1c47e64013533574345c14518fdc2afcb7c
ms.sourcegitcommit: be09f0f3708f2e8eb9f6f44e632162709b4daff6
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/21/2019
ms.locfileid: "65993952"
---
# <a name="how-to-mount-s3-for-hdfs-tiering-in-a-big-data-cluster"></a>Come montare S3 per HDFS la suddivisione in livelli in un cluster di big data

Le sezioni seguenti forniscono un esempio di come configurare la suddivisione in livelli con un'origine dati di archiviazione S3 HDFS.

## <a name="prerequisites"></a>Prerequisiti

- [Cluster di big data distribuita](deployment-guidance.md)
- [Strumenti dei big Data](deploy-big-data-tools.md)
  - **mssqlctl**
  - **kubectl**
- Creare e caricare dati in un bucket S3 
  - Carica CSV o Parquet file per il bucket S3. Si tratta dei dati HDFS esterni che verranno montati in HDFS nel cluster di big data.

## <a name="access-keys"></a>Chiavi di accesso

1. Aprire un prompt dei comandi in un computer client che possa accedere al cluster di big data.

1. Creare un file locale denominato **filename.creds** che contiene le credenziali dell'account S3 usando il formato seguente:

   ```text
    fs.s3a.access.key=<Access Key ID of the key>
    fs.s3a.secret.key=<Secret Access Key of the key>
   ```

   > [!TIP]
   > Per altre informazioni su come creare le chiavi di accesso di S3, vedere [chiavi di accesso S3](https://docs.aws.amazon.com/general/latest/gr/aws-sec-cred-types.html#access-keys-and-secret-access-keys).

## <a id="mount"></a> Montare l'archiviazione HDFS remoto

Ora che è stato creato un file di credenziali con le chiavi di accesso, è possibile avviare il montaggio. I passaggi seguenti montare l'archiviazione HDFS remoto S3 nell'archivio HDFS locale del cluster di big data.

1. Uso **kubectl** per trovare l'indirizzo IP dell'endpoint **controller-svc-external** servizio nel cluster di big data. Cercare il **External-IP**.

   ```bash
   kubectl get svc controller-svc-external -n <your-cluster-name>
   ```

1. Accedi con **mssqlctl** usando l'indirizzo IP esterno dell'endpoint del controller con il nome utente del cluster e la password:

   ```bash
   mssqlctl login -e https://<IP-of-controller-svc-external>:30080/
   ```

1. Montare l'archiviazione HDFS remoto in Azure usando **istallazione del pool di archiviazione cluster mssqlctl creare**. Prima di eseguire il comando seguente, sostituire i valori segnaposto:

   ```bash
   mssqlctl cluster storage-pool mount create --remote-uri s3a://<S3 bucket name> --mount-path /mounts/<mount-name> --credential-file <path-to-s3-credentials>/file.creds
   ```

   > [!NOTE]
   > Il montaggio di creare il comando è asincrona. A questo punto, non vi è alcun messaggio che indica se il montaggio ha avuto esito positivo. Vedere le [stato](#status) sezione per controllare lo stato dei punti di montaggio.

Se è stato montato, sarà possibile eseguire query sui dati HDFS ed eseguire i processi di Spark su di esso. Verrà visualizzata in HDFS per il cluster di big data nel percorso specificato dal `--mount-path`.

## <a id="status"></a> Ottenere lo stato dei punti di montaggio

Per elencare lo stato di tutti i punti di montaggio del cluster di big data, usare il comando seguente:

```bash
mssqlctl cluster storage-pool mount status
```

Per elencare lo stato di un montaggio in un percorso specifico in HDFS, usare il comando seguente:

```bash
mssqlctl cluster storage-pool mount status --mount-path <mount-path-in-hdfs>
```

## <a id="delete"></a> Eliminare il montaggio

Per eliminare il montaggio, usare il **mssqlctl cluster pool di archiviazione montaggio delete** comando e specificare il percorso di montaggio in HDFS:

```bash
mssqlctl cluster storage-pool mount delete --mount-path <mount-path-in-hdfs>
```

## <a name="next-steps"></a>Passaggi successivi

Per altre informazioni sui cluster di SQL Server 2019 dei big data, vedere [quali sono i cluster di SQL Server 2019 dei big data?](big-data-cluster-overview.md).
