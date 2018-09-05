---
title: Funkcja Call (C) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- function calls, C functions
- functions [C], calling
- function calls
ms.assetid: 35c66719-3f15-4d3b-97da-4e19dc97b308
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 1ec4e92774cdec75e47c07407ee72444a7486f7f
ms.sourcegitcommit: 92dbc4b9bf82fda96da80846c9cfcdba524035af
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/05/2018
ms.locfileid: "43751338"
---
# <a name="function-call-c"></a>Wywołanie funkcji (C)

A *wywołania funkcji* jest wyrażeniem, która zawiera nazwę wywoływanej funkcji lub wartość wskaźnika funkcji i, opcjonalnie, argumenty przekazywane do funkcji.  
  
## <a name="syntax"></a>Składnia

*wyrażeniem przyrostkowym*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*wyrażeniem przyrostkowym***(***argument-expression-list*<sub>zoptymalizowany pod kątem</sub> **)**   
  
*argument-expression-list*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*wyrażenia przypisania*<br/> &nbsp;&nbsp;&nbsp;&nbsp;*argument-expression-list* **,** *wyrażenia przypisania*  
  
*Wyrażeniem przyrostkowym* musi zwrócić adresu funkcji (na przykład identyfikator funkcji lub wartość wskaźnika funkcji), a *argument-expression-list* jest listą wyrażeń (oddzielonych przecinkami) których wartości ("arguments") są przekazywane do funkcji. *Argument-expression-list* argument może być pusta.  
  
Wyrażenie wywołania funkcji ma wartość i typ wartość zwracaną przez funkcję. Funkcja nie może zwracać obiekt typu tablicy. Jeśli funkcja zwracany typ jest `void` (oznacza to, że funkcja została zadeklarowana nigdy nie zostać zwrócona wartość), ma także wyrażenie wywołania funkcji `void` typu. (Zobacz [wywołania funkcji](../c-language/function-calls.md) Aby uzyskać więcej informacji.)  
  
## <a name="see-also"></a>Zobacz też

[Operator wywołania funkcji: ()](../cpp/function-call-operator-parens.md)