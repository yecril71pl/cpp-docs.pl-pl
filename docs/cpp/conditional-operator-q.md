---
title: 'Operator warunkowy: &quest; :'
ms.date: 11/04/2016
f1_keywords:
- '?:'
- '?'
helpviewer_keywords:
- conditional operators [C++]
- '? : operator'
ms.assetid: 88643ee8-7100-4f86-880a-705ec22b6271
ms.openlocfilehash: 1f2c58d5b7c31e9c29a72aea0e62494549fc10a9
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/27/2020
ms.locfileid: "87232329"
---
# <a name="conditional-operator-quest-"></a>Operator warunkowy: &quest; :

## <a name="syntax"></a>Składnia

```
expression ? expression : expression
```

## <a name="remarks"></a>Uwagi

Operator warunkowy (**?:**) jest operatorem Trzyelementowy (przyjmuje trzy operandy). Operator warunkowy działa w następujący sposób:

- Pierwszy operand jest niejawnie konwertowany na **`bool`** . Zostaje oceniony i przed kontynuowaniem ukończone zostają wszystkie efekty uboczne.

- Jeśli pierwszy operand ocenia wartość **`true`** (1), drugi operand jest oceniany.

- Jeśli pierwszy operand ocenia wartość **`false`** (0), trzeci operand jest oceniany.

Wynik operatora warunkowego jest wynikiem w zależności od ocenianego operandu — drugiego lub trzeciego. Tylko jeden z ostatnich dwóch operandów jest oceniany w wyrażeniu warunkowym.

Wyrażenia warunkowe mają zespolenie od prawej do lewej. Pierwszy operand musi być typu całkowitego lub typu wskaźnika. Następujące reguły mają zastosowanie do drugiego i trzeciego operandu:

- Jeśli oba operandy są tego samego typu, wynik jest tego typu.

- Jeśli oba operandy są typu arytmetycznego lub wyliczeniowego, zwykle konwersje arytmetyczne (objęte [konwersjemi standardowymi](standard-conversions.md)) są wykonywane w celu przekonwertowania ich do typu wspólnego.

- Jeśli oba operandy są typami wskaźników lub jeśli jeden jest typem wskaźnika, a drugi jest wyrażeniem stałym, którego wynikiem jest 0, konwersje wskaźnika są wykonywane w celu przekonwertowania ich do typu wspólnego.

- Jeśli oba operandy są typami odwołań, konwersje odwołań są wykonywane w celu przekonwertowania ich do typu wspólnego.

- Jeśli oba operandy są typu void, typem wspólnym jest typ void.

- Jeśli oba operandy są tego samego typu zdefiniowanego przez użytkownika, typem wspólnym jest ten typ.

- Jeśli operandy mają różne typy, a co najmniej jeden z operandów ma typ zdefiniowany przez użytkownika, reguły języka są używane do określenia typu wspólnego. (Zobacz ostrzeżenie poniżej).

Dowolna kombinacja drugiego i trzeciego operandu nie wymieniona na powyższej liście nie jest dozwolona. Typ wyniku jest popularnym typem i l-wartością, jeśli zarówno drugi jak i trzeci operand są tego samego typu i oba są l-wartościami.

> [!WARNING]
> Jeśli typy drugiego i trzeciego operandu nie są identyczne, są wywoływane reguły konwersji typu złożonego, jak określono w standardzie języka C++. Konwersje te mogą prowadzić do nieoczekiwanego zachowania, w tym konstruowania i niszczenia obiektów tymczasowych. Z tego powodu zdecydowanie radzimy sobie z jedną (1) unikać używania typów zdefiniowanych przez użytkownika jako argumentów operacji operatora warunkowego lub (2), jeśli używasz typów zdefiniowanych przez użytkownika, a następnie jawnie rzutuje każdy operand na wspólny typ.

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
