---
title: Podsumowanie dotyczące stałych
ms.date: 11/04/2016
helpviewer_keywords:
- constants, C
ms.assetid: 4158234c-e189-4e25-970f-52a04bc6380a
ms.openlocfilehash: f927d977d818bed28c5fd7392f7933cd1a63ced3
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62157750"
---
# <a name="summary-of-constants"></a>Podsumowanie dotyczące stałych

*stałe*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*Floating point — stała*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*integer-constant*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*Stała wyliczenia*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*Stała znakowa*

*Floating point-constant*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*ułamkowe — stała* *część wykładnik*<sub>zoptymalizowany pod kątem</sub> *liczb zmiennoprzecinkowych sufiks*<sub>zoptymalizowany pod kątem</sub><br/>
&nbsp;&nbsp;&nbsp;&nbsp;*digit-sequence* *exponent-part* *floating-suffix*<sub>opt</sub>

*Stała ułamkowe*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*sekwencja cyfr*<sub>zoptymalizowany pod kątem</sub> **.** *digit-sequence*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*sekwencja cyfr*  **.**

*wykładnik część*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**e** *logowania*<sub>zoptymalizowany pod kątem</sub> *sekwencję cyfr*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**e** *logowania*<sub>zoptymalizowany pod kątem</sub> *sekwencję cyfr*

*znak*: jeden z<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**+ -**

*digit-sequence*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*digit*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*digit-sequence* *digit*

*sufiks liczb zmiennoprzecinkowych*: jeden z<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**f, g F, G**

*stała całkowita*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*decimal-constant* *integer-suffix*<sub>opt</sub><br/>
&nbsp;&nbsp;&nbsp;&nbsp;*plik binarny constant* *integer-suffix*<sub>zoptymalizowany pod kątem</sub><br/>
&nbsp;&nbsp;&nbsp;&nbsp;*octal-constant* *integer-suffix*<sub>opt</sub><br/>
&nbsp;&nbsp;&nbsp;&nbsp;*hexadecimal-constant* *integer-suffix*<sub>opt</sub>

*decimal-constant*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*nonzero-digit*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*decimal-constant* *digit*

*plik binarny constant*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**0b** *cyfra binarna*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**0b** *cyfra binarna*

*stałej ósemkowej*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**0**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*octal-constant* *octal-digit*

*hexadecimal-constant*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**0x**  *hexadecimal-digit*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**0X**  *hexadecimal-digit*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*hexadecimal-constant* *hexadecimal-digit*

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
&nbsp;&nbsp;&nbsp;&nbsp;**'** *c-char-sequence* **'**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**L'** *c-char-sequence* **'**

*integer-suffix*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*unsigned-suffix* *long-suffix*<sub>opt</sub><br/>
&nbsp;&nbsp;&nbsp;&nbsp;*long-suffix* *unsigned-suffix*<sub>opt</sub>

*c-char-sequence*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*c-char*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*c-char-sequence* *c-char*

*c-char*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;Każdy członek znak źródłowy zestawu z wyjątkiem pojedynczego cudzysłowu (**"**), ukośnika odwrotnego (**\\**), lub sekwencje znaków nowego wiersza

*Sekwencja unikowa*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*simple-escape-sequence*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*octal-escape-sequence*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*hexadecimal-escape-sequence*

*proste sekwencje*: jeden z<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**\a \b \f \n \r \t \v**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**\\' \\" \\\ \\?**

*octal-escape-sequence*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**\\** *octal-digit*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**\\** *cyfrą systemu ósemkowego* *cyfrą ósemkową*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**\\** *octal-digit* *octal-digit* *octal-digit*

*hexadecimal-escape-sequence*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**\x** *hexadecimal-digit*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*hexadecimal-escape-sequence* *hexadecimal-digit*

## <a name="see-also"></a>Zobacz także

[Gramatyka leksykalna](../c-language/lexical-grammar.md)<br/>
