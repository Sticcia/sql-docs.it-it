---
title: Appendix - 1 (MySQLToSQL) | Microsoft Docs
ms.prod: sql
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.technology: ssma
ms.topic: conceptual
ms.assetid: 2d22766d-ff09-420d-ae7c-13b443e28bd0
author: Shamikg
ms.author: Shamikg
manager: craigg
ms.openlocfilehash: 20cda553190074236f8cf50bb719a5c1e019e416
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "63253305"
---
# <a name="appendix---1-mysqltosql"></a>Appendice - 1 (MySQLToSQL)
Panoramica della Console SSMA opzioni riga di comando:  
  
|Sl. No.|Opzione|Obbligatorio?|Argomento parametro|Valori consentiti|  
|-----------|----------|-------------|-------------------|--------------------|  
|1|-s/script|Yes|scriptfile|Nome file XML valido.<br /><br />File di definizione di Script della console.|  
|2|-v/variable|No|variablevaluefile|Nome file XML valido.<br /><br />Se vengono usate nel file di script, è necessario specificare questo file.|  
|3|-c/serverconnection|no|serverconnectionfile|Nome file XML valido.<br /><br />Questo file contiene informazioni di connessione server.|  
|4|-x/xmloutput|No|xmloutputfile|Questa opzione indica l'output di console in formato XML. Se questa opzione non è specificata, l'output predefinito è in formato testo.<br /><br />Se non viene specificato xmloutputfile, output XML viene indirizzato a STDOUT.<br /><br />Xmloutputfile è il nome del file in cui viene scritto l'output della console in formato XML.|  
|5|-l/log|No|logfile|Nome file valido.|  
|6|-e/projectenvironment|No|projectenvironmentfolder|Nome di cartella valido che contiene file dell'ambiente di progetto SSMA.|  
|7|-p/securepassword|No|-un/aggiungere {< server_id > [,... n] &#124; tutti i} - c&#124;serverconnection < server-connection-file > [-v&#124;variabile di < variabile-valore-file >] [-o/sovrascriverà]<br /><br />o Gestione configurazione<br /><br />-un/aggiungere {< server_id > [,... n] &#124; tutti i} -s&#124;script < file di script > [-v&#124;variabile di < variabile-valore-file >] [-o/sovrascriverà]<br /><br />-r/Rimuovi {< server_id > [,... n] &#124; tutti}<br /><br />-l/list<br /><br />/ esportazione di e-{< server-id > [,... n] &#124; tutti i} < crittografati-password - file ><br /><br />-i / Importa {< server-id > [,... n] &#124; tutti i} < crittografati-password-file >|Se specificato, questa opzione non deve essere eseguita con qualsiasi altra opzione.<br /><br />server-id: Un ID univoco fornito per un server {string}<br /><br />file di connessione server: file di definizione del server (serverconnectionfile o scriptfile).<br /><br />file di valore variabile: È un file di definizione di variabile e usato nel file di connessione server.<br /><br />encrypted-password-file: È un file server di password crittografato con una specificata dall'utente-passphrase.|  
|8|-?|No|Non applicabile|Non applicabile|  
  
## <a name="see-also"></a>Vedere anche  
[Esecuzione della Console SSMA (MySQL)](https://msdn.microsoft.com/e3e9f7e4-0619-4861-a202-3d5d39953b26)  
  
