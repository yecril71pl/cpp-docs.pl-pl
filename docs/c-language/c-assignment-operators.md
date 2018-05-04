---
title: Operatory przypisania w języku C | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- remainder assignment operator (%=)
- '&= operator'
- bitwise-AND assignment operator
- operators [C], assignment
- operators [C], shift
- ^= operator, assignment operators
- += operator
- '>>= operator'
- '|= operator'
- division assignment operator
- subtraction operator
- right shift operators
- subtraction operator, C assignment operators
- = operator, assignment operators
- '*= operator'
- '>> operator'
- '%= operator'
- assignment operators, C
- = operator
- assignment operators
- assignment conversions
- -= operator
- multiplication assignment operator (*=)
- shift operators, right
- /= operator
- operator >>=, C assignment operators
- <<= operator
ms.assetid: 11688dcb-c941-44e7-a636-3fc98e7dac40
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 9a13f3b36ae4f5bbd11f170d78d735427882d2ff
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
---
# <a name="c-assignment-operators"></a>Operatory przypisania w języku C
Operacja przypisania przypisuje wartość prawostronny operand do lokalizacji magazynu o nazwie przez argument po lewej stronie. W związku z tym lewostronny operand operatora przypisania musi być modyfikowalną l wartość. Po przypisania wyrażenie przypisania ma wartość lewy operand, ale nie jest wartością l-value.  
  
 **Składnia**  
  
 *wyrażenia przypisania*:  
 *Wyrażenia warunkowego*  
  
 *wyrażenie jednoargumentowe operator przypisania z wyrażenia przypisania*  
  
 *operator przypisania*: jeden z  
 **= \*=** `/=` `%=` `+=` **-= <\<= >>= &=** `^=` `|=`  
  
 Operatory przypisania w języku C można zarówno transformacji i przypisywanie wartości w jednej operacji. C zapewnia następujące operatory przypisania:  
  
|Operator|Operację|  
|--------------|-------------------------|  
|**=**|Przypisanie proste|  
|**\*=**|Mnożenie i przypisanie|  
|`/=`|Dzielenie i przypisanie|  
|`%=`|Przypisanie pozostałej|  
|`+=`|Dodawanie i przypisanie|  
|**-=**|Odejmowanie i przypisanie|  
|**<\<=**|Przesunięcie bitowe w lewo i przypisanie|  
|**>>=**|Przesunięcie bitowe w prawo i przypisanie|  
|**&=**|Operator- i przypisania|  
|`^=`|Przypisanie z bitowego OR wyłączne|  
|`&#124;=`|Wraz z wartościami granicznymi Alternatywy przypisania|  
  
 W przypisaniu typ wartości po prawej stronie jest konwertowana na typ wartości po lewej stronie, a wartość jest przechowywana w lewy argument operacji po przeprowadzeniu przypisania. Lewy argument operacji nie może być tablicą, funkcji lub stałą. Ścieżka określonych konwersji zależy od dwóch typów jest opisane szczegółowo w [konwersje typów](../c-language/type-conversions-c.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Operatory przypisania](../cpp/assignment-operators.md)