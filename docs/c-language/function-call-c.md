---
title: Wywołanie funkcji (C)
ms.date: 11/04/2016
helpviewer_keywords:
- function calls, C functions
- functions [C], calling
- function calls
ms.assetid: 35c66719-3f15-4d3b-97da-4e19dc97b308
ms.openlocfilehash: d22bdebc8fa832afb14a2cc09e6a441b7b9e8a5a
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62233301"
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

Wyrażenie wywołania funkcji ma wartość i typ wartości zwracanej funkcji. Funkcja nie może zwracać obiektu typu Array. Jeśli typem zwracanym funkcji jest `void` (to oznacza, że funkcja została zadeklarowana nigdy do zwrócenia wartości), wyrażenie wywołania funkcji również ma `void` typ. (Zobacz [wywołania funkcji](../c-language/function-calls.md) , aby uzyskać więcej informacji).

## <a name="see-also"></a>Zobacz też

[Operator wywołania funkcji: ()](../cpp/function-call-operator-parens.md)
