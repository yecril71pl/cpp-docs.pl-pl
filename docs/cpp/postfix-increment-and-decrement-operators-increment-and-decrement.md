---
title: 'Operatory przyrostka inkrementacji i dekrementacji: ++ i--| Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
f1_keywords:
- --
- ++
dev_langs:
- C++
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 4591f9f4fed8b3b8dd1c24b8200b3365d87194b8
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46044668"
---
# <a name="postfix-increment-and-decrement-operators--and---"></a>Operatory przyrostka inkrementacji i dekrementacji: ++ i --

## <a name="syntax"></a>Składnia

```
postfix-expression ++
postfix-expression --
```

## <a name="remarks"></a>Uwagi

Język C++ zawiera przedrostkowe i przyrostkowe operatory inkrementacyjne i dekrementacyjne; w tej sekcji opisano tylko przyrostkowe operatory inkrementacyjne i dekrementacyjne. (Aby uzyskać więcej informacji, zobacz [operatory prefiksów inkrementacji i dekrementacji](../cpp/prefix-increment-and-decrement-operators-increment-and-decrement.md).) Różnica między tymi dwoma jest, że w notacji przyrostkowej, operator pojawia się po *wyrażeniem przyrostkowym*, natomiast w notacji przedrostkowej, operator pojawia się przed *wyrażenia.* W poniższym przykładzie pokazano przyrostkowy operator inkrementacyjny:

```cpp
i++;
```

Efektem zastosowania przyrostkowego operatora inkrementacyjnego (**++**) jest, że wartość argumentu operacji jest zwiększana o jedną jednostkę odpowiedniego typu. Podobnie efektem zastosowania przyrostkowego operatora dekrementacyjnego (**--**) jest, że wartość argumentu operacji zostaje zmniejszona o jedną jednostkę odpowiedniego typu.

Ważne jest, aby należy pamiętać, że zwiększenie przyrostkowe lub dekrementacji wyrażenie zwróci wartość wyrażenia *przed* zastosowaniem odpowiedniego operatora. Operacja inkrementacyjna lub dekrementacyjna występuje *po* operand zostaje oceniony. Problem występuje tylko wtedy, gdy przyrostkowa operacja inkrementacyjna lub dekrementacyjna występuje w kontekście większego wyrażenia.

Po zastosowaniu przyrostkowego operatora do argumentu funkcji, nie ma gwarancji, że wartość zostanie zwiększona lub zmniejszona przed przekazaniem jej do funkcji.  Zobacz sekcję 1.9.17 w standardzie języka C++, aby uzyskać więcej informacji.

Zastosowanie przyrostkowego operatora inkrementacyjnego do wskaźnika do tablicy obiektów typu **długie** powoduje w rzeczywistości dodanie liczby cztery do wewnętrznej reprezentacji wskaźnika. To zachowanie powoduje, że wskaźnik, który wcześniej odwoływał się do *n*element th do odwoływania się do tablicy (*n*+ 1) th element.

Argumenty operacji dla przyrostkowych operatorów inkrementacyjnych i dekrementacyjnych muszą być modyfikowalnymi (nie **const**) l wartościami typu arytmetycznego lub wskaźnikowego. Typ wyniku jest taki sam, jak w przypadku *wyrażeniem przyrostkowym*, ale nie jest już l wartością.

**Visual Studio 2017 w wersji 15.3 lub nowszej** (udostępniono [/STD: c ++ 17](../build/reference/std-specify-language-standard-version.md)): argument przyrostka inkrementacji i dekrementacji operator nie może być typu **bool**.

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

[Wyrażenia przyrostków](../cpp/postfix-expressions.md)<br/>
[Wbudowane operatory, pierwszeństwo i kojarzenie języka C++](../cpp/cpp-built-in-operators-precedence-and-associativity.md)<br/>
[Operatory przyrostka inkrementacji i dekrementacji języka C](../c-language/c-postfix-increment-and-decrement-operators.md)