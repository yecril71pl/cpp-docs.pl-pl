---
title: 'Operatory równości: == i !='
description: Składnia języka C++ równa "i" nie jest równa operatora i jest używana.
ms.date: 07/23/2020
f1_keywords:
- '!='
- ==
- not_eq_cpp
helpviewer_keywords:
- '!= operator'
- equality operator
- not equal to comparison operator
- equality operator [C++], syntax
- == operator
- not_eq operator
- equal to operator
ms.assetid: ba4e9659-2392-4fb4-be5a-910a2a6df45a
ms.openlocfilehash: 567b83e99dce0354626f08a4788f1343314493b1
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/27/2020
ms.locfileid: "87227546"
---
# <a name="equality-operators--and-"></a>Operatory równości: == i !=

## <a name="syntax"></a>Składnia

> *wyrażenie* **`==`** *wyrażenie*\
> *wyrażenie* **`!=`** *wyrażenie*

## <a name="remarks"></a>Uwagi

Operatory równości danych binarnych porównują ich operandy dla ścisłej równości lub nierówności.

Operatory równości, równe ( **`==`** ) i nierówne ( **`!=`** ) mają niższy priorytet niż operatory relacyjne, ale zachowują się podobnie. Typem wyników dla tych operatorów jest **`bool`** .

Operator równości ( **`==`** ) zwraca, **`true`** Jeśli oba operandy mają tę samą wartość; w przeciwnym razie zwraca **`false`** . Operator nierówności ( **`!=`** ) zwraca **`true`** czy operandy nie mają tej samej wartości; w przeciwnym razie zwraca **`false`** .

## <a name="operator-keyword-for-"></a>Słowo kluczowe operatora dla! =

Język C++ określa **`not_eq`** jako alternatywną pisownię **`!=`** . (Nie istnieje alternatywna pisownia dla elementu **`==`** ). W języku C alternatywna pisownia jest podawana jako makro w \<iso646.h> nagłówku. W języku C++ alternatywna pisownia jest słowem kluczowym; Użycie \<iso646.h> lub odpowiednik języka C++ \<ciso646> jest przestarzałe. W programie Microsoft C++ [`/permissive-`](../build/reference/permissive-standards-conformance.md) [`/Za`](../build/reference/za-ze-disable-language-extensions.md) Opcja kompilatora or jest wymagana do włączenia alternatywnej pisowni.

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

## <a name="see-also"></a>Zobacz także

[Wyrażenia z operatorami binarnymi](../cpp/expressions-with-binary-operators.md)<br/>
[Wbudowane operatory języka C++, pierwszeństwo; i łączność](../cpp/cpp-built-in-operators-precedence-and-associativity.md)<br/>
[Operatory relacyjne i porównania języka C](../c-language/c-relational-and-equality-operators.md)
