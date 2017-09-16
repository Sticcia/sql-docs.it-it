---
title: Creare le credenziali - Eseguire l'autenticazione nel servizio di archiviazione Azure | Microsoft Docs
ms.custom: 
ms.date: 03/01/2017
ms.prod: sql-server-2014
ms.reviewer: 
ms.suite: 
ms.technology:
- dbe-backup-restore
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- sql13.swb.backuptourl.createcred.f1
ms.assetid: 0622619d-27c5-4ff0-83e5-cde31648c27a
caps.latest.revision: 7
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.translationtype: Human Translation
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: 3bf85ebdf78e42466474e6c68a43219fbb546bd1
ms.contentlocale: it-it
ms.lasthandoff: 06/22/2017

---
# <a name="create-credential---authenticate-to-azure-storage"></a>Creare le credenziali - Eseguire l'autenticazione nel servizio di archiviazione Azure
  Utilizzare la finestra di dialogo **Backup su URL – Creazione credenziali** per creare nuove credenziali SQL.  
  
 Quando si utilizza questa finestra di dialogo per creare le credenziali, è necessario fornire un certificato di gestione di Windows Azure aggiunto all'archivio certificati locale o un profilo di pubblicazione scaricato nel computer per convalidare la sottoscrizione e le informazioni sull'account di archiviazione.  
  
 **Credenziali SQL**  
 Specificare il nome delle credenziali SQL che si desidera creare.  
  
## <a name="windows-azure-credentials"></a>Credenziali di Windows Azure  
 **Certificato di gestione**  
 Utilizzare questa opzione per specificare un certificato dall'archivio certificati locale corrispondente al certificato di gestione di Windows Azure. Per ulteriori informazioni sul certificato di gestione di Windows Azure, vedere [Creare e caricare un certificato di gestione per Windows Azure](http://go.microsoft.com/fwlink/?LinkId=320781).  
  
 **Sottoscrizione**  
 Selezionare, digitare o incollare l'ID sottoscrizione di Windows Azure corrispondente al certificato di gestione dall'archivio certificati locale.  
  
 **Profilo di pubblicazione**  
 Utilizzare questa opzione se si dispone di un profilo di pubblicazione scaricato nel computer. Se si utilizza questa opzione, l'ID sottoscrizione e il certificato vengono inseriti automaticamente.  
  
> [!CAUTION]  
>  SQL Server supporta attualmente la versione del profilo di pubblicazione 2.0. Per scaricare la versione supportata del profilo di pubblicazione, vedere [Download del profilo di pubblicazione 2.0](http://go.microsoft.com/fwlink/?LinkId=396421).  
  
## <a name="storage-account"></a>Account di archiviazione  
 Selezionare l'account di archiviazione da utilizzare per archiviare i file di backup.  
  
  