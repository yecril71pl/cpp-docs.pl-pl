---
title: Podsumowanie dotyczące stałych
ms.date: 11/04/2016
helpviewer_keywords:
- constants, C
ms.assetid: 4158234c-e189-4e25-970f-52a04bc6380a
ms.openlocfilehash: 1da2a7434ced7f38fa199e5911e01709983fda91
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50547865"
---
# <a name="summary-of-constants"></a>Podsumowanie dotyczące stałych

*stałe*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*Floating point — stała*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*stała całkowita*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*Stała wyliczenia*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*Stała znakowa*

*Floating point-constant*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*ułamkowe — stała* *część wykładnik*<sub>zoptymalizowany pod kątem</sub> *liczb zmiennoprzecinkowych sufiks*<sub>zoptymalizowany pod kątem</sub><br/>
&nbsp;&nbsp;&nbsp;&nbsp;*sekwencja cyfr* *część wykładnik* *liczb zmiennoprzecinkowych sufiks*<sub>zoptymalizowany pod kątem</sub>

*Stała ułamkowe*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*sekwencja cyfr*<sub>zoptymalizowany pod kątem</sub> **.** *sekwencja cyfr*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*sekwencja cyfr***.**

*wykładnik część*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**e** *logowania*<sub>zoptymalizowany pod kątem</sub> *sekwencję cyfr*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**e** *logowania*<sub>zoptymalizowany pod kątem</sub> *sekwencję cyfr*

*znak*: jeden z<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**+ -**

*sekwencja cyfr*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*cyfra*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*sekwencja cyfr* *cyfra*

*sufiks liczb zmiennoprzecinkowych*: jeden z<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**f, g F, G**

*stała całkowita*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*decimal-constant* *integer-suffix*<sub>opt</sub><br/>
&nbsp;&nbsp;&nbsp;&nbsp;*plik binarny constant* *integer-suffix*<sub>zoptymalizowany pod kątem</sub><br/>
&nbsp;&nbsp;&nbsp;&nbsp;*octal-constant* *integer-suffix*<sub>opt</sub><br/>
&nbsp;&nbsp;&nbsp;&nbsp;*hexadecimal-constant* *integer-suffix*<sub>opt</sub>

*decimal-constant*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*nonzero-digit*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*decimal-constant* *cyfra*

*plik binarny constant*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**0b** *cyfra binarna*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**0b** *cyfra binarna*

*stałej ósemkowej*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**0**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*stałej ósemkowej* *cyfrą ósemkową*

*stałą szesnastkową*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**0 x***cyfry szesnastkowe*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**0 X***cyfry szesnastkowe*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*stałą szesnastkową* *cyfry szesnastkowe*

*cyfry niezerowych*: jeden z<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**1 2 3 4 5 6 7 8 9**

*cyfrą systemu ósemkowego*: jeden z<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**0 1 2 3 4 5 6 7**

*cyfry szesnastkowe*: jeden z<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**0 1 2 3 4 5 6 7 8 9**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**b c d e f**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**A B C D E F**

*unsigned-suffix*: jeden z<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**u U**

*Long-suffix*: jeden z<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**l L**

*stałej znakowej*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**"** *c char sekwencji* **"**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**L "** *c char sekwencji* **"**

*integer-suffix*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*unsigned-suffix* *long-suffix*<sub>zoptymalizowany pod kątem</sub><br/>
&nbsp;&nbsp;&nbsp;&nbsp;*Long-suffix* *unsigned-suffix*<sub>zoptymalizowany pod kątem</sub>

*c char sekwencji*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*c-char*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*c char sekwencji* *c-char*

*c-char*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;Każdy członek znak źródłowy zestawu z wyjątkiem pojedynczego cudzysłowu (**"**), ukośnika odwrotnego (**\\**), lub sekwencje znaków nowego wiersza

*Sekwencja unikowa*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*proste sekwencje*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*ósemkowa sekwencja unikowa*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*szesnastkowe sekwencje*

*proste sekwencje*: jeden z<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**\a \b \f \n \r \t \v**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**\\' \\" \\\ \\?**

*ósemkowa sekwencja unikowa*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**\\** *cyfrą ósemkową*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**\\** *cyfrą systemu ósemkowego* *cyfrą ósemkową*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**\\** *cyfrą systemu ósemkowego* *cyfrą systemu ósemkowego* *cyfrą ósemkową*

*szesnastkowe sekwencje*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**\x** *cyfry szesnastkowe*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*szesnastkowe sekwencje* *cyfry szesnastkowe*

## <a name="see-also"></a>Zobacz też

[Gramatyka leksykalna](../c-language/lexical-grammar.md)<br/>
