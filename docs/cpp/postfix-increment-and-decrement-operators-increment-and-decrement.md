---
title: 'Operatory przyrostka inkrementacji i dekrementacji: ++ i --'
ms.date: 11/04/2016
f1_keywords:
- --
- ++
helpviewer_keywords:
- increment operators [C++], syntax
- member-selection operators [C++]
- -- operator [C++], postfix decrement operators
- postfix operators [C++]
- ++ operator [C++], postfix increment operators
- decrement operators [C++], syntax
- operators [C++], postfix
- decrement operators [C++]
ms.assetid: 0204d5c8-51b0-4108-b8a1-074c5754d89c
ms.openlocfilehash: 8c3eeb47ec81f4073452c17f40eb2fec4911989f
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/27/2020
ms.locfileid: "87213284"
---
# <a name="postfix-increment-and-decrement-operators--and---"></a>Operatory przyrostka inkrementacji i dekrementacji: ++ i --

## <a name="syntax"></a>Składnia

```
postfix-expression ++
postfix-expression --
```

## <a name="remarks"></a>Uwagi

Język C++ zawiera przedrostkowe i przyrostkowe operatory inkrementacyjne i dekrementacyjne; w tej sekcji opisano tylko przyrostkowe operatory inkrementacyjne i dekrementacyjne. (Aby uzyskać więcej informacji, zobacz [Operatory zwiększania i zmniejszania prefiksu](../cpp/prefix-increment-and-decrement-operators-increment-and-decrement.md)). Różnica między nimi polega na tym, że w notacji przyrostkowej operator występuje po *przyrostkowym wyrażeniu*, natomiast w notacji prefiksu operator pojawia się przed *wyrażeniem.* W poniższym przykładzie pokazano przyrostkowy operator inkrementacyjny:

```cpp
i++;
```

Efekt zastosowania przyrostkowego operatora przyrostu ( **++** ) polega na tym, że wartość operandu jest zwiększana o jedną jednostkę odpowiedniego typu. Analogicznie, efekt zastosowania operatora zmniejszania przyrostka ( **--** ) polega na tym, że wartość operandu zostanie zmniejszona o jedną jednostkę odpowiedniego typu.

Należy zwrócić uwagę, że przyrostowe wyrażenie zwiększające lub zmniejszania daje wartość wyrażenia *przed* zastosowaniem odpowiedniego operatora. Operacja zwiększania lub zmniejszania występuje *po* obliczeniu operandu. Problem występuje tylko wtedy, gdy przyrostkowa operacja inkrementacyjna lub dekrementacyjna występuje w kontekście większego wyrażenia.

Po zastosowaniu przyrostkowego operatora do argumentu funkcji, nie ma gwarancji, że wartość zostanie zwiększona lub zmniejszona przed przekazaniem jej do funkcji.  Zobacz sekcję 1.9.17 w standardzie języka C++, aby uzyskać więcej informacji.

Stosowanie przyrostkowego operatora przyrostu do wskaźnika do tablicy obiektów typu **`long`** faktycznie dodaje cztery do wewnętrznej reprezentacji wskaźnika. To zachowanie powoduje, że wskaźnik, który wcześniej odnosił się do *n*-tym elementu tablicy, odwołuje się do elementu (*n*+ 1).

Operandy arytmetyczne przyrostu oraz operatory zmniejszania przyrostowego muszą być modyfikowalne (nie **`const`** ) l-wartości arytmetyczne lub typu wskaźnika. Typ wyniku jest taki sam jak w przypadku *wyrażenia przyrostkowego*, ale nie jest już wartością l.

**Program Visual Studio 2017 w wersji 15,3 lub nowszej** (dostępny w [/std: c++ 17](../build/reference/std-specify-language-standard-version.md)): operand przyrostka lub operator zmniejszania przyrostkowego nie może być typu **`bool`** .

Poniższy kod ilustruje przyrostkowy operator inkrementacyjny:

```cpp
// expre_Postfix_Increment_and_Decrement_Operators.cpp
// compile with: /EHsc
#include <iostream>
using namespace std;

int main() {
   int i = 10;
   cout << i++ << endl;
   cout << i << endl;
}
```

Nie są obsługiwane operacje postinkrementacyjne i postdekrementacyjne na typach wyliczeniowych.

```cpp
enum Compass { North, South, East, West );
Compass myCompass;
for( myCompass = North; myCompass != West; myCompass++ ) // Error
```

## <a name="see-also"></a>Zobacz także

[Wyrażenia przyrostkowe](../cpp/postfix-expressions.md)<br/>
[Wbudowane operatory, pierwszeństwo i kojarzenie języka C++](../cpp/cpp-built-in-operators-precedence-and-associativity.md)<br/>
[Operatory przyrostka dysku C i zmniejszania](../c-language/c-postfix-increment-and-decrement-operators.md)
