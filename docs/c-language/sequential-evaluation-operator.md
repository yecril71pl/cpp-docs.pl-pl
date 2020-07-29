---
title: Operator obliczania sekwencyjnego
ms.date: 11/04/2016
helpviewer_keywords:
- operators [C++], sequential-evaluation
- sequential-evaluation operator
- comma operator
ms.assetid: 587514f4-c8e2-44e9-81a8-7a553ce1453a
ms.openlocfilehash: ec2c866b512bc0b398375041b03c0ea697d3a0d2
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/27/2020
ms.locfileid: "87227780"
---
# <a name="sequential-evaluation-operator"></a>Operator obliczania sekwencyjnego

Operator sekwencyjnej oceny, nazywany także "operatorem przecinkowym", ocenia dwa operandy sekwencyjnie od lewej do prawej.

## <a name="syntax"></a>Składnia

*wyrażenie*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*przypisanie — wyrażenie*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*wyrażenie* **,** *przypisanie — wyrażenie*

Lewy operand operatora sekwencyjnej oceny jest obliczany jako **`void`** wyrażenie. Wynik operacji ma taką samą wartość i typ jak prawy operand. Każdy operand może być dowolnego typu. Operator sekwencyjnej oceny nie wykonuje konwersji typu między operandami i nie zwraca wartości l. Po pierwszym operandzie istnieje punkt sekwencji, co oznacza, że wszystkie efekty uboczne z obliczenia lewego operandu są kończone przed rozpoczęciem obliczania prawego operandu. Zobacz [punkty sekwencji](../c-language/c-sequence-points.md) , aby uzyskać więcej informacji.

Operator sekwencyjnej oceny jest zazwyczaj używany do oceny dwóch lub więcej wyrażeń w kontekstach, w których dozwolone jest tylko jedno wyrażenie.

Przecinki mogą być używane jako separatory w niektórych kontekstach. Jednakże należy zachować ostrożność, aby nie mylić użycia przecinka jako separatora przy użyciu jako operatora; te dwa zastosowania są całkowicie różne.

## <a name="example"></a>Przykład

Ten przykład ilustruje operator sekwencyjnej oceny:

```
for ( i = j = 1; i + j < 20; i += i, j-- );
```

W tym przykładzie każdy operand **`for`** trzeciego wyrażenia instrukcji jest oceniane niezależnie. Lewy operand `i += i` jest oceniany jako pierwszy, a następnie `j--` jest obliczany prawy operand,,.

```
func_one( x, y + 2, z );
func_two( (x--, y + 2), z );
```

W wywołaniu funkcji do `func_one` , trzy argumenty, oddzielone przecinkami, są przenoszone: `x` , `y + 2` , i `z` . W wywołaniu funkcji do `func_two` , nawiasy wymuszają, aby kompilator interpretował pierwszy przecinek jako operator oceny sekwencyjnej. To wywołanie funkcji przekazuje dwa argumenty do `func_two` . Pierwszy argument jest wynikiem operacji sekwencyjnej oceny `(x--, y + 2)` , która ma wartość i typ wyrażenia `y + 2` ; drugim argumentem jest `z` .

## <a name="see-also"></a>Zobacz także

[Operator przecinkowy:,](../cpp/comma-operator.md)
