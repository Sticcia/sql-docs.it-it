---
title: Configurare Kubernetes con kubeadm
titleSuffix: SQL Server big data clusters
description: Informazioni su come configurare su Kubernetes in più Ubuntu 16.04 o 18.04 macchine (fisiche o virtuali) per le distribuzioni di cluster (anteprima) di SQL Server 2019 dei big Data.
author: rothja
ms.author: jroth
manager: craigg
ms.date: 02/28/2019
ms.topic: conceptual
ms.prod: sql
ms.technology: big-data-cluster
ms.custom: seodec18
ms.openlocfilehash: 4e79c74851dae2d86b74064799b053d57b1a17db
ms.sourcegitcommit: 5748d710960a1e3b8bb003d561ff7ceb56202ddb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/09/2019
ms.locfileid: "65488278"
---
# <a name="configure-kubernetes-on-multiple-machines-for-sql-server-big-data-cluster-deployments"></a>Configurare Kubernetes su più computer per le distribuzioni di cluster di SQL Server i big Data

[!INCLUDE[tsql-appliesto-ssver15-xxxx-xxxx-xxx](../includes/tsql-appliesto-ssver15-xxxx-xxxx-xxx.md)]

Questo articolo viene fornito un esempio d'uso **kubeadm** configurare Kubernetes su più computer per le distribuzioni di cluster (anteprima) di SQL Server 2019 dei big Data. In questo esempio, più Ubuntu 16.04 o 18.04 macchine LTS (fisiche o virtuale) vengono usati come destinazione. Se si distribuisce a un'altra piattaforma di Linux, è necessario modificare alcuni dei comandi in modo che corrisponda il sistema.  

> [!TIP] 
> Per gli script di esempio di configurazione di Kubernetes, vedere [creare un cluster Kubernetes usando Kubeadm in Ubuntu 16.04 LTS o 18.04 LTS](https://github.com/Microsoft/sql-server-samples/tree/master/samples/features/sql-big-data-cluster/deployment/kubeadm).

## <a name="prerequisites"></a>Prerequisiti

- Valore minimo di 3 Linux computer fisici o macchine virtuali
- Configurazione consigliata per ogni computer:
   - 8 CPU
   - 32 GB di memoria
   - 100 GB di spazio di archiviazione

## <a name="prepare-the-machines"></a>Preparare i computer

In ogni computer, esistono diversi prerequisiti necessari. In un terminale bash, eseguire i comandi seguenti in ogni computer:

1. Aggiungere il computer corrente per il `/etc/hosts` file:

   ```bash
   echo $(hostname -i) $(hostname) | sudo tee -a /etc/hosts
   ```

1. Disabilitare lo swapping su tutti i dispositivi.

   ```bash
   sudo sed -i "/ swap / s/^/#/" /etc/fstab
   sudo swapoff -a
   ```

1. Importare le chiavi e registrare il repository per Kubernetes.

   ```bash
   sudo curl -s https://packages.cloud.google.com/apt/doc/apt-key.gpg | sudo apt-key add -
   echo 'deb http://apt.kubernetes.io/ kubernetes-xenial main' | sudo tee -a /etc/apt/sources.list.d/kubernetes.list
   ```

1. Configurare docker e Kubernetes prerequisiti nel computer.

   ```bash
   KUBE_DPKG_VERSION=1.11.3-00
   sudo apt-get update && /
   sudo apt-get install -y ebtables ethtool && /
   sudo apt-get install -y docker.io && /
   sudo apt-get install -y apt-transport-https && /
   sudo apt-get install -y kubelet=$KUBE_DPKG_VERSION kubeadm=$KUBE_DPKG_VERSION kubectl=$KUBE_DPKG_VERSION && /
   curl https://raw.githubusercontent.com/kubernetes/helm/master/scripts/get | bash
   ```
 
1. Impostare `net.bridge.bridge-nf-call-iptables=1`. In Ubuntu 18.04, abilitano prima i comandi seguenti `br_netfilter`.

   ```bash
   . /etc/os-release
   if [ "$VERSION_CODENAME" == "bionic" ]; then sudo modprobe br_netfilter; fi
   sudo sysctl net.bridge.bridge-nf-call-iptables=1
   ```

## <a name="configure-the-kubernetes-master"></a>Configurare il master di Kubernetes

Dopo aver eseguito i comandi precedenti in ogni computer, scegliere uno dei computer per essere il master di Kubernetes. Eseguire quindi i comandi seguenti in tale computer.

1. In primo luogo, creare un file rbac.yaml nella directory corrente con il comando seguente. 

   ```bash
   cat <<EOF > rbac.yaml
   apiVersion: rbac.authorization.k8s.io/v1beta1
   kind: ClusterRoleBinding
   metadata:
     name: default-rbac
   subjects:
   - kind: ServiceAccount
     name: default
     namespace: default
   roleRef:
     kind: ClusterRole
     name: cluster-admin
     apiGroup: rbac.authorization.k8s.io
   EOF
   ```

1. Inizializzare il master di Kubernetes in questo computer. Si verrà visualizzato l'output che il master di Kubernetes è stato inizializzato correttamente.

   ```bash
   KUBE_VERSION=1.11.3
   sudo kubeadm init --pod-network-cidr=10.244.0.0/16 --kubernetes-version=$KUBE_VERSION
   ```

1. Si noti il `kubeadm join` comando che è necessario usare negli altri server aggiunti al cluster Kubernetes. Copiare questo per un uso successivo.

   ![kubeadm join](./media/deploy-with-kubeadm/kubeadm-join.png)

1. Configurare un file di configurazione di Kubernetes home directory.

   ```bash
   mkdir -p $HOME/.kube
   sudo cp -i /etc/kubernetes/admin.conf $HOME/.kube/config
   sudo chown $(id -u):$(id -g) $HOME/.kube/config
   ```

1. Configurare il cluster e il dashboard di Kubernetes.

   ```bash
   kubectl apply -f https://raw.githubusercontent.com/coreos/flannel/master/Documentation/kube-flannel.yml
   helm init
   kubectl apply -f rbac.yaml
   kubectl apply -f https://raw.githubusercontent.com/kubernetes/dashboard/master/src/deploy/recommended/kubernetes-dashboard.yaml
   kubectl create clusterrolebinding kubernetes-dashboard --clusterrole=cluster-admin --serviceaccount=kube-system:kubernetes-dashboard
   ```

## <a name="configure-the-kubernetes-agents"></a>Configurare gli agenti di Kubernetes

Le altre macchine fungerà da agenti di Kubernetes nel cluster. 

In ognuna delle altre macchine, eseguire il `kubeadm join` comando che è stato copiato nella sezione precedente.

![agenti di join kubeadm](./media/deploy-with-kubeadm/kubeadm-join-agents.png)

## <a name="view-the-cluster-status"></a>Visualizzare lo stato del cluster

Per verificare la connessione al cluster, usare il [kubectl get](https://kubernetes.io/docs/reference/generated/kubectl/kubectl-commands) comando per restituire un elenco dei nodi del cluster.

```bash
kubectl get nodes
```

## <a name="next-steps"></a>Passaggi successivi

I passaggi descritti in questo articolo è configurato un cluster Kubernetes in più computer Ubuntu. Il passaggio successivo consiste nel distribuire il cluster di big data di SQL Server 2019. Per istruzioni, vedere l'articolo seguente:

[Distribuire SQL Server in Kubernetes](deployment-guidance.md#deploy)
