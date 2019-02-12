---
title: Instrukcja wyrażeń (C)
ms.date: 11/04/2016
helpviewer_keywords:
- statements, expression
- expression statements
ms.assetid: 1085982b-dc16-4c1e-9ddd-0cd85c8fe2e3
ms.openlocfilehash: 736ed4fbbd9f87c675c0bb9566c6c31287e77917
ms.sourcegitcommit: f4be868c0d1d78e550fba105d4d3c993743a1f4b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/12/2019
ms.locfileid: "56148793"
---
# <a name="expression-statement-c"></a>Instrukcja wyrażeń (C)

Po wykonaniu instrukcji wyrażenia wyrażenie jest obliczane zgodnie z regułami przedstawione [wyrażenia i przydziały](../c-language/expressions-and-assignments.md).

## <a name="syntax"></a>Składnia

*expression-statement*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*wyrażenie*<sub>zoptymalizowany pod kątem</sub> **;**

Ze wszystkimi efektami ubocznymi oceny wyrażenia są wykonywane przed wykonaniem następnej instrukcji. Instrukcja wyrażenia empty jest wywoływana instrukcja o wartości null. Zobacz [instrukcja o wartości Null](../c-language/null-statement-c.md) Aby uzyskać więcej informacji.

Przykłady te pokazują instrukcje wyrażeń.

```C
x = ( y + 3 );            /* x is assigned the value of y + 3  */
x++;                      /* x is incremented                  */
x = y = 0;                /* Both x and y are initialized to 0 */
proc( arg1, arg2 );       /* Function call returning void      */
y = z = ( f( x ) + 3 );   /* A function-call expression        */
```

W ostatniej instrukcji wyrażenie wywołania funkcji wartości wyrażenia, w tym dowolną wartość zwrócona przez funkcję, jest wzrosła o 3 i przypisywany do obu zmiennych `y` i `z`.

## <a name="see-also"></a>Zobacz także

[Instrukcje](../c-language/statements-c.md)
