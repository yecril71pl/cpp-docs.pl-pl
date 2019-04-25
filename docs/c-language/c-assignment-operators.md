---
title: Operatory przypisania w języku C
ms.date: 06/14/2018
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
ms.openlocfilehash: 5080f390d302840e9e7b349cf1c21ab618ae48db
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62326875"
---
# <a name="c-assignment-operators"></a>Operatory przypisania w języku C

Operacja przypisania przypisuje wartość operandu po prawej stronie do lokalizacji magazynu o nazwie określonej przez argument po lewej stronie. Dlatego lewostronny operand operatora przypisania musi być modyfikowalną l wartością. Po przypisaniu wyrażenia przypisania ma wartość lewy operand, ale nie jest l wartością.

## <a name="syntax"></a>Składnia

*assignment-expression*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*conditional-expression*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*unary-expression* *assignment-operator* *assignment-expression*

*operator przypisania*: jeden z<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**=** **\*=** **/=** **%=** **+=** **-=** **\<\<=** **>>=** **&=** **^=** **|=**

Operatory przypisania w języku C może przekształcić i przypisywanie wartości w ramach jednej operacji. C, oferuje następujące operatory przypisania:

|Operator|Operacja wykonywana|
|--------------|-------------------------|
|**=**|Przypisanie proste|
|**&#42;=**|Mnożenie i przypisanie|
|**/=**|Dzielenie i przypisanie|
|**%=**|Resztę przypisania|
|**+=**|Dodawanie i przypisanie|
|**-=**|Odejmowanie i przypisanie|
|**<\<=**|Przesunięcie bitowe w lewo i przypisanie|
|**>>=**|Przesunięcie bitowe w prawo i przypisanie|
|**&=**|Bitowe OR- i przypisanie|
|**^=**|Bitowe OR wyłączne przypisania|
|**&#124;=**|Przypisanie włącznie — Alternatywy bitowej|

W przypisaniu typ wartości po prawej stronie jest konwertowany na typ wartości po lewej stronie, a wartość jest przechowywana w lewy argument operacji po przeprowadzeniu przypisania. Lewy operand nie może być tablica, funkcji lub stałą. Ścieżki określonej konwersji, która jest zależna od dwóch typów, jest opisane szczegółowo w temacie [konwersje typów](../c-language/type-conversions-c.md).

## <a name="see-also"></a>Zobacz także

- [Operatory przypisania](../cpp/assignment-operators.md)