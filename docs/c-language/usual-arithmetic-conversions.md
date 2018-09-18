---
title: Popularne konwersje arytmetyczne | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- arithmetic conversions [C++]
- type conversion [C++], arithmetic
- operators [C], arithmetic conversions
- data type conversion [C++], arithmetic
- conversions [C++], arithmetic
- arithmetic operators [C++], type conversions
ms.assetid: bfa49803-0efd-45d0-b987-111412a140d7
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 15ceaa3e5b50fbc72d14564630399b5e5ba74b49
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46030432"
---
# <a name="usual-arithmetic-conversions"></a>Popularne konwersje arytmetyczne

Większość operatory języka C wykonywać konwersje typów, aby wyświetlić operandy wyrażenia do typu wspólnego, albo aby rozszerzyć wartości krótka liczba całkowita określająca rozmiar w operacjach maszyny. Konwersje wykonywane przez operatory języka C zależą od tego, konkretny operator i typ operandu lub argumentów operacji. Jednak wielu operatorów wykonywać podobne konwersje operandów typów całkowitych i zmiennoprzecinkowych. Konwersje te są nazywane "konwersje arytmetyczne". Konwersja wartości argumentu operacji na zgodny typ. powoduje, że nie wprowadzono zmian w jej wartość.

Konwersje arytmetyczne podsumowano poniżej są nazywane "typowe konwersje arytmetyczne". Te kroki są stosowane tylko w przypadku operatory binarne, które oczekują typu arytmetycznego. Celem jest uzyskanie wspólnego typu, który jest również typ wyniku. Aby ustalić, jakie konwersje faktycznie mieć miejsce, kompilator dotyczy następującego algorytmu do operacji binarnych w wyrażeniu. Poniższe kroki nie są kolejność pierwszeństwa.

1. Jeśli jeden z operandów jest typu `long double`, to drugi operand jest konwertowany na typ `long double`.

1. Jeśli powyższy warunek nie jest spełniony i jeden z operandów jest typu **double**, to drugi operand jest konwertowany na typ **double**.

1. Jeśli dwa powyższe warunki nie są spełnione i jeden z operandów jest typu **float**, to drugi operand jest konwertowany na typ **float**.

1. Jeśli trzy powyższe warunki nie są spełnione (żaden z operandów jest typu zmiennoprzecinkowego), a następnie konwersje wartości całkowitych są wykonywane na operandach w następujący sposób:

   - Jeśli jeden z operandów jest typu `unsigned long`, to drugi operand jest konwertowany na typ `unsigned long`.

   - Jeśli powyższy warunek nie jest spełniony i jeden z operandów jest typu **długie** i drugą typu `unsigned int`, oba operandy są konwertowane na typ `unsigned long`.

   - Jeśli dwa powyższe warunki nie są spełnione i jeden z operandów jest typu **długie**, to drugi operand jest konwertowany na typ **długie**.

   - Jeśli trzy powyższe warunki nie są spełnione i jeden z operandów jest typu `unsigned int`, to drugi operand jest konwertowany na typ `unsigned int`.

   - Jeśli żaden z powyższych warunków nie jest spełniony, oba operandy są konwertowane na typ `int`.

Poniższy kod ilustruje te reguły konwersji:

```
float   fVal;
double  dVal;
int   iVal;
unsigned long ulVal;

dVal = iVal * ulVal; /* iVal converted to unsigned long
                      * Uses step 4.
                      * Result of multiplication converted to double
                      */
dVal = ulVal + fVal; /* ulVal converted to float
                      * Uses step 3.
                      * Result of addition converted to double
                      */
```

## <a name="see-also"></a>Zobacz też

[Operatory języka C](../c-language/c-operators.md)