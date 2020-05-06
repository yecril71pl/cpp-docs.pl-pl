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

*stała*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*zmiennoprzecinkowe — stała*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*Integer — stała*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*Wyliczenie — stała*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*znak — stała*

*zmiennoprzecinkowe — stała*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;dwuargumentowy *—* *wykładnik*<sub>opt</sub> stałej —<sub>wybór</sub> *sufiksu zmiennoprzecinkowego*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*wykładnik* *sekwencji cyfr* —<sub>wybór</sub> *sufiksu zmiennoprzecinkowego*części

*stała ułamkowa*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*wybór sekwencji cyfr*<sub>opt</sub> **.** *Sekwencja cyfr*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*sekwencja cyfr*  **.**

*część wykładnika*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;cyfra za *podpisanie*<sub>opt</sub> **e** *-sekwencji*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;Cyfra za *podpisanie*<sub>opt</sub> **E** *-sekwencji*

*znak*: jedno z<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**+ -**

*sekwencja cyfr*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*kontrol*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*cyfra* *cyfra*

*sufiks zmiennoprzecinkowy*: jeden z<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**f l l**

*Liczba całkowita — stała*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*Decimal — stała* *Liczba całkowita sufiksu*<sub>opt</sub><br/>
&nbsp;&nbsp;&nbsp;&nbsp;*binarne — stała* *Liczba całkowita sufiksu*<sub>opt</sub><br/>
&nbsp;&nbsp;&nbsp;&nbsp;*ósemkowe — stała* *Liczba całkowita sufiksu*<sub>opt</sub><br/>
&nbsp;&nbsp;&nbsp;&nbsp;*niestandardowa* *Liczba całkowita z sufiksem*<sub>opt</sub> szesnastkowym

*stała dziesiętna*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*niezerowe cyfry*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*dziesiętna —* *cyfra* stała

*stała binarna*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**0b** *— cyfra binarna*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**0b** *— cyfra binarna*

*ósemkowa — stała*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**2,0**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*ósemkowe — stała* *cyfra ósemkowa*

*stała szesnastkowa*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**0x**  *— cyfra szesnastkowa*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**0x**  *— cyfra szesnastkowa*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*szesnastkowe — stała* *szesnastkowa*

*niezerowe cyfry*: jedno z<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**1 2 3 4 5 6 7 8 9**

*ósemkowa — cyfra*: jeden z<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**0 1 2 3 4 5 6 7**

*cyfra szesnastkowa*: jedna z<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**0 1 2 3 4 5 6 7 8 9**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**a b c d e f**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**A B C D E F**

*niepodpisany sufiks*: jeden z<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**u U**

*długi sufiks*: jeden z<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**l L**

*znak — stała*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**"** *c-char-Sequence* **"**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**L "** *c-char-Sequence* **"**

*sufiks wartości całkowitej*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;<sub>wybór</sub> *długich sufiksów* *bez znaku*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;<sub>wybór</sub> *długiego* sufiksu *bez sufiksu*

*c-char-Sequence*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*c-char*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*c-char-Sequence* *c-char*

*c-char*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;Każdy element członkowski zestawu znaków źródłowych z wyjątkiem pojedynczego cudzysłowu (**'**), ukośnika odwrotnego**\\**() lub znaku ucieczki wiersza

*sekwencja unikowa*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*prosta — sekwencja ucieczki*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*ósemkowe — sekwencja ucieczki*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*szesnastkowe — sekwencja ucieczki*

*prosta — sekwencja ucieczki*: jedna z<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**\a \b/\n/\r \t \v**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**\\' \\" \\\ \\?**

*ósemkowe — sekwencja ucieczki*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**\\***cyfra ósemkowa*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**\\**ósemkowa *cyfra* *ósemkowa*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**\\***ósemkowa cyfra* *ósemkowa* *cyfra* ósemkowa

*notacja szesnastkowa — sekwencja ucieczki*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**\x** *— cyfra szesnastkowa*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*szesnastkowe — Ucieczka — sekwencja* *szesnastkowa*

## <a name="see-also"></a>Zobacz też

[Gramatyka leksykalna](../c-language/lexical-grammar.md)<br/>
