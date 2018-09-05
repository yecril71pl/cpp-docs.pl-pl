---
title: Podsumowanie tokenów | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
ms.assetid: 2978cbf6-e66e-46fc-9938-caa052f2ccf7
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: e331661fc011fe0ab98a762f5c7081c35f06363c
ms.sourcegitcommit: 92dbc4b9bf82fda96da80846c9cfcdba524035af
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/05/2018
ms.locfileid: "43758482"
---
# <a name="summary-of-tokens"></a>Podsumowanie tokenów

*Token*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*Słowo kluczowe*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*Identyfikator*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*Stałe*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*literał ciągu*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*Operator*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*znak interpunkcyjny*

*Przetwarzanie wstępne token*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*Nazwa nagłówka*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*Identyfikator*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*numer strony*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*Stała znakowa*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*literał ciągu*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*znak interpunkcyjny — operator*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;każdy znak niebędący odstępem, który nie może być jedną z powyższych

*Nazwa nagłówka*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**\<**  *PATH-spec*  **>**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**"***specyfikacji ścieżki***"** 

*PATH-spec*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;Ścieżka pliku prawne

*numer strony*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*cyfra*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**.** *digit*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*numer strony* *cyfra* <br/>
&nbsp;&nbsp;&nbsp;&nbsp;*numer strony* *nie cyfrą*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*numer strony***e***logowania* <br/>
&nbsp;&nbsp;&nbsp;&nbsp;*numer strony***E***logowania* <br/>
&nbsp;&nbsp;&nbsp;&nbsp;*numer strony***.** 

## <a name="see-also"></a>Zobacz też

[Gramatyka leksykalna](../c-language/lexical-grammar.md)