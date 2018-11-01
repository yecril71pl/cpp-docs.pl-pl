---
title: Wywołanie funkcji (C)
ms.date: 11/04/2016
helpviewer_keywords:
- function calls, C functions
- functions [C], calling
- function calls
ms.assetid: 35c66719-3f15-4d3b-97da-4e19dc97b308
ms.openlocfilehash: 46e010ed625e23aa6c21b8c78280b714c68582b8
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50478120"
---
# <a name="function-call-c"></a>Wywołanie funkcji (C)

A *wywołania funkcji* jest wyrażeniem, która zawiera nazwę wywoływanej funkcji lub wartość wskaźnika funkcji i, opcjonalnie, argumenty przekazywane do funkcji.

## <a name="syntax"></a>Składnia

*wyrażeniem przyrostkowym*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*wyrażeniem przyrostkowym***(***argument-expression-list*<sub>zoptymalizowany pod kątem</sub> **)**

*argument-expression-list*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*wyrażenia przypisania*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*argument-expression-list* **,** *wyrażenia przypisania*

*Wyrażeniem przyrostkowym* musi zwrócić adresu funkcji (na przykład identyfikator funkcji lub wartość wskaźnika funkcji), a *argument-expression-list* jest listą wyrażeń (oddzielonych przecinkami) których wartości ("arguments") są przekazywane do funkcji. *Argument-expression-list* argument może być pusta.

Wyrażenie wywołania funkcji ma wartość i typ wartość zwracaną przez funkcję. Funkcja nie może zwracać obiekt typu tablicy. Jeśli funkcja zwracany typ jest `void` (oznacza to, że funkcja została zadeklarowana nigdy nie zostać zwrócona wartość), ma także wyrażenie wywołania funkcji `void` typu. (Zobacz [wywołania funkcji](../c-language/function-calls.md) Aby uzyskać więcej informacji.)

## <a name="see-also"></a>Zobacz też

[Operator wywołania funkcji: ()](../cpp/function-call-operator-parens.md)