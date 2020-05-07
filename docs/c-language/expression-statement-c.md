---
title: Instrukcja wyrażeń (C)
ms.date: 11/04/2016
helpviewer_keywords:
- statements, expression
- expression statements
ms.assetid: 1085982b-dc16-4c1e-9ddd-0cd85c8fe2e3
ms.openlocfilehash: 736ed4fbbd9f87c675c0bb9566c6c31287e77917
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62233712"
---
# <a name="expression-statement-c"></a>Instrukcja wyrażeń (C)

Po wykonaniu instrukcji Expression wyrażenie jest oceniane zgodnie z regułami opisanymi w [wyrażeniach i przypisaniach](../c-language/expressions-and-assignments.md).

## <a name="syntax"></a>Składnia

*wyrażenie-instrukcja*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*expression*<sub>wybór</sub> wyrażenia **;**

Wszystkie efekty uboczne z oceny wyrażenia są kończone przed wykonaniem następnej instrukcji. Pusta Instrukcja wyrażenia jest nazywana instrukcją o wartości null. Aby uzyskać więcej informacji [, zobacz instrukcję o wartości null](../c-language/null-statement-c.md) .

W tych przykładach przedstawiono instrukcje wyrażeń.

```C
x = ( y + 3 );            /* x is assigned the value of y + 3  */
x++;                      /* x is incremented                  */
x = y = 0;                /* Both x and y are initialized to 0 */
proc( arg1, arg2 );       /* Function call returning void      */
y = z = ( f( x ) + 3 );   /* A function-call expression        */
```

W ostatniej instrukcji wyrażenie wywołania funkcji, wartość wyrażenia, która zawiera każdą wartość zwracaną przez funkcję, jest zwiększane o 3, a następnie przypisane do zmiennych `y` i. `z`

## <a name="see-also"></a>Zobacz też

[Instrukcje](../c-language/statements-c.md)
