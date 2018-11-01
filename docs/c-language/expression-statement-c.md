---
title: Instrukcja wyrażeń (C)
ms.date: 11/04/2016
helpviewer_keywords:
- statements, expression
- expression statements
ms.assetid: 1085982b-dc16-4c1e-9ddd-0cd85c8fe2e3
ms.openlocfilehash: b825e88703e1913d9b6d916360174060854c632a
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50667470"
---
# <a name="expression-statement-c"></a>Instrukcja wyrażeń (C)

Po wykonaniu instrukcji wyrażenia wyrażenie jest obliczane zgodnie z regułami przedstawione [wyrażenia i przydziały](../c-language/expressions-and-assignments.md).

## <a name="syntax"></a>Składnia

*Instrukcja wyrażeń*:<br/>
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

## <a name="see-also"></a>Zobacz też

[Instrukcje](../c-language/statements-c.md)