---
title: Konwersje z innych typów
ms.date: 01/29/2018
helpviewer_keywords:
- values, converting
- type casts, conversion
ms.assetid: 30fbd974-8f5a-4b70-ac44-d3937b96b702
ms.openlocfilehash: f9f2d73e57c576dcf8afed008a74e5e7dd9b9d6f
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62312469"
---
# <a name="conversions-from-other-types"></a>Konwersje z innych typów

Ponieważ wartość **wyliczenia** jest wartością **int** według definicji, konwersje do i z wartości **wyliczenia** są takie same jak dla typu **int** . Dla kompilatora Microsoft C, liczba całkowita jest taka sama jak **Long**.

**Specyficzne dla firmy Microsoft**

Nie można wykonywać konwersji między typami struktury lub Unii.

Dowolna wartość może zostać przekonwertowana na typ **void**, ale wynik takiej konwersji może być używany tylko w kontekście, w którym jest odrzucana wartość wyrażenia, na przykład w instrukcji wyrażenia.

Typ **void** nie ma wartości według definicji. W związku z tym nie można go przekonwertować na inny typ, a inne typy nie mogą być konwertowane na typ **void** przez przypisanie. Można jednak jawnie rzutować wartość na typ **void**, jak opisano w [konwersji rzutowania typu](../c-language/type-cast-conversions.md).

**ZAKOŃCZENIE określonych przez firmę Microsoft**

## <a name="see-also"></a>Zobacz też

[Konwersje przypisań](../c-language/assignment-conversions.md)
