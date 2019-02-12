---
title: Wywołanie funkcji (C)
ms.date: 11/04/2016
helpviewer_keywords:
- function calls, C functions
- functions [C], calling
- function calls
ms.assetid: 35c66719-3f15-4d3b-97da-4e19dc97b308
ms.openlocfilehash: d22bdebc8fa832afb14a2cc09e6a441b7b9e8a5a
ms.sourcegitcommit: f4be868c0d1d78e550fba105d4d3c993743a1f4b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/12/2019
ms.locfileid: "56147415"
---
# <a name="function-call-c"></a>Wywołanie funkcji (C)

A *wywołania funkcji* jest wyrażeniem, która zawiera nazwę wywoływanej funkcji lub wartość wskaźnika funkcji i, opcjonalnie, argumenty przekazywane do funkcji.

## <a name="syntax"></a>Składnia

*postfix-expression*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*wyrażeniem przyrostkowym***(***argument-expression-list*<sub>zoptymalizowany pod kątem</sub> **)**

*argument-expression-list*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*assignment-expression*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*argument-expression-list* **,** *wyrażenia przypisania*

*Wyrażeniem przyrostkowym* musi zwrócić adresu funkcji (na przykład identyfikator funkcji lub wartość wskaźnika funkcji), a *argument-expression-list* jest listą wyrażeń (oddzielonych przecinkami) których wartości ("arguments") są przekazywane do funkcji. *Argument-expression-list* argument może być pusta.

Wyrażenie wywołania funkcji ma wartość i typ wartość zwracaną przez funkcję. Funkcja nie może zwracać obiekt typu tablicy. Jeśli funkcja zwracany typ jest `void` (oznacza to, że funkcja została zadeklarowana nigdy nie zostać zwrócona wartość), ma także wyrażenie wywołania funkcji `void` typu. (Zobacz [wywołania funkcji](../c-language/function-calls.md) Aby uzyskać więcej informacji.)

## <a name="see-also"></a>Zobacz także

[Operator wywołania funkcji: ()](../cpp/function-call-operator-parens.md)
