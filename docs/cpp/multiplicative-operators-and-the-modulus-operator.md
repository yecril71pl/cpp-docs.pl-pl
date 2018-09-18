---
title: Operatory mnożenia i Operator modulo | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
f1_keywords:
- '%'
- /
dev_langs:
- C++
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 02d6d7d5d8f6c7dcce54e1dff54795b253d9d04a
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46106068"
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

- Dzielenie (**/**)

- Moduł (resztę z dzielenia) (**%**)

Te operatory dwuargumentowe mają łączność od lewej do prawej.

Operatory multiplikatywne przyjmują operandy typów arytmetycznych. Operator modulo (**%**) ma bardziej rygorystyczne wymagania w tym jego operandy muszą być typu całkowitego. (Aby uzyskać resztę z dzielenia liczb zmiennopozycyjnych, należy użyć funkcji środowiska uruchomieniowego [fmod](../c-runtime-library/reference/fmod-fmodf.md).) Konwersje omówione w [konwersje standardowe](standard-conversions.md) są stosowane do operandów, a wynik jest typu konwertowanego.

Operator mnożenia daje wynik mnożenia pierwszego operandu przez drugi.

Operator dzielenia daje wynik dzielenia pierwszego operandu przez drugi.

Operator modulo daje resztę uzyskaną z następującego wyrażenia, gdzie *e1* jest pierwszym operandem i *e2* jest drugim: *e1* -(*e1*  /  *e2*) \* *e2*, gdzie oba operandy są typu całkowitoliczbowego.

Dzielenie przez 0 w wyrażeniu dzielenia lub modulo jest nieokreślone i powoduje błąd w czasie wykonywania. Dlatego następujące wyrażenia generują nieokreślone, błędne wyniki:

```cpp
i % 0
f / 0.0
```

Jeśli oba operandy wyrażenia mnożenia, dzielenia lub modulo mają taki sam znak, wynik jest dodatni. W przeciwnym razie wynik jest ujemny. Znak wyniku operacji modulo zależy od implementacji.

> [!NOTE]
>  Ponieważ konwersje wykonywane przez operatory multiplikatywne nie przewidują warunków przepełnienia lub niedomiaru, informacje mogą zostać utracone, jeśli wynik operacji multiplikatywnej nie może być przedstawiony w typie operandów po konwersji.

**Microsoft Specific**

W Microsoft C++, wynik wyrażenia modulo jest zawsze taki sam, jak znak pierwszego operandu.

**END specyficzny dla Microsoft**

Jeśli obliczone dzielenie dwóch liczb całkowitych jest niedokładne i tylko jeden argument jest liczbą ujemną, wynik jest największą liczbą całkowitą (w wielkości, pomijając znak), mniejszą niż dokładna wartość, którą dałaby operacja dzielenia. Na przykład, obliczona wartość -11 / 3 to-3.666666666. Wynik takiego dzielenia jest -3.

Relacja między operatory multiplikatywne otrzymuje tożsamość (*e1* / *e2*) \* *e2*  +  *e1* % *e2* == *e1*.

## <a name="example"></a>Przykład

Następujący program pokazuje operatory multiplikatywne. Należy pamiętać, że oba operandy z `10 / 3` muszą być jawnie rzutowane na typ **float** Aby uniknąć obcinania, tak aby oba operandy są typu **float** przed dzieleniem.

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

## <a name="see-also"></a>Zobacz także

[Wyrażenia z operatorami dwuargumentowymi](../cpp/expressions-with-binary-operators.md)<br/>
[Wbudowane operatory, pierwszeństwo i kojarzenie języka C++](../cpp/cpp-built-in-operators-precedence-and-associativity.md)<br/>
[Operatory mnożenia języka C](../c-language/c-multiplicative-operators.md)