---
title: Configurare il controllo accessi (SQL Server Management Studio) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: sql-tools
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- auditing [SQL Server]
- audits [SQL Server], logins
- logins [SQL Server], auditing
ms.assetid: 16961116-57ac-4eef-8037-791b26ade548
author: markingmyname
ms.author: maghan
manager: craigg
ms.openlocfilehash: 1ce5c0323d98e2b8f05813513b3a2f44444a6695
ms.sourcegitcommit: bb5484b08f2aed3319a7c9f6b32d26cff5591dae
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/06/2019
ms.locfileid: "65102775"
---
# <a name="configure-login-auditing-sql-server-management-studio"></a>Configurazione del controllo accessi (SQL Server Management Studio)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]
In questo argomento viene descritto come configurare controllo di accesso in [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)] per eseguire il monitoraggio dell'attività di accesso del [!INCLUDE[ssDEnoversion](../includes/ssdenoversion_md.md)]. È possibile configurare il controllo accessi per scrivere nel log degli errori quando si verificano gli eventi riportati di seguito.  
  
-   Accessi non riusciti  
  
-   Accessi riusciti  
  
-   Accessi riusciti e non riusciti  
  
Per rendere effettiva questa opzione, è necessario riavviare [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] .  
  
## <a name="SSMSProcedure"></a>Utilizzo di SQL Server Management Studio  
  
#### <a name="to-configure-login-auditing"></a>Per configurare il controllo accessi  
  
1.  In [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)]connettersi a un'istanza del [!INCLUDE[ssDEnoversion](../includes/ssdenoversion_md.md)] tramite Esplora oggetti.  
  
2.  In Esplora oggetti fare clic con il pulsante destro del mouse sul nome del server e quindi scegliere **Proprietà**.  
  
3.  Nella pagina **Sicurezza** selezionare l'opzione desiderata in **Controllo accessi** e chiudere la pagina **Proprietà server** .  
  
4.  In Esplora oggetti fare clic con il pulsante destro del mouse sul nome del server e scegliere **Riavvia**.  
  
