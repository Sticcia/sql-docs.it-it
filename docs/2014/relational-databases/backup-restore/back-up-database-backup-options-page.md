---
title: Backup database (pagina Opzioni di backup) | Microsoft Docs
ms.custom: ''
ms.date: 03/07/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: backup-restore
ms.topic: conceptual
f1_keywords:
- sql12.swb.backupdatabase.options.f1
- swb.backupdatabase.options.f1
ms.assetid: df0ddcdb-c94e-472b-b786-469ae8117b93
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: c8030a0005f0f5b949a3eecd12d73f3a3aa709c2
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62876864"
---
# <a name="back-up-database-backup-options-page"></a>Backup database (pagina Opzioni di backup)
  Utilizzare la pagina  **Opzioni di backup** della finestra di dialogo **Backup database** per visualizzare o modificare le opzioni di backup del database.  
  
 **Per creare un backup utilizzando SQL Server Management Studio**  
  
-   [Creazione di un backup completo del database &#40;SQL Server&#41;](create-a-full-database-backup-sql-server.md)  
  
-   [Creare un backup differenziale del database &#40;SQL Server&#41;](create-a-differential-database-backup-sql-server.md)  
  
> [!IMPORTANT]  
>  È possibile definire un piano di manutenzione database per creare backup di database. Per altre informazioni, vedere [Piani di manutenzione](../maintenance-plans/maintenance-plans.md) e [Usare la Creazione guidata piano di manutenzione](../maintenance-plans/use-the-maintenance-plan-wizard.md).  
  
> [!NOTE]  
>  Quando si specifica un'attività di backup usando [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], è possibile generare lo script [!INCLUDE[tsql](../../includes/tsql-md.md)][BACKUP](/sql/t-sql/statements/backup-transact-sql) corrispondente facendo clic sul pulsante **Script** e quindi selezionando una destinazione per lo script.  
  
## <a name="options"></a>Opzioni  
  
### <a name="backup-set"></a>Set di backup  
 Le opzioni del pannello **Set di backup** consentono di specificare informazioni facoltative sul set di backup creato dall'operazione di backup.  
  
 **Name**  
 Consente di specificare il nome del set di backup. Il sistema suggerisce automaticamente un nome predefinito in base al nome del database e al tipo di backup.  
  
 Per informazioni sui set di backup, vedere [Set di supporti, gruppi di supporti e set di backup &#40;SQL Server&#41;](media-sets-media-families-and-backup-sets-sql-server.md).  
  
 **Descrizione**  
 Consente di immettere una descrizione del set di backup.  
  
 **Scadenza set di backup**  
 Scegliere una delle opzioni di scadenza seguenti. Questa opzione è disabilitata se è stato scelto **URL** come destinazione di backup.  
  
|||  
|-|-|  
|**After**|Consente di specificare il numero di giorni che devono trascorrere prima che il set di backup scada e possa venire sovrascritto. È possibile impostare un valore compreso nell'intervallo da 0 a 99999 giorni. L'impostazione del valore 0 giorni indica che il set di backup non ha scadenza.<br /><br /> Il valore predefinito per la scadenza del backup corrisponde al valore impostato nell'opzione **Periodo di memorizzazione predefinito supporti di backup (giorni)** . Per accedere a questa opzione fare clic con il pulsante destro del mouse sul nome del server in Esplora oggetti e selezionare **Proprietà**. Fare quindi clic sulla pagina **Impostazioni database** della finestra di dialogo **Proprietà server** .|  
|**On**|Consente di specificare la data di scadenza del set di backup per la possibile sovrascrittura.|  
  
### <a name="compression"></a>Compressione  
 [!INCLUDE[ssEnterpriseEd10](../../../includes/ssenterpriseed10-md.md)] (o versioni successive) supporta la [compressione dei backup](backup-compression-sql-server.md).  
  
 **Imposta compressione backup**  
 In [!INCLUDE[ssEnterpriseEd10](../../../includes/ssenterpriseed10-md.md)] o versione successiva selezionare uno dei seguenti valori di compressione dei backup:  
  
|||  
|-|-|  
|**Utilizza l'impostazione predefinita del server**|Fare clic su questa opzione per utilizzare l'impostazione predefinita a livello di server.<br /><br /> Questa impostazione predefinita è specificata dall'opzione di configurazione del server **Valore predefinito di compressione backup** . Per informazioni su come visualizzare l'impostazione corrente di questa opzione, vedere [Visualizzare o configurare l'opzione di configurazione del server backup compression default](../../database-engine/configure-windows/view-or-configure-the-backup-compression-default-server-configuration-option.md).|  
|**Comprimi backup**|Fare clic su questa opzione per comprimere il backup, indipendentemente dall'impostazione predefinita a livello di server.<br /><br /> **\*\* Importante \*\*** Per impostazione predefinita, la compressione aumenta significativamente l'uso della CPU e la CPU aggiuntiva usata dal processo di compressione può avere un impatto negativo sulle operazioni simultanee. Potrebbe pertanto essere necessario creare backup compressi con priorità bassa in una sessione in cui l'utilizzo della CPU è limitato da [Resource Governor](../resource-governor/resource-governor.md). Per ulteriori informazioni, vedere [Utilizzo di Resource Governor per limitare l'utilizzo della CPU da parte della compressione dei backup &#40;Transact-SQL&#41;](use-resource-governor-to-limit-cpu-usage-by-backup-compression-transact-sql.md).|  
|**Non comprimere il backup**|Fare clic su questa opzione per creare un backup non compresso, indipendentemente dall'impostazione predefinita a livello di server.|  
  
### <a name="encryption"></a>Crittografia  
 Per creare un backup crittografato, selezionare la casella di controllo **Crittografa backup** . Selezionare un algoritmo di crittografia da utilizzare per il passaggio di crittografia e specificare un certificato o una chiave asimmetrica da un elenco di chiavi asimmetriche o di certificati esistenti. Gli algoritmi di crittografia disponibili sono:  
  
-   AES 128  
  
-   AES 192  
  
-   AES 256  
  
-   Triple DES  
  
> [!TIP]  
>  L'opzione di crittografia è disabilitata se si è scelto di eseguire l'accodamento a un set di backup esistente.  
>   
>  È consigliabile eseguire il backup del certificato o delle chiavi e archiviarli in un percorso diverso da quello utilizzato per il backup crittografato.  
>   
>  Sono supportate solo le chiavi che si trovano in Extensible Key Management (EKM).  
  
## <a name="see-also"></a>Vedere anche  
 [BACKUP &#40;Transact-SQL&#41;](/sql/t-sql/statements/backup-transact-sql)   
 [Backup di un log delle transazioni &#40;SQL Server&#41;](back-up-a-transaction-log-sql-server.md)   
 [Backup di file e filegroup &#40;SQL Server&#41;](back-up-files-and-filegroups-sql-server.md)   
 [Esecuzione del backup del log delle transazioni quando il database è danneggiato &#40;SQL Server&#41;](back-up-the-transaction-log-when-the-database-is-damaged-sql-server.md)  
  
  
