---
title: Grammatica formale per Shape | Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- shape commands [ADO], shape grammar
- data shaping [ADO], shape grammar
ms.assetid: ea691475-0f03-4abe-a785-b77e77712d1d
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 3b26eaeb804f8d92a7122814641cadf5889b77b8
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "63161413"
---
# <a name="formal-shape-grammar"></a>Grammatica formale per Shape
Questa è la grammatica formale per la creazione di qualsiasi comando shape:  
  
-   I termini grammaticali obbligatori sono stringhe di testo delimitate da parentesi quadre ("<>").  
  
-   Termini facoltativi sono delimitati da parentesi quadre ("[]").  
  
-   Alternative sono indicate da una barra ("&#124;").  
  
-   Ripetuto alternative sono indicate dai puntini di sospensione (..."").  
  
-   *Alfa* indica una stringa di caratteri alfabetici.  
  
-   *Cifra* indica una stringa di numeri.  
  
-   *Cifra Unicode* indica una stringa di cifre unicode.  
  
 Tutte le altre condizioni sono valori letterali.  
  
|Nome|Definizione|  
|----------|----------------|  
|\<shape-command>|SHAPE [\<table-exp> [[AS] \<alias>]][\<shape-action>]|  
|\<table-exp>|{\<provider-command-text>} &#124;<br /><br /> (\<shape-command>) &#124;<br /><br /> TABELLA \<racchiusi tra virgolette-name >&#124;<br /><br /> \<quoted-name>|  
|\<shape-action>|APPEND \<elenco di campi con alias >&#124;<br /><br /> COMPUTE \<aliased-field-list> [BY \<field-list>]|  
|\<aliased-field-list>|\<aliased-field> [, \<aliased-field...>]|  
|\<aliased-field>|\<field-exp> [[AS] \<alias>]|  
|\<field-exp>|(\<relation-exp>) &#124;<br /><br /> \<calculated-exp> &#124;<br /><br /> \<aggregate-exp> &#124;<br /><br /> \<new-exp>|  
|<relation_exp>|\<table-exp> [[AS] \<alias>]<br /><br /> RELATE \<relazione-cond-list >|  
|\<relation-cond-list>|\<relation-cond> [, \<relation-cond>...]|  
|\<relation-cond>|\<campo-name > a \<figlio-ref >|  
|\<child-ref>|\<field-name> &#124;<br /><br /> PARAMETRO \<-ref param >|  
|\<param-ref>|\<number>|  
|\<field-list>|\<field-name> [, \<field-name>]|  
|\<aggregate-exp>|SUM(\<qualified-field-name>) &#124;<br /><br /> AVG(\<qualified-field-name>) &#124;<br /><br /> MIN(\<qualified-field-name>) &#124;<br /><br /> MAX(\<qualified-field-name>) &#124;<br /><br /> COUNT(\<qualified-alias> &#124; \<qualified-name>) &#124;<br /><br /> STDEV(\<qualified-field-name>) &#124;<br /><br /> QUALSIASI (\<qualified-campo-name >)|  
|\<calculated-exp>|CALC(\<expression>)|  
|\<qualified-field-name>|\<alias>.[\<alias>...]\<field-name>|  
|\<alias>|\<quoted-name>|  
|\<field-name>|\<quoted-name> [[AS] \<alias>]|  
|\<quoted-name>|"\<string>" &#124;<br /><br /> '\<string>' &#124;<br /><br /> [\<string>] &#124;<br /><br /> \<Nome >|  
|\<qualified-name>|alias[.alias...]|  
|\<Nome >|alpha [ alpha &#124; digit &#124; _ &#124; # &#124; : &#124; ...]|  
|\<number>|cifra [numero]|  
|\<new-exp>|NUOVE \<-tipo di campo > [(\<numero > [, \<numero >])]|  
|\<field-type>|Un tipo di dati OLE DB o ADO.|  
|\<string>|Unicode-char [-char unicode...]|  
|\<expression>|Un'espressione Visual Basic le applicazioni cui gli operandi sono altre colonne non CALC nella stessa riga.|  
  
## <a name="see-also"></a>Vedere anche  
 [Accesso alle righe in un Recordset gerarchico](../../../ado/guide/data/accessing-rows-in-a-hierarchical-recordset.md)   
 [Panoramica del Data Shaping](../../../ado/guide/data/data-shaping-overview.md)   
 [Provider necessari per il Data Shaping](../../../ado/guide/data/required-providers-for-data-shaping.md)   
 [Clausola APPEND per Shape](../../../ado/guide/data/shape-append-clause.md)   
 [Comandi Shape in generale](../../../ado/guide/data/shape-commands-in-general.md)   
 [Clausola COMPUTE di Shape](../../../ado/guide/data/shape-compute-clause.md)   
 [Funzioni di Visual Basic, Applications Edition](../../../ado/guide/data/visual-basic-for-applications-functions.md)
