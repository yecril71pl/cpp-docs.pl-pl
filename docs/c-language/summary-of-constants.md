---
title: Podsumowanie dotyczące stałych | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- constants, C
ms.assetid: 4158234c-e189-4e25-970f-52a04bc6380a
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 98b67bf6fd81ee611d99904931a825ee28448482
ms.sourcegitcommit: 9a0905c03a73c904014ec9fd3d6e59e4fa7813cd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/29/2018
ms.locfileid: "43217386"
---
# <a name="summary-of-constants"></a>Podsumowanie dotyczące stałych

*stałe*:  
&nbsp;&nbsp;&nbsp;&nbsp;*Floating point — stała*  
&nbsp;&nbsp;&nbsp;&nbsp;*stała całkowita*  
&nbsp;&nbsp;&nbsp;&nbsp;*Stała wyliczenia*  
&nbsp;&nbsp;&nbsp;&nbsp;*Stała znakowa*

*Floating point-constant*:  
&nbsp;&nbsp;&nbsp;&nbsp;*ułamkowe — stała* *część wykładnik*<sub>zoptymalizowany pod kątem</sub> *liczb zmiennoprzecinkowych sufiks*<sub>zoptymalizowany pod kątem</sub>  
&nbsp;&nbsp;&nbsp;&nbsp;*sekwencja cyfr* *część wykładnik* *liczb zmiennoprzecinkowych sufiks*<sub>zoptymalizowany pod kątem</sub>

*Stała ułamkowe*:  
&nbsp;&nbsp;&nbsp;&nbsp;*sekwencja cyfr*<sub>zoptymalizowany pod kątem</sub> **.** *sekwencja cyfr*  
&nbsp;&nbsp;&nbsp;&nbsp;*sekwencja cyfr***.** 

*wykładnik część*:  
&nbsp;&nbsp;&nbsp;&nbsp;**e** *logowania*<sub>zoptymalizowany pod kątem</sub> *sekwencję cyfr*  
&nbsp;&nbsp;&nbsp;&nbsp;**E** *logowania*<sub>zoptymalizowany pod kątem</sub> *sekwencję cyfr*  

*znak*: jeden z  
&nbsp;&nbsp;&nbsp;&nbsp;**+ -**

*sekwencja cyfr*:  
&nbsp;&nbsp;&nbsp;&nbsp;*cyfra*  
&nbsp;&nbsp;&nbsp;&nbsp;*sekwencja cyfr* *cyfra*

*sufiks liczb zmiennoprzecinkowych*: jeden z  
&nbsp;&nbsp;&nbsp;&nbsp;**f, g F, G**

*stała całkowita*:  
&nbsp;&nbsp;&nbsp;&nbsp;*decimal-constant* *integer-suffix*<sub>opt</sub>  
&nbsp;&nbsp;&nbsp;&nbsp;*plik binarny constant* *integer-suffix*<sub>zoptymalizowany pod kątem</sub>  
&nbsp;&nbsp;&nbsp;&nbsp;*octal-constant* *integer-suffix*<sub>opt</sub>  
&nbsp;&nbsp;&nbsp;&nbsp;*hexadecimal-constant* *integer-suffix*<sub>opt</sub>

*decimal-constant*:  
&nbsp;&nbsp;&nbsp;&nbsp;*cyfry niezerowych* &nbsp; &nbsp; &nbsp; &nbsp; *decimal-constant* *cyfra*

*plik binarny constant*:  
&nbsp;&nbsp;&nbsp;&nbsp;**0b** *cyfra binarna*  
&nbsp;&nbsp;&nbsp;&nbsp;**0b** *cyfra binarna*

*stałej ósemkowej*:  
&nbsp;&nbsp;&nbsp;&nbsp;**0**  
&nbsp;&nbsp;&nbsp;&nbsp;*stałej ósemkowej* *cyfrą ósemkową*

*stałą szesnastkową*:  
&nbsp;&nbsp;&nbsp;&nbsp;**0 x***cyfry szesnastkowe*   
&nbsp;&nbsp;&nbsp;&nbsp;**0 X***cyfry szesnastkowe* &nbsp; &nbsp; &nbsp; &nbsp; *stałą szesnastkową* *cyfry szesnastkowe* 

*cyfry niezerowych*: jeden z  
&nbsp;&nbsp;&nbsp;&nbsp;**1 2 3 4 5 6 7 8 9**

*cyfrą systemu ósemkowego*: jeden z  
&nbsp;&nbsp;&nbsp;&nbsp;**0 1 2 3 4 5 6 7**

*cyfry szesnastkowe*: jeden z  
&nbsp;&nbsp;&nbsp;&nbsp;**0 1 2 3 4 5 6 7 8 9**  
&nbsp;&nbsp;&nbsp;&nbsp;**b c d e f**  
&nbsp;&nbsp;&nbsp;&nbsp;**A B C D E F**

*unsigned-suffix*: jeden z  
&nbsp;&nbsp;&nbsp;&nbsp;**u U**

*Long-suffix*: jeden z  
&nbsp;&nbsp;&nbsp;&nbsp;**l L**

*stałej znakowej*:  
&nbsp;&nbsp;&nbsp;&nbsp;**"** *c char sekwencji* **"**  
&nbsp;&nbsp;&nbsp;&nbsp;**L "** *c char sekwencji* **"**

*integer-suffix*:  
&nbsp;&nbsp;&nbsp;&nbsp;*unsigned-suffix* *long-suffix*<sub>zoptymalizowany pod kątem</sub>  
&nbsp;&nbsp;&nbsp;&nbsp;*Long-suffix* *unsigned-suffix*<sub>zoptymalizowany pod kątem</sub>

*c char sekwencji*:  
&nbsp;&nbsp;&nbsp;&nbsp;*c-char*  
&nbsp;&nbsp;&nbsp;&nbsp;*c char sekwencji* *c-char*

*c-char*:  
&nbsp;&nbsp;&nbsp;&nbsp;Każdy członek znak źródłowy zestawu z wyjątkiem pojedynczego cudzysłowu (**"**), ukośnika odwrotnego (**\\**), lub sekwencje znaków nowego wiersza

*Sekwencja unikowa*:  
&nbsp;&nbsp;&nbsp;&nbsp;*proste sekwencje*  
&nbsp;&nbsp;&nbsp;&nbsp;*ósemkowa sekwencja unikowa*  
&nbsp;&nbsp;&nbsp;&nbsp;*szesnastkowe sekwencje*

*proste sekwencje*: jeden z  
&nbsp;&nbsp;&nbsp;&nbsp;**\a \b \f \n \r \t \v**  
&nbsp;&nbsp;&nbsp;&nbsp;**\\' \\" \\\ \\?**

*ósemkowa sekwencja unikowa*:  
&nbsp;&nbsp;&nbsp;&nbsp;**\\** *cyfrą ósemkową*  
&nbsp;&nbsp;&nbsp;&nbsp;**\\** *cyfrą systemu ósemkowego* *cyfrą ósemkową*  
&nbsp;&nbsp;&nbsp;&nbsp;**\\** *cyfrą systemu ósemkowego* *cyfrą systemu ósemkowego* *cyfrą ósemkową*

*szesnastkowe sekwencje*:  
&nbsp;&nbsp;&nbsp;&nbsp;**\x** *cyfry szesnastkowe*  
&nbsp;&nbsp;&nbsp;&nbsp;*szesnastkowe sekwencje* *cyfry szesnastkowe*  
  
## <a name="see-also"></a>Zobacz też

[Gramatyka leksykalna](../c-language/lexical-grammar.md)  
