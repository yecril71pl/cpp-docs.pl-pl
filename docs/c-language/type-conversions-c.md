---
title: Konwersje typu (C)
ms.date: 11/04/2016
helpviewer_keywords:
- conversions, type
- type conversion
- converting types
- integral promotions
- type casts, when performed
ms.assetid: d130ee7c-03c3-48f4-af7b-1fdba0d3b086
ms.openlocfilehash: 281234b857a97acbb57ebbfca7b678a637d00764
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62346291"
---
# <a name="type-conversions-c"></a>Konwersje typu (C)

Konwersje typów są zależne od określonego operatora i typu argumentu lub operatorów. Konwersje są wykonywane w następujących przypadkach:

- Wartości typu jeden jest przypisany do zmiennej innego typu lub operator konwertuje typ jej operand lub operandy przed wykonaniem operacji

- Kiedy wartości z jednego typu jest jawnie rzutowane na inny typ.

- Gdy wartość jest przekazywany jako argument do funkcji lub gdy typem jest zwracany przez funkcję

Znak, krótka liczba całkowita lub pola bitowe liczba całkowita, wszystkie podpisana lub nie, lub obiekt typu wyliczenia, może być używany w wyrażeniu, wszędzie tam, gdzie można użyć liczby całkowitej. Jeśli `int` może reprezentować wszystkie wartości oryginalnego typu, a następnie wartość jest konwertowana na `int`; w przeciwnym razie jest konwertowany na `unsigned int`. Ten proces jest nazywany "promocją typu całkowitego". Promocje typów całkowitych zachować wartość. Oznacza to, że wartość po promocji może być taka sama, jak na samym podwyższeniu. Zobacz [zwykle konwersje arytmetyczne](../c-language/usual-arithmetic-conversions.md) Aby uzyskać więcej informacji.

## <a name="see-also"></a>Zobacz także

[Wyrażenia i przydziały](../c-language/expressions-and-assignments.md)
