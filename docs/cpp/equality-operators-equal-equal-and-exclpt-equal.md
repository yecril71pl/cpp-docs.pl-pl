---
title: 'Operatory porównania: == i !='
ms.date: 11/04/2016
f1_keywords:
- '!='
- ==
helpviewer_keywords:
- '!= operator'
- equality operator
- not equal to comparison operator
- equality operator [C++], syntax
- == operator
- not_eq operator
- equal to operator
ms.assetid: ba4e9659-2392-4fb4-be5a-910a2a6df45a
ms.openlocfilehash: 8a0c08f438528caeaac6d5e52e806a36fe56dd25
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/24/2020
ms.locfileid: "80189250"
---
# <a name="equality-operators--and-"></a>Operatory porównania: == i !=

## <a name="syntax"></a>Składnia

```
expression == expression
expression != expression
```

## <a name="remarks"></a>Uwagi

Operatory równości danych binarnych porównują ich operandy dla ścisłej równości lub nierówności.

Operatory równości, równe (`==`), a nie równe (`!=`) mają niższy priorytet niż operatory relacyjne, ale zachowują się podobnie. Typem wyniku dla tych operatorów jest **bool**.

Operator równości (`==`) zwraca **wartość true** (1), jeśli oba operandy mają tę samą wartość. w przeciwnym razie zwraca **wartość false** (0). Operator nierówności (`!=`) zwraca **wartość true** , jeśli operandy nie mają tej samej wartości; w przeciwnym razie zwraca **wartość false**.

## <a name="operator-keyword-for-"></a>Słowo kluczowe operatora dla! =

Operator `not_eq` jest odpowiednikiem tekstu `!=`. Istnieją dwa sposoby uzyskania dostępu do operatora `not_eq` w programach: Dołącz plik nagłówka `iso646.h`lub Kompiluj z opcją kompilatora [/za](../build/reference/za-ze-disable-language-extensions.md) (Wyłącz rozszerzenia językowe).

## <a name="example"></a>Przykład

```cpp
// expre_Equality_Operators.cpp
// compile with: /EHsc
#include <iostream>

using namespace std;

int main() {
   cout  << boolalpha
         << "The true expression 3 != 2 yields: "
         << (3 != 2) << endl
         << "The false expression 20 == 10 yields: "
         << (20 == 10) << endl;
}
```

Operatory równości mogą porównywać wskaźniki z elementami członkowskimi tego samego typu. W takim przypadku konwersje typu wskaźnik do elementu członkowskiego są wykonywane. Wskaźniki do elementów członkowskich można także porównać z wyrażeniem stałym, którego wynikiem jest 0.

## <a name="see-also"></a>Zobacz też

[Wyrażenia z operatorami dwuargumentowymi](../cpp/expressions-with-binary-operators.md)<br/>
[Wbudowane operatory, pierwszeństwo i kojarzenie języka C++](../cpp/cpp-built-in-operators-precedence-and-associativity.md)<br/>
[Operatory relacyjne i porównania języka C](../c-language/c-relational-and-equality-operators.md)
