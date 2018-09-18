---
title: 'Operatory relacyjne: &lt;, &gt;, &lt;=, i &gt;= | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
f1_keywords:
- <
- '>'
dev_langs:
- C++
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 7d9c51036b183e2368def19dcd70f804acc2826a
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46081614"
---
# <a name="relational-operators-lt-gt-lt-and-gt"></a>Operatory relacyjne: &lt;, &gt;, &lt;=, i &gt;=

## <a name="syntax"></a>Składnia

```
expression < expression
expression > expression
expression <= expression
expression >= expression
```

## <a name="remarks"></a>Uwagi

Operatory relacyjne binarne określają następujące relacje:

- Mniej niż (**\<**)

- Większa (**>**)

- Mniejsze niż lub równe (**\<=**)

- Większa niż lub równe (**>=**)

Operatory relacyjne mają łączność od lewej do prawej. Oba operandy operatory relacyjne musi być typu arytmetycznego lub wskaźnikowego. Dają one wartości typu **bool**. Wartość zwracana jest **false** (0), jeśli relacja wyrażenia jest wartość FAŁSZ; w przeciwnym razie, wartość zwracana jest **true** (1).

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

Wyrażenia w poprzednim przykładzie muszą być ujęte w nawiasy, ponieważ operator wstawiania strumienia (**<<**) mają wyższy priorytet niż operatory relacyjne. Dlatego pierwsze wyrażenie bez nawiasów oceniono jako:

```cpp
(cout << "The true expression 3 > 2 yields: " << 3) < (2 << "\n");
```

Popularne konwersje arytmetyczne omówione w [konwersje standardowe](standard-conversions.md) są stosowane do operandy typów arytmetycznych.

## <a name="comparing-pointers"></a>Porównywanie wskaźników

Gdy dwa wskaźniki do obiektów tego samego typu są porównywane, wynik zależy od lokalizacji obiektów wskazywanych w przestrzeni adresowej programu. Wskaźniki można również porównać do stałego wyrażenia, które ocenia na 0 lub do wskaźnika typu `void *`. Jeśli wskaźnik jest porównywany wskaźnika typu `void *`, drugi wskaźnik jest niejawnie konwertowany na typ `void *`. Następnie dokonywane jest porównanie.

Nie można porównać dwóch wskaźników różnego typu, chyba że:

- Jeden typ to typ klasy pochodzącej z drugiego typu.

- Co najmniej jeden ze wskaźników jest jawnie konwertowany (rzutowany) na typ `void *`. (Drugi wskaźnik jest niejawnie konwertowany na typ `void *` do konwersji.)

Wynik porównania dwóch wskaźników tego samego typu, które wskazują ten sam obiekt zawsze będzie równy. Jeżeli porównywane są dwa wskaźniki do niestatycznych elementów członkowskich obiektu, obowiązują następujące zasady:

- Jeśli typem klasy nie jest **Unii**, a jeśli dwa elementy członkowskie nie są rozdzielone *specyfikator dostępu*, takich jak **publicznych**, **chronione**, lub **prywatnej**, wskaźnik do składowej zadeklarowanej ostatnio da większy wynik porównania niż wskaźnik do składowej zadeklarowanej wcześniej.

- Jeśli dwa elementy członkowskie są rozdzielone *specyfikator dostępu*, wyniki są niezdefiniowane.

- Jeśli typem klasy jest **Unii**, wskaźniki do różnych składowych danych w tym **Unii** porównania równości.

Jeśli dwa wskaźniki wskazują elementy tej samej tablicy lub na pierwszy element poza tablicą, wskaźnik do obiektu z wyższym indeksem dolnym daje większy wynik porównania. Porównanie wskaźników jest gwarantowane jako prawidłowe tylko wtedy, gdy wskaźniki dotyczą obiektów w jednej tablicy lub do pierwszej lokalizacji poza tablicą.

## <a name="see-also"></a>Zobacz także

[Wyrażenia z operatorami dwuargumentowymi](../cpp/expressions-with-binary-operators.md)<br/>
[Wbudowane operatory, pierwszeństwo i kojarzenie języka C++](../cpp/cpp-built-in-operators-precedence-and-associativity.md)<br/>
[Operatory relacyjne i porównania języka C](../c-language/c-relational-and-equality-operators.md)