---
title: Wyrażenie Statement (C) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- statements, expression
- expression statements
ms.assetid: 1085982b-dc16-4c1e-9ddd-0cd85c8fe2e3
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 73071e5cc3eef20895e4eff3bade8e37066dfd71
ms.sourcegitcommit: 92dbc4b9bf82fda96da80846c9cfcdba524035af
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/05/2018
ms.locfileid: "43765960"
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