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
ms.openlocfilehash: 791f18793b49f7d3a986c3271fddef3acef33062
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81367922"
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

- Mnożenie<strong>\*</strong>( )

- Dywizja**/**( )

- Moduł (pozostała część od**%** podziału) ( )

Te operatory dwuargumentowe mają łączność od lewej do prawej.

Operatory multiplikatywne przyjmują operandy typów arytmetycznych. Operator modułu (**%**) ma bardziej rygorystyczne wymagania, ponieważ jego argumenty muszą być typu integralnego. (Aby uzyskać pozostałą część podziału zmiennoprzecinkowego, użyj funkcji czasu wykonywania, [fmod](../c-runtime-library/reference/fmod-fmodf.md).) Konwersje objęte [konwersjami standardowymi](standard-conversions.md) są stosowane do argumentów, a wynik jest typu przekonwertowanego.

Operator mnożenia daje wynik mnożenia pierwszego operandu przez drugi.

Operator dzielenia daje wynik dzielenia pierwszego operandu przez drugi.

Operator modułu daje pozostałą część podana przez następujące wyrażenie, gdzie *e1* jest pierwszym operandem, a *e2* drugim: *e1* - (*e1* / *e2*) \* *e2*, gdzie oba opery są typu integralnego.

Dzielenie przez 0 w wyrażeniu dzielenia lub modulo jest nieokreślone i powoduje błąd w czasie wykonywania. Dlatego następujące wyrażenia generują nieokreślone, błędne wyniki:

```cpp
i % 0
f / 0.0
```

Jeśli oba operandy wyrażenia mnożenia, dzielenia lub modulo mają taki sam znak, wynik jest dodatni. W przeciwnym razie wynik jest ujemny. Znak wyniku operacji modulo zależy od implementacji.

> [!NOTE]
> Ponieważ konwersje wykonywane przez operatory multiplikatywne nie przewidują warunków przepełnienia lub niedomiaru, informacje mogą zostać utracone, jeśli wynik operacji multiplikatywnej nie może być przedstawiony w typie operandów po konwersji.

**Specyficzne dla firmy Microsoft**

W Microsoft C++, wynik wyrażenia modulo jest zawsze taki sam, jak znak pierwszego operandu.

**ZAKOŃCZ Specyficzne dla firmy Microsoft**

Jeśli obliczone dzielenie dwóch liczb całkowitych jest niedokładne i tylko jeden argument jest liczbą ujemną, wynik jest największą liczbą całkowitą (w wielkości, pomijając znak), mniejszą niż dokładna wartość, którą dałaby operacja dzielenia. Na przykład wartość obliczona -11 / 3 wynosi -3.66666666. Wynik tego integralnego podziału wynosi -3.

Związek między operatorami mnożenia wynika z tożsamości ( \* *e1* / *e2*) *e2* + *e1* % *e2 e1* == *e1 e1*.

## <a name="example"></a>Przykład

Następujący program pokazuje operatory multiplikatywne. Należy zauważyć, że `10 / 3` albo operand musi być jawnie rzutowana do typu **float,** aby uniknąć obcinania, tak aby oba argumenty są typu **float** przed podziałem.

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
