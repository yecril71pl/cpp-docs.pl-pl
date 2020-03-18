---
title: Manipulowanie buforem
ms.date: 04/04/2018
helpviewer_keywords:
- buffers, manipulation routines
- buffers
ms.assetid: 164f4860-ce66-412c-8291-396fbd70f03e
ms.openlocfilehash: a79bfdb33d2bff5e18c916a2e116ab03251afdf1
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/17/2020
ms.locfileid: "79443587"
---
# <a name="buffer-manipulation"></a>Manipulowanie buforem

Te procedury służą do pracy z obszarami pamięci w oparciu o bajt po bajcie.

## <a name="buffer-manipulation-routines"></a>Procedury manipulowania buforem

|Procedura|Użycie|
|-------------|---------|
|[_memccpy](../c-runtime-library/reference/memccpy.md)|Kopiuj znaki z jednego buforu do innego do momentu skopiowania danego znaku lub podanej liczby znaków|
|[memchr, wmemchr](../c-runtime-library/reference/memchr-wmemchr.md)|Zwróć wskaźnik do pierwszego wystąpienia w określonej liczbie znaków, danego znaku w buforze|
|[memcmp, wmemcmp](../c-runtime-library/reference/memcmp-wmemcmp.md)|Porównaj określoną liczbę znaków z dwóch buforów|
|[memcpy, wmemcpy](../c-runtime-library/reference/memcpy-wmemcpy.md), [memcpy_s, wmemcpy_s](../c-runtime-library/reference/memcpy-s-wmemcpy-s.md)|Kopiuj określoną liczbę znaków z jednego buforu do innego|
|[_memicmp, _memicmp_l](../c-runtime-library/reference/memicmp-memicmp-l.md)|Porównaj określoną liczbę znaków z dwóch buforów bez względu na wielkość liter|
|[memmove, wmemmove](../c-runtime-library/reference/memmove-wmemmove.md),[memmove_s, wmemmove_s](../c-runtime-library/reference/memmove-s-wmemmove-s.md)|Kopiuj określoną liczbę znaków z jednego buforu do innego|
|[memset, wmemset](../c-runtime-library/reference/memset-wmemset.md)|Użyj danego znaku, aby zainicjować określoną liczbę bajtów w buforze|
|[_swab](../c-runtime-library/reference/swab.md)|Zamień bajty danych i Zapisz je w określonej lokalizacji|

Gdy obszary źródłowe i docelowe nakładają się na siebie, tylko **memmove** jest gwarantowane, że pełne źródło zostanie prawidłowo skopiowane.

## <a name="see-also"></a>Zobacz też

[Procedury czasu wykonywania języka Universal C według kategorii](../c-runtime-library/run-time-routines-by-category.md)
