---
title: Configurare un firewall per l'accesso FILESTREAM | Microsoft Docs
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: filestream
ms.topic: conceptual
helpviewer_keywords:
- Windows Firewall [Database Engine], FILESTREAM
- FILESTREAM [SQL Server], Windows Firewall
ms.assetid: fc52007f-c26f-4f8e-b9d8-55a7978f4d56
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 6be07fffa636a2cdc51197916d2bdf218cdea289
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62920207"
---
# <a name="configure-a-firewall-for-filestream-access"></a>Configurare un firewall per l'accesso FILESTREAM
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  Per utilizzare FILESTREAM in un ambiente protetto da firewall, il client e il serve devono essere entrambi in grado di risolvere nomi DNS nel server in cui sono presenti i file FILESTREAM. Per FILESTREAM è necessario che le porte 139 e 445 di condivisione file di Windows siano aperte.  
  
### <a name="to-open-the-windows-file-sharing-ports-on-a-computer-that-is-running-windows-7"></a>Per aprire le porte di condivisione file di Windows in un computer che esegue Windows 7  
  
1.  Nel Pannello di controllo aprire **Windows Firewall**.  
  
2.  Nel riquadro sinistro scegliere **Impostazioni avanzate**. Se viene richiesta una password di amministratore o una conferma, digitare la password o fornire la conferma.  
  
3.  Nel riquadro sinistro della finestra di dialogo **Windows Firewall con sicurezza avanzata** fare clic su **Regole connessioni in entrata**, quindi scegliere **Nuova regola**nel riquadro destro.  
  
4.  Seguire le istruzioni della Creazione guidata nuova regola connessioni in entrata per aggiungere la porta TCP 139.  
  
5.  Ripetere il passaggio precedente per aggiungere la porta TCP 445.  
  
6.  Chiudere la finestra di dialogo **Windows Firewall con sicurezza avanzata** .  
  
  
