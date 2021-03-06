---
title: Sys.external_language_files (Transact-SQL) - SQL Server | Microsoft Docs
ms.custom: ''
ms.date: 05/22/2019
ms.prod: sql
ms.reviewer: dphansen
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- external_languages
- external_languages_TSQL
- sys.external_languages
- sys.external_languages_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sys.external_languages catalog view
author: nelgson
ms.author: negust
manager: cgronlun
monikerRange: '>=sql-server-ver15||=sqlallproducts-allversions'
ms.openlocfilehash: 0d1325311ef0b708f5a3abd5f4494e099863efc2
ms.sourcegitcommit: be09f0f3708f2e8eb9f6f44e632162709b4daff6
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/21/2019
ms.locfileid: "65995089"
---
# <a name="sysexternallanguagefiles-transact-sql"></a>Sys.external_language_files (Transact-SQL)
[!INCLUDE[tsql-appliesto-ssver15-xxxx-xxxx-xxx](../../includes/tsql-appliesto-ssver15-xxxx-xxxx-xxx.md)]

Questa vista del catalogo fornisce un elenco dei file di estensione di linguaggio esterno nel database. **R** e **Python** sono nomi riservati e nessun linguaggio esterno può essere creato con tali nomi specifici.

Quando viene creato un linguaggio esterno da un file_spec, l'estensione stessa e le relative proprietà sono elencate in questa visualizzazione. Questa vista contiene una voce per ogni linguaggio, per ogni sistema operativo.

## <a name="sysexternallanguages"></a>sys.external_languages

Sys.external_language_files la vista del catalogo include una riga per ogni estensione del linguaggio esterna nel database. Parametri

|Nome colonna |Tipo di dati | Descrizione|
|------|------|------|
|external_language_id |INT | ID della lingua esterna|
|content|varbinary(max) |Contenuto del file di estensione del linguaggio esterno|
|file_name|nvarchar(266)|Nome del file di estensione del linguaggio|
|Piattaforma|TINYINT|ID della piattaforma host in cui è installato SQL Server|
|platform_desc |nvarchar(60)|Nome della piattaforma dell'host. I valori validi sono 'WINDOWS', 'LINUX'.|
|parameters|nvarchar(4000)|Linguaggio esterno prameters|
|environment_variables |nvarchar(4000)|Variabili di ambiente di linguaggio esterno|

## <a name="see-also"></a>Vedere anche  

+ [sys.external_languages](sys-external-languages-transact-sql.md)  
+ [CREAZIONE DI LINGUAGGIO ESTERNO](../../t-sql/statements/create-external-language-transact-sql.md)  
