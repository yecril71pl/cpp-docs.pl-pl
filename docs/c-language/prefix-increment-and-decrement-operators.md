---
title: Prefiksów inkrementacji i dekrementacji | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- increment operators, types of
- decrement operators, syntax
- decrement operators
ms.assetid: 9a441bb9-d94a-4b6a-9db2-0d0d76bc480d
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 7077e1b40701f8586ce8322ac9922517ac77b22b
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46018291"
---
# <a name="prefix-increment-and-decrement-operators"></a>Operatory prefiksów inkrementacji i dekrementacji

Operatory jednoargumentowe (`++` i **--**) są nazywane "prefiks" przyrostem lub operatory dekrementacji, gdy operatory inkrementacji lub dekrementacji następować przed elementem operandu. Przyrostka inkrementacji i dekrementacji ma wyższy priorytet niż prefiksów inkrementacji i dekrementacji. Argument musi być typu całkowitego, zmiennoprzecinkowego lub wskaźnik i musi być wyrażeniem modyfikowalną l wartością (bez **const** atrybutu). Wynik jest wartością l.

Gdy operator pojawia się przed argumentem, argument jest zwiększone lub zmniejszone, a jego nowa wartość jest wynikiem wyrażenia.

Argument operacji typu całkowitego lub zmiennoprzecinkowego jest zwiększone lub zmniejszone wartość całkowita 1. Typ wyniku jest taki sam jak typ operandu. Argument operacji typu wskaźnika jest zwiększone lub zmniejszone rozmiar obiektu, które ona rozwiązuje. Wskazuje zwiększona wskaźnik do następnego obiektu. zmniejszony wskaźnik wskazuje poprzedniego obiektu.

## <a name="example"></a>Przykład

Ten przykład ilustruje operator jednoargumentowy dekrementacja prefiksu:

```
if( line[--i] != '\n' )
    return;
```

W tym przykładzie zmienna `i` zostanie zmniejszony, zanim zostaną one użyte jako indeks dolny, aby `line`.

## <a name="see-also"></a>Zobacz też

[Operatory jednoargumentowe języka C](../c-language/c-unary-operators.md)