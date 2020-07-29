---
title: Wywołanie funkcji (C)
ms.date: 11/04/2016
helpviewer_keywords:
- function calls, C functions
- functions [C], calling
- function calls
ms.assetid: 35c66719-3f15-4d3b-97da-4e19dc97b308
ms.openlocfilehash: 23531f25128fc267caa3a3cad5f2c52e603a2cc6
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/27/2020
ms.locfileid: "87229691"
---
# <a name="function-call-c"></a>Wywołanie funkcji (C)

*Wywołanie funkcji* jest wyrażeniem, które zawiera nazwę wywoływanej funkcji lub wartość wskaźnika funkcji oraz, opcjonalnie, argumenty, które są przekazane do funkcji.

## <a name="syntax"></a>Składnia

*wyrażenie przyrostkowe*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*przyrostkowe wyrażenie***(***opt-expression-list*<sub>opt</sub> **)**    

*argument-lista wyrażeń*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*przypisanie — wyrażenie*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*argumenty argumentu-list* **,** *przypisanie-wyrażenie*

*Wyrażenie przyrostkowe* musi być szacowane do adresu funkcji (na przykład identyfikatora funkcji lub wartości wskaźnika funkcji), a *Lista argumentów wyrażenia* jest listą wyrażeń (rozdzielonych przecinkami), których wartości ("argumenty") są przekazane do funkcji. Argument *-Expression-List* może być pusty.

Wyrażenie wywołania funkcji ma wartość i typ wartości zwracanej funkcji. Funkcja nie może zwracać obiektu typu Array. Jeśli typem zwracanym funkcji jest **`void`** (to oznacza, że funkcja została zadeklarowana nigdy do zwrócenia wartości), wyrażenie wywołania funkcji również ma **`void`** Typ. (Zobacz [wywołania funkcji](../c-language/function-calls.md) , aby uzyskać więcej informacji).

## <a name="see-also"></a>Zobacz także

[Operator wywołania funkcji: ()](../cpp/function-call-operator-parens.md)
