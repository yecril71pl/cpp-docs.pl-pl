---
title: 'Operator warunkowy:? :'
ms.date: 11/04/2016
f1_keywords:
- '?:'
- '?'
helpviewer_keywords:
- conditional operators [C++]
- '? : operator'
ms.assetid: 88643ee8-7100-4f86-880a-705ec22b6271
ms.openlocfilehash: 8744ca8546d48e9283cc0dfa9d80babf5076f8b3
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62399151"
---
# <a name="conditional-operator--"></a>Operator warunkowy:? :

## <a name="syntax"></a>Składnia

```
expression ? expression : expression
```

## <a name="remarks"></a>Uwagi

Operator warunkowy (**?:**) jest trójargumentowy (ma trzy operandy). Operator warunkowy działa w następujący sposób:

- Pierwszy operand jest niejawnie konwertowany na **bool**. Zostaje oceniony i przed kontynuowaniem ukończone zostają wszystkie efekty uboczne.

- Jeśli pierwszy operand ma wartość **true** (1), drugi operand jest oceniany.

- Jeśli pierwszy operand ma wartość **false** (0), trzeci operand jest oceniany.

Wynik operatora warunkowego jest wynikiem w zależności od ocenianego operandu — drugiego lub trzeciego. Tylko jeden z ostatnich dwóch operandów jest oceniany w wyrażeniu warunkowym.

Wyrażenia warunkowe mają zespolenie od prawej do lewej. Pierwszy operand musi być typu całkowitego lub typu wskaźnika. Następujące reguły mają zastosowanie do drugiego i trzeciego argumentu operacji:

- Jeśli oba operandy są tego samego typu, wynik jest tego typu.

- Jeśli oba operandy są typu operacji arytmetycznych lub wyliczeniem, zwykle konwersje arytmetyczne (omówione w [konwersje standardowe](standard-conversions.md)) są wykonywane w celu przekonwertowania ich do typu wspólnego.

- Jeśli oba operandy są typami wskaźników lub jeśli jeden jest typem wskaźnika, a drugi jest stałym wyrażeniem, którego wynikiem jest 0, konwersje wskaźnika są wykonywane w celu przekonwertowania ich do typu wspólnego.

- Jeśli oba operandy są typami odwołań, konwersje odwołania są wykonywane w celu przekonwertowania ich do typu wspólnego.

- Jeśli oba operandy są typu void, wspólny typ jest typem void.

- Jeśli oba operandy są tego samego typu zdefiniowanego przez użytkownika, wspólny typ jest tego typu.

- Jeśli argumenty mają różne typy i co najmniej jeden z argumentów ma typ zdefiniowany przez użytkownika reguły języka są używane do określenia typu wspólnego. (Zobacz poniższe ostrzeżenie).

Dowolna kombinacja drugiego i trzeciego operandu nie wymieniona na powyższej liście nie jest dozwolona. Typ wyniku jest popularnym typem i l-wartością, jeśli zarówno drugi jak i trzeci operand są tego samego typu i oba są l-wartościami.

> [!WARNING]
>  Jeśli typy drugiego i trzeciego operandu nie są identyczne, reguły konwersji typu złożonego, jak to określono w standardzie C++, są wywoływane. Takiej konwersji może prowadzić do nieoczekiwanego zachowania, w tym budowa i niszczenie obiektów tymczasowych. Z tego powodu zdecydowanie zaleca się do jednego (1) unika się używania typów zdefiniowanych przez użytkownika jako argumentów za pomocą operatora warunkowego lub (2) Jeśli możesz użyć typów zdefiniowanych przez użytkownika, a następnie jawnie rzutowane każdy argument do typu wspólnego.

## <a name="example"></a>Przykład

```cpp
// expre_Expressions_with_the_Conditional_Operator.cpp
// compile with: /EHsc
// Demonstrate conditional operator
#include <iostream>
using namespace std;
int main() {
   int i = 1, j = 2;
   cout << ( i > j ? i : j ) << " is greater." << endl;
}
```

## <a name="see-also"></a>Zobacz także

[Wbudowane operatory, pierwszeństwo i kojarzenie języka C++](../cpp/cpp-built-in-operators-precedence-and-associativity.md)<br/>
[Operator wyrażenia warunkowego](../c-language/conditional-expression-operator.md)