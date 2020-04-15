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
ms.openlocfilehash: 4ba4c80d40450fd5975b047a1a4fca63146c5773
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81337263"
---
# <a name="conditional-operator-quest-"></a>Operator warunkowy: &quest; :

## <a name="syntax"></a>Składnia

```
expression ? expression : expression
```

## <a name="remarks"></a>Uwagi

Operator warunkowy (**? :**) jest operatorem trójskładnikowym (zajmuje trzy operandy). Operator warunkowy działa w następujący sposób:

- Pierwszy operand jest niejawnie konwertowany na **bool**. Zostaje oceniony i przed kontynuowaniem ukończone zostają wszystkie efekty uboczne.

- Jeśli pierwszy operand ocenia **true** (1), drugi operand jest oceniany.

- Jeśli pierwszy operand ocenia **false** (0), trzeci operand jest oceniany.

Wynik operatora warunkowego jest wynikiem w zależności od ocenianego operandu — drugiego lub trzeciego. Tylko jeden z ostatnich dwóch operandów jest oceniany w wyrażeniu warunkowym.

Wyrażenia warunkowe mają zespolenie od prawej do lewej. Pierwszy operand musi być typu całkowitego lub typu wskaźnika. Do drugiego i trzeciego operandów mają zastosowanie następujące zasady:

- Jeśli oba argumenty są tego samego typu, wynik jest tego typu.

- Jeśli oba argumenty są typami arytmetycznymi lub wyliczanymi, zwykłe konwersje arytmetyczne (omówione w [konwersjach standardowych)](standard-conversions.md)są wykonywane w celu przekonwertowania ich na wspólny typ.

- Jeśli oba argumenty są typu wskaźnika lub jeśli jeden jest typem wskaźnika, a drugi jest wyrażeniem stałym, które ocenia do 0, konwersje wskaźnika są wykonywane w celu przekonwertowania ich na wspólny typ.

- Jeśli oba argumenty mają typy odwołań, konwersje odwołań są wykonywane w celu przekonwertowania ich na typ wspólny.

- Jeśli oba argumenty są typu void, typowy typ jest void typu.

- Jeśli oba argumenty są tego samego typu zdefiniowanego przez użytkownika, typowym typem jest ten typ.

- Jeśli argumenty mają różne typy i co najmniej jeden z argumentów ma typ zdefiniowany przez użytkownika, reguły języka są używane do określenia typu wspólnego. (Patrz ostrzeżenie poniżej).

Dowolna kombinacja drugiego i trzeciego operandu nie wymieniona na powyższej liście nie jest dozwolona. Typ wyniku jest popularnym typem i l-wartością, jeśli zarówno drugi jak i trzeci operand są tego samego typu i oba są l-wartościami.

> [!WARNING]
> Jeśli typy drugiego i trzeciego argumentów nie są identyczne, wywoływane są reguły konwersji typów złożonych, określone w standardzie C++. Konwersje te mogą prowadzić do nieoczekiwanego zachowania, w tym budowy i niszczenia obiektów tymczasowych. Z tego powodu zdecydowanie zalecamy(1) unikanie używania typów zdefiniowanych przez użytkownika jako argumentów z operatorem warunkowym lub (2) w przypadku używania typów zdefiniowanych przez użytkownika, a następnie jawnie rzutowanie każdego operandu na wspólny typ.

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

## <a name="see-also"></a>Zobacz też

[Wbudowane operatory, pierwszeństwo i kojarzenie języka C++](../cpp/cpp-built-in-operators-precedence-and-associativity.md)<br/>
[Operator wyrażenia warunkowego](../c-language/conditional-expression-operator.md)
