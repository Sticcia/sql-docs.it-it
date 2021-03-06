---
title: SQL Server Management Studio - Dati di diagnostica e utilizzo (SSMS) | Microsoft Docs
ms.custom: ''
ms.date: 04/16/2019
ms.prod: sql
ms.prod_service: sql-tools
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
ms.assetid: c28ffa44-7b8b-4efa-b755-c7a3b1c11ce4
author: markingmyname
ms.author: maghan
manager: craigg
ms.openlocfilehash: 0810533a3488043ef4b3d8db9c0de4f3174b4ba8
ms.sourcegitcommit: bb5484b08f2aed3319a7c9f6b32d26cff5591dae
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/06/2019
ms.locfileid: "65102623"
---
# <a name="local-audit-for-ssms-usage-and-diagnostic-data-collection"></a>Controllo locale per la raccolta di dati di diagnostica e utilizzo di SSMS
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

SQL Server Management Studio (SSMS) include funzionalità abilitate per Internet che consentono di raccogliere e inviare a Microsoft dati anonimi di diagnostica e di utilizzo delle funzionalità. SSMS può raccogliere informazioni standard sul computer e informazioni relative all'uso e alle prestazioni che possono venire trasmesse a Microsoft e analizzate al fine di migliorare la qualità, la sicurezza e l'affidabilità di SSMS. Microsoft non raccoglie il nome, l'indirizzo o altre informazioni di contatto degli utenti. Per informazioni dettagliate, vedere l'[Informativa sulla privacy di Microsoft](https://privacy.microsoft.com/privacystatement) e [Supplemento alla privacy di SQL Server](https://go.microsoft.com/fwlink/?LinkID=868444).

## <a name="audit-feature-usage-and-diagnostic-data"></a>Controllare i dati di diagnostica e utilizzo delle funzionalità

Per vedere i dati relativi all'utilizzo delle funzionalità raccolti da SSMS, seguire questa procedura:

1.  Avviare SSMS.
2.  Fare clic su **Visualizza** e quindi su **Output** nel menu principale per visualizzare la finestra **Output**. 
3.  Quando la finestra **Output** è visualizzata, scegliere **Telemetria** dal menu **Mostra output di**.

Quando si usa SSMS per interagire con i database, la finestra **Output** mostra i dati raccolti.

## <a name="enable-or-disable-usage-and-diagnostic-data-collection-in-ssms"></a>Abilitare o disabilitare la raccolta di dati di diagnostica e utilizzo in SSMS

Per acconsentire esplicitamente alla raccolta di dati di utilizzo per SQL Server Management Studio o per rifiutare in modo esplicito:

- Per SQL Server Management Studio 17:

  `Subkey = HKEY_CURRENT_USER\Software\Microsoft\SQL Server Management Studio\14.0`

  Nome RegEntry = `UserFeedbackOptIn`

  Tipo di voce `DWORD`: `0` rifiuto esplicito; `1` consenso esplicito

  SSMS 17.x si basa inoltre sulla shell di Visual Studio 2015 e l'installazione di Visual Studio consente di abilitare i commenti e suggerimenti utenti per impostazione predefinita.  

  Per configurare Visual Studio per disabilitare i commenti e suggerimenti dei clienti nei singoli computer, modificare il valore della sottochiave del Registro di sistema seguente in una stringa `0`: `HKEY_LOCAL_MACHINE\Software\Policies\Microsoft\VisualStudio\SQM OptIn`

  Modificare ad esempio la sottochiave nella stringa seguente:  
  `HKEY_LOCAL_MACHINE\Software\Policies\Microsoft\VisualStudio\SQM OptIn `=` 0`

  I Criteri di gruppo basati sul Registro di sistema per queste sottochiavi del Registro di sistema vengono rispettati dalla raccolta di dati di diagnostica e utilizzo di SQL Server 2017.

- Per SQL Server Management Studio 18:

  `Subkey = HKEY_CURRENT_USER\Software\Microsoft\SQL Server Management Studio\18.0_IsoShell`

  Nome RegEntry = `UserFeedbackOptIn`

  Tipo di voce `DWORD`: `0` rifiuto esplicito; `1` consenso esplicito

## <a name="see-also"></a>Vedere anche

- [Configurare la raccolta di dati di diagnostica e utilizzo per SQL Server](../sql-server/usage-and-diagnostic-data-configuration-for-sql-server.md)
- [Controllo locale per la raccolta di dati di diagnostica e utilizzo di SQL Server](http://msdn.microsoft.com/library/mt743085.aspx)