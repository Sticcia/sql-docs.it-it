---
title: Utilizzare l'istanza del cluster di failover, SQL Server in Linux | Documenti Microsoft
description: 
author: MikeRayMSFT
ms.author: mikeray
manager: jhubbard
ms.date: 08/28/2017
ms.topic: article
ms.prod: sql-linux
ms.technology: database-engine
ms.assetid: 
ms.translationtype: MT
ms.sourcegitcommit: 834bba08c90262fd72881ab2890abaaf7b8f7678
ms.openlocfilehash: a8595b61afd374d6127f6cc7b9b363f325a257b5
ms.contentlocale: it-it
ms.lasthandoff: 10/02/2017

---
# <a name="operate-failover-cluster-instance---sql-server-on-linux"></a>Utilizzare l'istanza del cluster di failover, SQL Server in Linux

[!INCLUDE[tsql-appliesto-sslinux-only](../includes/tsql-appliesto-sslinux-only.md)]

Questo articolo spiega come usare un'istanza di cluster di failover di SQL Server (FCI) in Linux. Se non è stato creato un failover di SQL Server in Linux, vedere [istanza cluster di failover Configura: SQL Server in Linux](sql-server-linux-shared-disk-cluster-configure.md). 

## <a name="failover"></a>Failover

Il failover per FCI è simile a un cluster di failover di Windows Server (WSFC). Se il nodo del cluster che ospita l'istanza FCI di cui si verifichi l'errore di qualche tipo, l'istanza FCI deve automaticamente il failover a un altro nodo. A differenza di un cluster WSFC, non è possibile impostare i proprietari preferiti, in modo Pacemaker selezioni il nodo che sarà il nuovo host per l'istanza FCI.

Vi sono casi che è possibile eseguire manualmente il failover a un altro nodo. Il processo non è lo stesso di FCI su un cluster WSFC. Su un cluster WSFC, il failover delle risorse a livello di ruolo. In Pacemaker, si sceglie di spostare una risorsa, e presupponendo che tutti i vincoli siano corretti, tutti gli altri elementi vengono spostati anche. 

La modalità di failover dipende dalla distribuzione di Linux. Seguire le istruzioni per la distribuzione di linux.

- [RHEL o Ubuntu](#rhelFailover)
- [SLES](#slesFailover)

## <a name = "#rhelFailover"></a>Failover manuale (RHEL o Ubuntu)

Per eseguire un failover manuale, bopomofo Red Hat Enterprise Linux (RHEL) o il server Ubuntu eseguita i passaggi seguenti.
1.  Il comando seguente: 

   ```bash
   sudo pcs resource move <FCIResourceName> <NewHostNode> 
   ```

   \<FCIResourceName > è il nome della risorsa Pacemaker per l'istanza cluster di failover di SQL Server.

   \<NewHostNode > è il nome del nodo del cluster che si desidera ospitare l'istanza FCI. 

   Non sarà possibile ricevere un acknowledgement.

2.  Durante un failover manuale, Pacemaker crea un vincolo di percorso per la risorsa che è stato scelto per spostare manualmente. Per visualizzare questo vincolo, eseguire `sudo pcs constraint`.

3.  Dopo aver completato il failover, è possibile rimuovere il vincolo eseguendo `sudo pcs resource clear <FCIResourceName>`. 

\<FCIResourceName > è il nome della risorsa Pacemaker per l'istanza FCI. 

## <a name = "#slesFailover"></a>Failover manuale (SLES)


In Suse Linux Enterprise Server (SLES), utilizzare il `migrate` comando per eseguire il failover manuale di una FCI di SQL Server. Esempio:

```bash
crm resource migrate <FCIResourceName> <NewHostNode>
```

\<FCIResourceName > è il nome di risorsa per l'istanza del cluster di failover. 

\<NewHostNode > è il nome del nuovo host di destinazione. 


<!---
|Distribution |Topic 
|----- |-----
|**Red Hat Enterprise Linux with HA add-on** |[Configure](sql-server-linux-shared-disk-cluster-red-hat-7-configure.md)<br/>[Operate](sql-server-linux-shared-disk-cluster-red-hat-7-operate.md)
|**SUSE Linux Enterprise Server with HA add-on** |[Configure](sql-server-linux-shared-disk-cluster-sles-configure.md)
--->

## <a name="next-steps"></a>Passaggi successivi

- [Configurare l'istanza del cluster di failover, SQL Server in Linux](sql-server-linux-shared-disk-cluster-configure.md)

<!--Image references-->
