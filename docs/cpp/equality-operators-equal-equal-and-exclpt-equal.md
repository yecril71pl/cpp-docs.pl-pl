---
title: 'Operatory porównania: == i !='
ms.date: 11/04/2016
f1_keywords:
- not_eq
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
ms.openlocfilehash: d6248d4a31c478b62e5fbe304d9bde9b51b7cb06
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62392172"
---
# <a name="equality-operators--and-"></a>Operatory porównania: == i !=

## <a name="syntax"></a>Składnia

```
expression == expression
expression != expression
```

## <a name="remarks"></a>Uwagi

Operatory binarne porównania porównać ich operandami dla Ścisła równość i nierówność.

Operatory porównania, równa się (`==`) i nie równa się (`!=`), mają niższy priorytet niż operatory relacyjne, ale także działają w podobny sposób. Typ wyniku dla tych operatorów **bool**.

Operator równości (`==`) zwraca **true** (1), jeśli oba operandy mają taką samą wartość; w przeciwnym razie zwraca **false** (0). Nie równe — operator (`!=`) zwraca **true** Jeśli operandów nie mają tej samej wartości; w przeciwnym razie zwraca **false**.

## <a name="operator-keyword-for-"></a>Słowo kluczowe operator! =

`not_eq` Operator jest odpowiednikiem tekstu `!=`. Istnieją dwa sposoby dostępu do `not_eq` operatora w programach: uwzględnić plik nagłówka `iso646.h`, lub kompilowanie z [/Za](../build/reference/za-ze-disable-language-extensions.md) — opcja kompilatora (Wyłącz rozszerzenia językowe).

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

Operatory porównania porównanie wskaźników do elementów członkowskich tego samego typu. Takie porównania są wykonywane konwersje wskaźników do elementów członkowskich. Wskaźniki do elementów członkowskich można również porównać do stałego wyrażenia, którego wynikiem jest 0.

## <a name="see-also"></a>Zobacz także

[Wyrażenia z operatorami dwuargumentowymi](../cpp/expressions-with-binary-operators.md)<br/>
[Wbudowane operatory, pierwszeństwo i kojarzenie języka C++](../cpp/cpp-built-in-operators-precedence-and-associativity.md)<br/>
[Operatory relacyjne i porównania języka C](../c-language/c-relational-and-equality-operators.md)