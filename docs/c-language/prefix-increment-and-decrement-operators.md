---
title: Operatory prefiksów inkrementacji i dekrementacji
ms.date: 11/04/2016
helpviewer_keywords:
- increment operators, types of
- decrement operators, syntax
- decrement operators
ms.assetid: 9a441bb9-d94a-4b6a-9db2-0d0d76bc480d
ms.openlocfilehash: 041c44829b8a267ca053dc85da0333e86db6b7b7
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62325497"
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

## <a name="see-also"></a>Zobacz także

[Operatory jednoargumentowe języka C](../c-language/c-unary-operators.md)
