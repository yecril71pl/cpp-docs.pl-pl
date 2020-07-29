---
title: Konwersje z innych typów
ms.date: 01/29/2018
helpviewer_keywords:
- values, converting
- type casts, conversion
ms.assetid: 30fbd974-8f5a-4b70-ac44-d3937b96b702
ms.openlocfilehash: bd00bbb8944a0273163fa0c5952be510c9dd697c
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/27/2020
ms.locfileid: "87200338"
---
# <a name="conversions-from-other-types"></a>Konwersje z innych typów

Ponieważ **`enum`** wartość jest **`int`** wartością według definicji, konwersje do i z **`enum`** wartości są takie same jak dla **`int`** typu. Dla kompilatora Microsoft C, liczba całkowita jest taka sama jak **`long`** .

**Specyficzne dla firmy Microsoft**

Nie można wykonywać konwersji między typami struktury lub Unii.

Dowolna wartość może zostać przekonwertowana na typ **`void`** , ale wynik takiej konwersji może być używany tylko w kontekście, w którym jest odrzucana wartość wyrażenia, na przykład w instrukcji wyrażenia.

**`void`** Typ nie ma wartości według definicji. W związku z tym nie można go przekonwertować na inny typ, a inne typy nie mogą być konwertowane na **`void`** przez przypisanie. Można jednak jawnie rzutować wartość na typ **`void`** , jak opisano w [konwersji rzutowania typu](../c-language/type-cast-conversions.md).

**ZAKOŃCZENIE określonych przez firmę Microsoft**

## <a name="see-also"></a>Zobacz także

[Konwersje przypisań](../c-language/assignment-conversions.md)
