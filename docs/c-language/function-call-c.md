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
ms.openlocfilehash: 49c9483cb6e556d5a8b174377c0dad666834c9e5
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
ms.locfileid: "32384362"
---
# <a name="function-call-c"></a>Wywołanie funkcji (C)
"Wywołanie funkcji" to wyrażenie, która zawiera nazwę wywoływanej funkcji lub wartość wskaźnika funkcji i, opcjonalnie, argumenty przekazywany do funkcji.  
  
## <a name="syntax"></a>Składnia  
 *Operatory przyrostka wyrażenie*:  
 *wyrażenie przyrostek***(***lista wyrażeń argument* opt **)**   
  
 *Lista wyrażeń argument*:  
 *assignment-expression*  
  
 *Lista wyrażeń argument***,***wyrażenia przypisania*   
  
 *Wyrażenie przyrostek* musi być adresem funkcji (na przykład identyfikator funkcji lub wartość wskaźnika funkcji), i *lista wyrażeń argument* znajduje się lista wyrażeń (oddzielone przecinkami) których wartości ("argumentów") są przekazywane do funkcji. *Lista wyrażeń argument* argument może być pusta.  
  
 Wyrażenie wywołania funkcji ma wartość i typ wartości zwracanej przez funkcję. Funkcja nie może zwracać obiektu typu array. Jeśli funkcja zwracany typ jest `void` (oznacza to, że funkcja została zadeklarowana nigdy nie, aby zwrócić wartość), ma także wyrażenie wywołania funkcji `void` typu. (Zobacz [wywołania funkcji](../c-language/function-calls.md) Aby uzyskać więcej informacji.)  
  
## <a name="see-also"></a>Zobacz też  
 [Operator wywołania funkcji: ()](../cpp/function-call-operator-parens.md)