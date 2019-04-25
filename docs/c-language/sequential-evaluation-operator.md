---
title: Operator obliczania sekwencyjnego
ms.date: 11/04/2016
helpviewer_keywords:
- operators [C++], sequential-evaluation
- sequential-evaluation operator
- comma operator
ms.assetid: 587514f4-c8e2-44e9-81a8-7a553ce1453a
ms.openlocfilehash: 2cbffc51fb7113ae442dbfcd1db01bbf27a67746
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62158524"
---
# <a name="sequential-evaluation-operator"></a>Operator obliczania sekwencyjnego

Operator obliczania sekwencyjnego, nazywany również "operator przecinka," ocenia dwóch argumentów operacji sekwencyjnie od lewej do prawej.

## <a name="syntax"></a>Składnia

*expression*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*assignment-expression*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*wyrażenie* **,** *wyrażenia przypisania*

Lewy operand operator obliczania sekwencyjnego zostało ocenione jako `void` wyrażenia. Wynik operacji ma ten sam wartość i typ jako prawy operand. Każdy argument może być dowolnego typu. Operator obliczania sekwencyjnego nie wykonuje konwersje typów swoich argumentów, a nie przekazuje on l wartością. Po pierwszego operandu, co oznacza, że wszystkie efekty uboczne z oceny lewy operand odbywa się przed rozpoczęciem obliczania prawy operand jest punkt sekwencji. Zobacz [punktów sekwencji](../c-language/c-sequence-points.md) Aby uzyskać więcej informacji.

Operator obliczania sekwencyjnego zazwyczaj jest używane do oceny co najmniej dwóch wyrażeń w kontekstach, których jest dozwolone tylko jedno wyrażenie.

Przecinki może służyć jako separatorów w niektórych kontekstach. Jednakże należy zachować ostrożność nie należy mylić użycie przecinka jako separatora przy jego użyciu jako operator; używa dwóch całkowicie różnią się.

## <a name="example"></a>Przykład

Ten przykład ilustruje operator obliczania sekwencyjnego:

```
for ( i = j = 1; i + j < 20; i += i, j-- );
```

W tym przykładzie każdy argument operacji **dla** instrukcji trzeci jest obliczane wyrażenie niezależnie. Lewy operand `i += i` jest pierwszy ocenione, a następnie prawy operand `j--`, jest obliczane.

```
func_one( x, y + 2, z );
func_two( (x--, y + 2), z );
```

W funkcji wywołanie `func_one`, trzech argumentów, oddzielając je średnikami, są przekazywane: `x`, `y + 2`, i `z`. W funkcji wywołanie `func_two`, nawiasy wymuszają na kompilatorze interpretowanie przecinkiem jako operator obliczania sekwencyjnego. Wywołanie tej funkcji przekazuje dwa argumenty `func_two`. Pierwszy argument jest wynikiem operacji obliczania sekwencyjnego `(x--, y + 2)`, który ma wartość i typ wyrażenia `y + 2`; drugi argument funkcji jest `z`.

## <a name="see-also"></a>Zobacz także

[Operator przecinkowy: ,](../cpp/comma-operator.md)
