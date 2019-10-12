---
title: 'Operator warunkowy: &quest;:'
ms.date: 11/04/2016
f1_keywords:
- '?:'
- '?'
helpviewer_keywords:
- conditional operators [C++]
- '? : operator'
ms.assetid: 88643ee8-7100-4f86-880a-705ec22b6271
ms.openlocfilehash: 0a66b82682f90345518a2d520945e3aff1f78f89
ms.sourcegitcommit: 170f5de63b0fec8e38c252b6afdc08343f4243a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/11/2019
ms.locfileid: "72276804"
---
# <a name="conditional-operator-quest-"></a>Operator warunkowy: &quest;:

## <a name="syntax"></a>Składnia

```
expression ? expression : expression
```

## <a name="remarks"></a>Uwagi

Operator warunkowy ( **?:** ) jest operatorem Trzyelementowy (przyjmuje trzy operandy). Operator warunkowy działa w następujący sposób:

- Pierwszy operand jest niejawnie konwertowany na **bool**. Jest on oceniany i wszystkie efekty uboczne są wykonywane przed kontynuowaniem.

- Jeśli pierwszy operand ma **wartość true** (1), drugi operand jest oceniany.

- Jeśli pierwszy operand ma **wartość false** (0), trzeci operand jest oceniany.

Wynik operatora warunkowego jest wynikiem oceny dowolnego operandu — drugiego lub trzeciego. W wyrażeniu warunkowym jest oceniane tylko jeden z ostatnich dwóch argumentów operacji.

Wyrażenia warunkowe mają łączność od prawej do lewej. Pierwszy operand musi być typu całkowitego lub wskaźnika. Następujące reguły mają zastosowanie do drugiego i trzeciego operandu:

- Jeśli oba operandy są tego samego typu, wynik jest tego typu.

- Jeśli oba operandy są typu arytmetycznego lub wyliczeniowego, zwykle konwersje arytmetyczne (objęte [konwersjemi standardowymi](standard-conversions.md)) są wykonywane w celu przekonwertowania ich do typu wspólnego.

- Jeśli oba operandy są typami wskaźników lub jeśli jeden jest typem wskaźnika, a drugi jest wyrażeniem stałym, którego wynikiem jest 0, konwersje wskaźnika są wykonywane w celu przekonwertowania ich do typu wspólnego.

- Jeśli oba operandy są typami odwołań, konwersje odwołań są wykonywane w celu przekonwertowania ich do typu wspólnego.

- Jeśli oba operandy są typu void, typem wspólnym jest typ void.

- Jeśli oba operandy są tego samego typu zdefiniowanego przez użytkownika, typem wspólnym jest ten typ.

- Jeśli operandy mają różne typy, a co najmniej jeden z operandów ma typ zdefiniowany przez użytkownika, reguły języka są używane do określenia typu wspólnego. (Zobacz ostrzeżenie poniżej).

Wszystkie kombinacje drugiego i trzeciego operandu nie znajdują się na poprzedniej liście są niedozwolone. Typ wyniku jest typem wspólnym i jest l-wartością, jeśli oba operandy drugiego i trzeciego są tego samego typu, a oba są wartościami l.

> [!WARNING]
>  Jeśli typy drugiego i trzeciego operandu nie są identyczne, są wywoływane reguły konwersji typu złożonego, jak określono w C++ standardzie. Konwersje te mogą prowadzić do nieoczekiwanego zachowania, w tym konstruowania i niszczenia obiektów tymczasowych. Z tego powodu zdecydowanie radzimy sobie z jedną (1) unikać używania typów zdefiniowanych przez użytkownika jako argumentów operacji operatora warunkowego lub (2), jeśli używasz typów zdefiniowanych przez użytkownika, a następnie jawnie rzutuje każdy operand na wspólny typ.

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

[C++Wbudowane operatory, pierwszeństwo i łączność](../cpp/cpp-built-in-operators-precedence-and-associativity.md)<br/>
[Operator wyrażenia warunkowego](../c-language/conditional-expression-operator.md)