---
title: Manipulowanie buforem
ms.date: 04/04/2018
f1_keywords:
- c.memory
helpviewer_keywords:
- buffers, manipulation routines
- buffers
ms.assetid: 164f4860-ce66-412c-8291-396fbd70f03e
ms.openlocfilehash: e8a449cbfa6a52ccc2346e2215ce187c09d677e9
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62290394"
---
# <a name="buffer-manipulation"></a>Manipulowanie buforem

Użyj tych procedur, aby pracować z obszary pamięci na podstawie bajt po bajcie.

## <a name="buffer-manipulation-routines"></a>Manipulowanie buforem procedury

|Procedura|Zastosowanie|
|-------------|---------|
|[_memccpy](../c-runtime-library/reference/memccpy.md)|Kopiowanie znaków z buforu na inny do momentu danego znaku lub daną liczbę znaków, które zostały skopiowane|
|[memchr, wmemchr](../c-runtime-library/reference/memchr-wmemchr.md)|Zwraca wskaźnik do pierwszego wystąpienia w ciągu określonej liczby znaków, z danego znaku w buforze|
|[memcmp, wmemcmp](../c-runtime-library/reference/memcmp-wmemcmp.md)|Porównaj określoną liczbę znaków z dwóch buforów|
|[memcpy, wmemcpy —](../c-runtime-library/reference/memcpy-wmemcpy.md), [memcpy_s —, wmemcpy_s —](../c-runtime-library/reference/memcpy-s-wmemcpy-s.md)|Kopiuj określoną liczbę znaków z buforu na inny|
|[_memicmp, _memicmp_l](../c-runtime-library/reference/memicmp-memicmp-l.md)|Porównaj określoną liczbę znaków z dwóch buforów bez uwzględniania wielkości liter|
|[memmove, wmemmove —](../c-runtime-library/reference/memmove-wmemmove.md),[memmove_s —, wmemmove_s —](../c-runtime-library/reference/memmove-s-wmemmove-s.md)|Kopiuj określoną liczbę znaków z buforu na inny|
|[memset, wmemset](../c-runtime-library/reference/memset-wmemset.md)|Użycie danego znaku, aby zainicjować określoną liczbę bajtów w buforze|
|[_swab](../c-runtime-library/reference/swab.md)|Wymiana bajtów danych i przechowywać je w określonej lokalizacji|

Gdy obszary źródłowe i docelowe nakładają się, tylko **memmove** jest gwarantowane, skopiować pełną źródła poprawnie.

## <a name="see-also"></a>Zobacz także

[Procedury czasu wykonywania języka Universal C według kategorii](../c-runtime-library/run-time-routines-by-category.md)
