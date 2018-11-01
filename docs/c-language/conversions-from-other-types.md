---
title: Konwersje z innych typów
ms.date: 01/29/2018
helpviewer_keywords:
- values, converting
- type casts, conversion
ms.assetid: 30fbd974-8f5a-4b70-ac44-d3937b96b702
ms.openlocfilehash: f9f2d73e57c576dcf8afed008a74e5e7dd9b9d6f
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50448662"
---
# <a name="conversions-from-other-types"></a>Konwersje z innych typów

Ponieważ **wyliczenia** wartość **int** wartość zgodnie z definicją, konwersje do i z **wyliczenia** wartości są takie same jak w przypadku **int** typu. Dla kompilatora Microsoft C, liczba całkowita jest taka sama jak **długie**.

**Microsoft Specific**

Nie konwersji między typami struktury lub Unii są dozwolone.

Każda wartość może zostać przekonwertowana na typ **void**, ale wynik konwersji elementu mogą być używane wyłącznie w kontekście wartości wyrażenia w przypadku odrzuconych, na przykład instrukcja wyrażenia.

**Void** typu nie ma wartości, zgodnie z definicją. Dlatego nie można przekonwertować żadnego innego typu i innych typów, nie można przekonwertować na **void** przez przypisanie. Jednak jawne Rzutowanie wartości na typ **void**, zgodnie z opisem w [konwersje rzutowania typów](../c-language/type-cast-conversions.md).

**END specyficzny dla Microsoft**

## <a name="see-also"></a>Zobacz także

[Konwersje przypisań](../c-language/assignment-conversions.md)
