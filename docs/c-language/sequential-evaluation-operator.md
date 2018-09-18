---
title: Operator obliczania sekwencyjnego | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- operators [C++], sequential-evaluation
- sequential-evaluation operator
- comma operator
ms.assetid: 587514f4-c8e2-44e9-81a8-7a553ce1453a
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: a285cc87ec4182586663afcb3559101167ae7261
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46095576"
---
# <a name="sequential-evaluation-operator"></a>Operator obliczania sekwencyjnego

Operator obliczania sekwencyjnego, nazywany również "operator przecinka," ocenia dwóch argumentów operacji sekwencyjnie od lewej do prawej.

## <a name="syntax"></a>Składnia

*wyrażenie*: *wyrażenia przypisania*

*wyrażenie***,***wyrażenia przypisania*

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

## <a name="see-also"></a>Zobacz też

[Operator przecinkowy: ,](../cpp/comma-operator.md)