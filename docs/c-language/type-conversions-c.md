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

Konwersje typów zależą od określonego operatora i typu operandu lub operatorów. Konwersje typów są wykonywane w następujących przypadkach:

- Gdy wartość jednego typu jest przypisana do zmiennej innego typu lub operator konwertuje typ operandu lub operandów przed wykonaniem operacji

- Gdy wartość jednego typu jest jawnie rzutowana na inny typ

- Gdy wartość jest przekazana jako argument do funkcji lub gdy typ jest zwracany przez funkcję

Znak, krótka liczba całkowita lub pole bitowe całkowite, wszystkie podpisane lub Nielub obiekt typu wyliczeniowy, może być używane w wyrażeniu wszędzie tam, gdzie można użyć liczby całkowitej. Jeśli `int` może reprezentować wszystkie wartości oryginalnego typu, wartość zostanie przekonwertowana na `int`; w przeciwnym razie jest konwertowany na `unsigned int`. Ten proces jest nazywany "promocją integralną". Wartość zachowywania całkowitych promocji. Oznacza to, że wartość po podwyższeniu poziomu jest taka sama jak przed podwyższeniem poziomu. Aby uzyskać więcej informacji, zobacz [typowe konwersje arytmetyczne](../c-language/usual-arithmetic-conversions.md) .

## <a name="see-also"></a>Zobacz też

[Wyrażenia i przydziały](../c-language/expressions-and-assignments.md)
