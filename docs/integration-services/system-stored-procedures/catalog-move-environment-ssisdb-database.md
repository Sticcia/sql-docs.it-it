---
title: catalog.move_environment (database SSISDB) | Microsoft Docs
ms.custom: ''
ms.date: 03/03/2017
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.technology: integration-services
ms.topic: language-reference
ms.assetid: b3fb5242-3c4c-4a87-b3e5-beb22fbab053
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: 04ced3ce325755f465aaf203f08ed08e38d99f62
ms.sourcegitcommit: fd71d04a9d30a9927cbfff645750ac9d5d5e5ee7
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/16/2019
ms.locfileid: "65716163"
---
# <a name="catalogmoveenvironment-ssisdb-database"></a>catalog.move_environment (database SSISDB)

[!INCLUDE[ssis-appliesto](../../includes/ssis-appliesto-ssvrpluslinux-asdb-asdw-xxx.md)]


[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  Viene spostato un ambiente da una cartella a un'altra all'interno del catalogo di [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)].  
  
## <a name="syntax"></a>Sintassi  
  
```sql  
catalog.move_environment [ @source_folder = ] source_folder  
    , [ @environment_name = ] environment_name  
    , [ @destination_folder = ] destination_folder  
```  
  
## <a name="arguments"></a>Argomenti  
 [ @source_folder = ] *source_folder*  
 Nome della cartella di origine, in cui si trova l'ambiente prima dello spostamento. *source_folder* è di tipo **nvarchar(128)**.  
  
 [ @environment_name = ] *environment_name*  
 Nome dell'ambiente che deve essere spostato. *environment_name* è di tipo **nvarchar(128)**.  
  
 [ @destination_folder = ] *destination_folder*  
 Nome della cartella di destinazione, in cui si trova l'ambiente dopo lo spostamento. *destination_folder* è di tipo **nvarchar(128)**.  
  
## <a name="return-code-value"></a>Valore del codice restituito  
 0 (esito positivo)  
  
## <a name="result-sets"></a>Set di risultati  
 None  
  
## <a name="permissions"></a>Autorizzazioni  
 Per questa stored procedure è necessaria una delle autorizzazioni seguenti:  
  
-   Autorizzazioni READ e MODIFY sull'ambiente  
  
-   Appartenenza al ruolo del database **ssis_admin**  
  
-   Appartenenza al ruolo del server **sysadmin**  
  
## <a name="errors-and-warnings"></a>Errori e avvisi  
 Nell'elenco seguente vengono descritte alcune condizioni che possono generare un errore o un avviso:  
  
-   Ambiente inesistente nella cartella di origine  
  
-   Ambiente con stesso nome già presente nella cartella di destinazione  
  
-   Utente senza autorizzazioni appropriate.  
  
## <a name="remarks"></a>Remarks  
 I riferimenti all'ambiente dai progetti non seguono l'ambiente durante lo spostamento, pertanto è necessario aggiornarli di conseguenza. Questa stored procedure verrà completata anche se i riferimenti all'ambiente vengono interrotti spostando un ambiente. I riferimenti all'ambiente devono essere aggiornati dopo il completamento di questa stored procedure.  
  
> [!NOTE]  
>  Un progetto può disporre di riferimenti all'ambiente relativi o assoluti. I riferimenti relativi fanno riferimento all'ambiente in base al nome. Per tali riferimenti è necessario che l'ambiente si trovi nella stessa cartella del progetto. I riferimenti assoluti fanno riferimento all'ambiente in base al nome e alla cartella. Tali riferimenti fanno riferimento agli ambienti che si trovano in una cartella diversa da quella del progetto.  
  
  
