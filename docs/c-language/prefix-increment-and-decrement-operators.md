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

Operatory jednoargumentowe`++` ( **--** i) są nazywane operatorami przyrostu lub zmniejszania "prefix", gdy operatory przyrostu i zmniejszania są wyświetlane przed argumentem operacji. Przyrosty przyrostkowe i zmniejszania mają wyższy priorytet niż przyrost i zmniejszenie prefiksu. Operand musi mieć typ całkowity, zmiennoprzecinkowy lub wskaźnik i musi być modyfikowalnym wyrażeniem l-wartości (wyrażeniem bez atrybutu **const** ). Wynik jest l-wartością.

Gdy operator występuje przed jego operandem, operand jest zwiększany lub zmniejszany, a jego nowa wartość jest wynikiem wyrażenia.

Operand typu całkowitego lub zmiennoprzecinkowego jest zwiększany lub zmniejszany przez wartość całkowitą 1. Typ wyniku jest taki sam jak typ argumentu operacji. Operand typu wskaźnika jest zwiększany lub zmniejszany o rozmiar obiektu, do którego się odnosi. Przyrostowy wskaźnik wskazuje na następny obiekt; zmniejszający wskaźnik wskazuje na poprzedni obiekt.

## <a name="example"></a>Przykład

Ten przykład ilustruje operator jednoargumentowego zmniejszania prefiksu:

```
if( line[--i] != '\n' )
    return;
```

W tym przykładzie zmienna `i` jest zmniejszana, zanim zostanie użyta jako indeks dolny do. `line`

## <a name="see-also"></a>Zobacz też

[Operatory jednoargumentowe języka C](../c-language/c-unary-operators.md)
