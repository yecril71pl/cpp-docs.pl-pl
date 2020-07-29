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
ms.openlocfilehash: 7d7c55c15a8f3e2a53e350da947cf524ae064a09
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/27/2020
ms.locfileid: "87231432"
---
# <a name="type-conversions-c"></a>Konwersje typu (C)

Konwersje typów zależą od określonego operatora i typu operandu lub operatorów. Konwersje typów są wykonywane w następujących przypadkach:

- Gdy wartość jednego typu jest przypisana do zmiennej innego typu lub operator konwertuje typ operandu lub operandów przed wykonaniem operacji

- Gdy wartość jednego typu jest jawnie rzutowana na inny typ

- Gdy wartość jest przekazana jako argument do funkcji lub gdy typ jest zwracany przez funkcję

Znak, krótka liczba całkowita lub pole bitowe całkowite, wszystkie podpisane lub Nielub obiekt typu wyliczeniowy, może być używane w wyrażeniu wszędzie tam, gdzie można użyć liczby całkowitej. Jeśli **`int`** może reprezentować wszystkie wartości oryginalnego typu, wartość jest konwertowana na **`int`** ; w przeciwnym razie jest konwertowana na **`unsigned int`** . Ten proces jest nazywany "promocją integralną". Wartość zachowywania całkowitych promocji. Oznacza to, że wartość po podwyższeniu poziomu jest taka sama jak przed podwyższeniem poziomu. Aby uzyskać więcej informacji, zobacz [typowe konwersje arytmetyczne](../c-language/usual-arithmetic-conversions.md) .

## <a name="see-also"></a>Zobacz także

[Wyrażenia i przydziały](../c-language/expressions-and-assignments.md)
