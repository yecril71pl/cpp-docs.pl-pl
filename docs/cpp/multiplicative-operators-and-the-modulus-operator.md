---
title: Operatory mnożenia i Operator modulo
ms.date: 11/04/2016
f1_keywords:
- '%'
- /
helpviewer_keywords:
- operators [C++], multiplicative
- arithmetic operators [C++], multiplicative operators
- modulus operator [C++]
- '* operator'
- division operator [C++], multiplicative operators
- '% operator'
- multiplication operator [C++], multiplicative operators
- multiplicative operators [C++]
- division operator
ms.assetid: b53ea5da-d0b4-40dc-98f3-0aa52d548293
ms.openlocfilehash: bc6359d3d7d2045d44af07f80b3e101da356d4b1
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/24/2020
ms.locfileid: "80179357"
---
# <a name="multiplicative-operators-and-the-modulus-operator"></a>Operatory mnożenia i Operator modulo

## <a name="syntax"></a>Składnia

```
expression * expression
expression / expression
expression % expression
```

## <a name="remarks"></a>Uwagi

Operatory multiplikatywne to:

- Mnożenie (<strong>\*</strong>)

- Dzielenie ( **/** )

- Modulo (reszta z dzielenia) ( **%** )

Te operatory dwuargumentowe mają łączność od lewej do prawej.

Operatory multiplikatywne przyjmują operandy typów arytmetycznych. Operator modulo ( **%** ) ma bardziej rygorystyczne wymaganie, aby jego operandy muszą być typu całkowitego. (Aby uzyskać resztę podziału zmiennoprzecinkowego, użyj funkcji Run-Time, [FMOD —](../c-runtime-library/reference/fmod-fmodf.md)). Konwersje omówione w [konwersjach standardowych](standard-conversions.md) są stosowane do operandów, a wynik jest konwertowany typ.

Operator mnożenia daje wynik mnożenia pierwszego operandu przez drugi.

Operator dzielenia daje wynik dzielenia pierwszego operandu przez drugi.

Operator modulo Zwraca resztę podaną przez następujące wyrażenie, gdzie *E1* jest pierwszym operandem, a *E2* jest drugim: *E1* -(*E1* / *E2*) \* *E2*, gdzie oba operandy są typami całkowitymi.

Dzielenie przez 0 w wyrażeniu dzielenia lub modulo jest nieokreślone i powoduje błąd w czasie wykonywania. Dlatego następujące wyrażenia generują nieokreślone, błędne wyniki:

```cpp
i % 0
f / 0.0
```

Jeśli oba operandy wyrażenia mnożenia, dzielenia lub modulo mają taki sam znak, wynik jest dodatni. W przeciwnym razie wynik jest ujemny. Znak wyniku operacji modulo zależy od implementacji.

> [!NOTE]
>  Ponieważ konwersje wykonywane przez operatory multiplikatywne nie przewidują warunków przepełnienia lub niedomiaru, informacje mogą zostać utracone, jeśli wynik operacji multiplikatywnej nie może być przedstawiony w typie operandów po konwersji.

**Specyficzne dla firmy Microsoft**

W Microsoft C++, wynik wyrażenia modulo jest zawsze taki sam, jak znak pierwszego operandu.

**ZAKOŃCZENIE określonych przez firmę Microsoft**

Jeśli obliczone dzielenie dwóch liczb całkowitych jest niedokładne i tylko jeden argument jest liczbą ujemną, wynik jest największą liczbą całkowitą (w wielkości, pomijając znak), mniejszą niż dokładna wartość, którą dałaby operacja dzielenia. Na przykład obliczona wartość-11/3 wynosi-3,666666666. Wynik tego podziału całkowitego to-3.

Relacja między operatorami mnożenia jest podawana przez tożsamość (*e1* / *E2*) \* *e2* + *E1* % *E2* == *E1*.

## <a name="example"></a>Przykład

Następujący program pokazuje operatory multiplikatywne. Należy zauważyć, że każdy operand `10 / 3` musi być jawnie rzutowany na typ **float** , aby uniknąć obcinania, tak aby oba operandy były typu **zmiennoprzecinkowego** przed dzieleniem.

```cpp
// expre_Multiplicative_Operators.cpp
// compile with: /EHsc
#include <iostream>
using namespace std;
int main() {
   int x = 3, y = 6, z = 10;
   cout  << "3 * 6 is " << x * y << endl
         << "6 / 3 is " << y / x << endl
         << "10 % 3 is " << z % x << endl
         << "10 / 3 is " << (float) z / x << endl;
}
```

## <a name="see-also"></a>Zobacz też

[Wyrażenia z operatorami dwuargumentowymi](../cpp/expressions-with-binary-operators.md)<br/>
[Wbudowane operatory, pierwszeństwo i kojarzenie języka C++](../cpp/cpp-built-in-operators-precedence-and-associativity.md)<br/>
[Operatory mnożenia języka C](../c-language/c-multiplicative-operators.md)
