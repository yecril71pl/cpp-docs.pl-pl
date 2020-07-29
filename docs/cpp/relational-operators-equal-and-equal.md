---
title: 'Operatory relacyjne: &lt; , &gt; , &lt; = i&gt;='
ms.date: 11/04/2016
f1_keywords:
- <
- '>'
helpviewer_keywords:
- '> operator'
- less than operator
- relational operators [C++], syntax
- '>= operator'
- greater than or equal to operators [C++]
- greater than operators [C++]
- < operator
- less than or equal to operator
- <= operator
ms.assetid: d346b53d-f14d-4962-984f-89d39a17ca0f
ms.openlocfilehash: 81421a135059b8804955d472365ebef9802d3210
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/27/2020
ms.locfileid: "87227117"
---
# <a name="relational-operators-lt-gt-lt-and-gt"></a>Operatory relacyjne: &lt; , &gt; , &lt; = i&gt;=

## <a name="syntax"></a>Składnia

```
expression < expression
expression > expression
expression <= expression
expression >= expression
```

## <a name="remarks"></a>Uwagi

Binarne operatory relacyjne określają następujące relacje:

- Mniejsze niż ( **\<** )

- Większe niż ( **>** )

- Mniejsze niż lub równe ( **\<=** )

- Większe niż lub równe ( **>=** )

Operatory relacyjne mają łączność od lewej do prawej. Oba operandy operatorów relacyjnych muszą być typu arytmetycznego lub wskaźnika. Dają one wartości typu **`bool`** . Zwracana wartość to **`false`** (0), jeśli relacja w wyrażeniu ma wartość FAŁSZ; w przeciwnym razie zwracana wartość to **`true`** (1).

## <a name="example"></a>Przykład

```cpp
// expre_Relational_Operators.cpp
// compile with: /EHsc
#include <iostream>

using namespace std;

int main() {
   cout  << "The true expression 3 > 2 yields: "
         << (3 > 2) << endl
         << "The false expression 20 < 10 yields: "
         << (20 < 10) << endl;
}
```

Wyrażenia w poprzednim przykładzie muszą być ujęte w nawiasy, ponieważ operator wstawiania strumienia ( **<<** ) ma wyższy priorytet niż operatory relacyjne. W związku z tym pierwsze wyrażenie bez nawiasów będzie oceniane jako:

```cpp
(cout << "The true expression 3 > 2 yields: " << 3) < (2 << "\n");
```

Zwykle konwersje arytmetyczne omówione w [konwersji standardowej](standard-conversions.md) są stosowane do operandów typów arytmetycznych.

## <a name="comparing-pointers"></a>Porównywanie wskaźników

Gdy dwa wskaźniki do obiektów tego samego typu są porównywane, wynik zależy od lokalizacji obiektów wskazywanych w przestrzeni adresowej programu. Wskaźniki można także porównać do stałego wyrażenia, które ma wartość 0 lub do wskaźnika typu `void *` . Jeśli Porównanie wskaźnika jest wykonywane względem wskaźnika typu `void *` , inny wskaźnik jest niejawnie konwertowany na typ `void *` . Następnie dokonywane jest porównanie.

Nie można porównać dwóch wskaźników różnego typu, chyba że:

- Jeden typ to typ klasy pochodzącej z drugiego typu.

- Co najmniej jeden ze wskaźników jest jawnie konwertowany (rzutowany) na typ `void *` . (Drugi wskaźnik jest niejawnie konwertowany na typ `void *` dla konwersji).

Wynik porównania dwóch wskaźników tego samego typu, które wskazują ten sam obiekt zawsze będzie równy. Jeżeli porównywane są dwa wskaźniki do niestatycznych elementów członkowskich obiektu, obowiązują następujące zasady:

- Jeśli typ klasy nie jest a **`union`** i jeśli dwa elementy członkowskie nie są oddzielone *specyfikatorem dostępu*, na przykład, **`public`** **`protected`** , lub **`private`** , wskaźnik do składowej zadeklarowanej jako Last będzie porównywany z większym niż wskaźnik do składowej zadeklarowanej wcześniej.

- Jeśli dwa elementy członkowskie są oddzielone *specyfikatorem dostępu*, wyniki są niezdefiniowane.

- Jeśli typ klasy to a **`union`** , wskaźniki do różnych składowych danych, które są **`union`** równe.

Jeśli dwa wskaźniki wskazują elementy tej samej tablicy lub na pierwszy element poza tablicą, wskaźnik do obiektu z wyższym indeksem dolnym daje większy wynik porównania. Porównanie wskaźników jest gwarantowane jako prawidłowe tylko wtedy, gdy wskaźniki dotyczą obiektów w jednej tablicy lub do pierwszej lokalizacji poza tablicą.

## <a name="see-also"></a>Zobacz także

[Wyrażenia z operatorami dwuargumentowymi](../cpp/expressions-with-binary-operators.md)<br/>
[Wbudowane operatory, pierwszeństwo i kojarzenie języka C++](../cpp/cpp-built-in-operators-precedence-and-associativity.md)<br/>
[Operatory relacyjne i porównania języka C](../c-language/c-relational-and-equality-operators.md)
