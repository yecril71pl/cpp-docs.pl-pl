---
title: "Stałe całkowite języka C | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 02/01/2018
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-language
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- integer constants
ms.assetid: fcf6b83c-2038-49ec-91ca-3d5ca1f83037
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 6c23e90d235e1ad2a8cca577c5cfbf2be55b52b6
ms.sourcegitcommit: 30ab99c775d99371ed22d1a46598e542012ed8c6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/03/2018
---
# <a name="c-integer-constants"></a>Stałe całkowite języka C

"Stała całkowita" jest dziesiętna (o podstawie 10), ósemkowy (podstawa 8) lub liczbą szesnastkową (podstawa 16), która reprezentuje wartością całkowitą. Stałe całkowite umożliwia reprezentują wartości całkowite, których nie można zmienić.

## <a name="syntax"></a>Składnia

*integer-constant*:  
&nbsp;&nbsp;*decimal-constant* *integer-suffix*<sub>opt</sub>  
&nbsp;&nbsp;*octal-constant* *integer-suffix*<sub>opt</sub>  
&nbsp;&nbsp;*hexadecimal-constant* *integer-suffix*<sub>opt</sub>  

*decimal — stała*:  
&nbsp;&nbsp;*nonzero-digit*  
&nbsp;&nbsp;*decimal — stała* *cyfrę*  

*ósemkowe stała*:  
&nbsp;&nbsp;**0**  
&nbsp;&nbsp;*ósemkowe stała* *-ósemkowego*  

*Stała liczba szesnastkowa*:  
&nbsp;&nbsp;**0 x***cyfrę szesnastkową*   
&nbsp;&nbsp;**0 X***cyfrę szesnastkową*   
&nbsp;&nbsp;*Stała liczba szesnastkowa* *cyfrę szesnastkową*  

*niezerowe cyfrowy*: jeden z  
&nbsp;&nbsp;**1 2 3 4 5 6 7 8 9**  

*ósemkowego*: jeden z  
&nbsp;&nbsp;**0 1 2 3 4 5 6 7**  

*cyfrę szesnastkową*: jeden z  
&nbsp;&nbsp;**0 1 2 3 4 5 6 7 8 9**  
&nbsp;&nbsp;**b c d e f**  
&nbsp;&nbsp;**A B C D E F**  
  
*integer-suffix*:  
&nbsp;&nbsp;*sufiks niepodpisane* *long sufiks*<sub>opcjonalnych</sub>  
&nbsp;&nbsp;*long-suffix* *unsigned-suffix*<sub>opt</sub>  
&nbsp;&nbsp;*unsigned-suffix* *64-bit-integer-suffix*<sub>opt</sub>

*sufiks niepodpisane*: jeden z  
&nbsp;&nbsp;**u U**  

*sufiks Long*: jeden z  
&nbsp;&nbsp;**l L**  
  
*64-bitowe — liczba całkowita sufiks*: jeden z &nbsp; &nbsp; **komputerach komputerach 64 64**  

Stałe całkowite są dodatnie, chyba że są poprzedzone znakiem minus (**-**). Znak minus jest interpretowany jako Jednoargumentowy operator negacji arytmetyczne. (Zobacz [jednoargumentowe operatory arytmetyczne](../c-language/unary-arithmetic-operators.md) informacji dotyczących tego operatora.)

Jeśli zaczyna się od stałej całkowitej **0 x** lub **0 X**, jest szesnastkową. Jeśli zaczyna się od cyfry **0**, jest ósemkowe. W przeciwnym razie jest przyjmowana dziesiętną.

Następujące wiersze są równoważne:

```C
0x1C   /* = Hexadecimal representation for decimal 28 */
034    /* = Octal representation for decimal 28 */
```

Żadne znaki odstępu można oddzielić cyfr całkowitą wartością stałą. Poniższe przykłady pokazują prawidłowych stałych decimal, ósemkowe i szesnastkowe.

```C
/* Decimal Constants */
10
132
32179

/* Octal Constants */
012
0204
076663

/* Hexadecimal Constants */
0xa or 0xA
0x84
0x7dB3 or 0X7DB3
```

## <a name="see-also"></a>Zobacz także

[Stałe języka C](../c-language/c-constants.md)  
