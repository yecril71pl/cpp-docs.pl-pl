---
title: Podsumowanie tokenów
ms.date: 11/04/2016
ms.assetid: 2978cbf6-e66e-46fc-9938-caa052f2ccf7
ms.openlocfilehash: 4fdc1cf4c4e5a89cc9ecf029e64b6eb5422cd6a3
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62345139"
---
# <a name="summary-of-tokens"></a>Podsumowanie tokenów

*token*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*keyword*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*Identyfikator*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*Stałe*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*literał ciągu*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*Operator*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*znak interpunkcyjny*

*Przetwarzanie wstępne token*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*header-name*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*Identyfikator*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*numer strony*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*Stała znakowa*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*literał ciągu*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*znak interpunkcyjny — operator*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;każdy znak niebędący odstępem, który nie może być jedną z powyższych

*header-name*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**\<**  *PATH-spec*  **>**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**"***specyfikacji ścieżki***"**

*path-spec*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;Ścieżka pliku prawne

*numer strony*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*digit*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**.** *digit*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*pp-number* *digit* <br/>
&nbsp;&nbsp;&nbsp;&nbsp;*numer strony* *nie cyfrą*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*numer strony***e***logowania*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*numer strony***E***logowania*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*numer strony* **.**

## <a name="see-also"></a>Zobacz także

[Gramatyka leksykalna](../c-language/lexical-grammar.md)
