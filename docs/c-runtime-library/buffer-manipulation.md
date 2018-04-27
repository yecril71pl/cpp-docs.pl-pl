---
title: Bufor manipulowania | Dokumenty Microsoft
ms.custom: ''
ms.date: 04/04/2018
ms.technology:
- cpp-standard-libraries
ms.topic: article
f1_keywords:
- c.memory
dev_langs:
- C++
helpviewer_keywords:
- buffers, manipulation routines
- buffers
ms.assetid: 164f4860-ce66-412c-8291-396fbd70f03e
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: aaa85b3e3f0730a564ac1aff3e74f58cef20356a
ms.sourcegitcommit: ef859ddf5afea903711e36bfd89a72389a12a8d6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/20/2018
---
# <a name="buffer-manipulation"></a>Manipulowanie buforem

Użyj tych procedur do pracy z obszary pamięci na podstawie po bicie.

## <a name="buffer-manipulation-routines"></a>Manipulowanie buforem procedury

|Procedura|Zastosowanie|
|-------------|---------|
|[_memccpy](../c-runtime-library/reference/memccpy.md)|Kopiowanie znaków z buforu do innego dopóki podany znak lub został skopiowany podana liczba znaków|
|[memchr, wmemchr](../c-runtime-library/reference/memchr-wmemchr.md)|Zwraca wskaźnik do pierwszego wystąpienia, w ciągu określonej liczby znaków, z podany znak w buforze|
|[memcmp, wmemcmp](../c-runtime-library/reference/memcmp-wmemcmp.md)|Porównanie określoną liczbę znaków z dwóch buforów|
|[memcpy, wmemcpy —](../c-runtime-library/reference/memcpy-wmemcpy.md), [memcpy_s —, wmemcpy_s —](../c-runtime-library/reference/memcpy-s-wmemcpy-s.md)|Skopiuj określoną liczbę znaków z buforu na inny|
|[_memicmp, _memicmp_l](../c-runtime-library/reference/memicmp-memicmp-l.md)|Porównanie określoną liczbę znaków z dwóch buforów bez uwzględniania wielkości liter|
|[memmove —, wmemmove —](../c-runtime-library/reference/memmove-wmemmove.md),[memmove_s —, wmemmove_s —](../c-runtime-library/reference/memmove-s-wmemmove-s.md)|Skopiuj określoną liczbę znaków z buforu na inny|
|[memset, wmemset](../c-runtime-library/reference/memset-wmemset.md)|Użyj danego znaku zainicjować określoną liczbę bajtów w buforze|
|[_swab](../c-runtime-library/reference/swab.md)|Wymiana bajtów danych i zapisywania ich w określonej lokalizacji|

Gdy obszary źródłowe i docelowe nakładają się, tylko **memmove —** może skopiować pełną źródła poprawnie.

## <a name="see-also"></a>Zobacz także

[Universal C procedury czasu wykonywania według kategorii](../c-runtime-library/run-time-routines-by-category.md)
