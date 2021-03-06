---
title: Rimuovere un listener del gruppo di disponibilità (SQL Server) | Microsoft Docs
ms.custom: ''
ms.date: 05/17/2016
ms.prod: sql
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
f1_keywords:
- sql13.swb.availabilitygroup.removeaglistener.default.f1
helpviewer_keywords:
- Availability Groups [SQL Server], listeners
ms.assetid: fd9bba9a-d29f-4c23-8ecd-aaa049ed5f1b
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 3fb1c490f8a20da4df987c003a4aa1d89619ed94
ms.sourcegitcommit: 179ab0e55f918f58a18c43af076130f4ac3decd6
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/19/2019
ms.locfileid: "62826251"
---
# <a name="remove-an-availability-group-listener-sql-server"></a>Rimuovere un listener del gruppo di disponibilità (SQL Server)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  Questo argomento illustra come rimuovere un listener da un gruppo di disponibilità AlwaysOn usando [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)], [!INCLUDE[tsql](../../../includes/tsql-md.md)]o PowerShell in [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)].  
  
  
##  <a name="Prerequisites"></a> Prerequisiti  
  
-   È necessario essere connessi all'istanza del server che ospita la replica primaria.  
  
##  <a name="Recommendations"></a> Indicazioni  
 Prima di eliminare un listener del gruppo di disponibilità, si consiglia di verificare che non sia utilizzato da alcuna applicazione.  
 
  
##  <a name="Permissions"></a> Autorizzazioni  
 È necessaria l'autorizzazione ALTER AVAILABILITY GROUP nel gruppo di disponibilità, l'autorizzazione CONTROL AVAILABILITY GROUP, l'autorizzazione ALTER ANY AVAILABILITY GROUP o l'autorizzazione CONTROL SERVER.  
  
##  <a name="SSMSProcedure"></a> Utilizzo di SQL Server Management Studio  
 **Per rimuovere un listener del gruppo di disponibilità**  
  
1.  In Esplora oggetti connettersi all'istanza del server in cui viene ospitata la replica primaria e fare clic sul nome del server per espandere il relativo albero.  
  
2.  Espandere il nodo **Disponibilità elevata AlwaysOn** e il nodo **Gruppi di disponibilità**.  
  
3.  Espandere il nodo del gruppo di disponibilità ed espandere il nodo **Listener gruppo di disponibilità** .  
  
4.  Fare clic con il pulsante destro del mouse sul listener da rimuovere, quindi scegliere il comando **Elimina** .  
  
5.  Verrà aperta la finestra di dialogo **Rimuovi listener dal gruppo disponibilità** . Per ulteriori informazioni, vedere [Rimuovi listener dal gruppo di disponibilità](#AgListenerPropertiesDialog), più avanti in questo argomento.  
  
###  <a name="AgListenerPropertiesDialog"></a> Rimuovi listener dal gruppo disponibilità (finestra di dialogo)  
 **Nome**  
 Nome del listener da rimuovere.  
  
 **Result**  
 Viene visualizzato un collegamento, **Esito positivo** o **Errore**, su cui è possibile fare clic per altre informazioni.  
  
##  <a name="TsqlProcedure"></a> Uso di Transact-SQL  
 **Per rimuovere un listener del gruppo di disponibilità**  
  
1.  Connettersi all'istanza del server che ospita la replica primaria.  
  
2.  Utilizzare l'istruzione [ALTER AVAILABILITY GROUP](../../../t-sql/statements/alter-availability-group-transact-sql.md) , come indicato di seguito:  
  
     ALTER AVAILABILITY GROUP *group_name* REMOVE LISTENER **'**_dns_name_**'**  
  
     dove *group_name* è il nome del gruppo di disponibilità e *dns_name* è il nome DNS del listener del gruppo di disponibilità.  
  
     Nell'esempio seguente viene eliminato il listener del gruppo di disponibilità `AccountsAG` . Il nome DNS è AccountsAG_Listener.  
  
    ```  
    ALTER AVAILABILITY GROUP AccountsAG REMOVE LISTENER 'AccountsAG_Listener';  
    ```  
  
##  <a name="PowerShellProcedure"></a> Utilizzo di PowerShell  
 **Per rimuovere un listener del gruppo di disponibilità**  
  
1.  Impostare il valore predefinito (**cd**) sull'istanza del server che ospita la replica primaria.  
  
2.  Usare il cmdlet **Remove-Item** predefinito per rimuovere un listener. Ad esempio, il seguente comando rimuove il listener `MyListener` dal gruppo di disponibilità `MyAg`.  
  
    ```  
    Remove-Item `   
    SQLSERVER:\Sql\PrimaryServer\InstanceName\AvailabilityGroups\MyAg\AGListeners\MyListener  
    ```  
  
    > [!NOTE]  
    >  Per visualizzare la sintassi di un cmdlet, usare il cmdlet **Get-Help** nell'ambiente PowerShell di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] . Per altre informazioni, vedere [Get Help SQL Server PowerShell](../../../relational-databases/scripting/get-help-sql-server-powershell.md).  
  
##  <a name="RelatedTasks"></a> Attività correlate  
  
-   [Creare o configurare un listener del gruppo di disponibilità &#40;SQL Server&#41;](../../../database-engine/availability-groups/windows/create-or-configure-an-availability-group-listener-sql-server.md)  
  
-   [Visualizzare le proprietà del listener del gruppo di disponibilità &#40;SQL Server&#41;](../../../database-engine/availability-groups/windows/view-availability-group-listener-properties-sql-server.md)  
  
## <a name="see-also"></a>Vedere anche  
 [Panoramica di gruppi di disponibilità AlwaysOn &#40;SQL Server&#41;](../../../database-engine/availability-groups/windows/overview-of-always-on-availability-groups-sql-server.md)   
 [Listener del gruppo di disponibilità, connettività client e failover dell'applicazione &#40;SQL Server&#41;](../../../database-engine/availability-groups/windows/listeners-client-connectivity-application-failover.md)  
  
  
