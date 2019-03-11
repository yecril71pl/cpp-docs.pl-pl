---
title: Wyrównywanie danych
ms.date: 11/04/2016
f1_keywords:
- data.alignment
helpviewer_keywords:
- data alignment [C++]
ms.assetid: 35ac3d2d-a4b3-421b-954f-b7372b1f18e1
ms.openlocfilehash: 92b8df81751e01e655e348d5f090705e5194312b
ms.sourcegitcommit: dedd4c3cb28adec3793329018b9163ffddf890a4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/11/2019
ms.locfileid: "57738809"
---
# <a name="data-alignment"></a>Wyrównywanie danych

Następujące funkcje środowiska wykonawczego języka C obsługuje wyrównanie danych.

## <a name="data-alignment-routines"></a>Wyrównywanie danych procedury

|Procedura|Zastosowanie|
|-------------|---------|
|[_aligned_free](../c-runtime-library/reference/aligned-free.md)|Zwalnia blok pamięci, która została przydzielona za pomocą [_aligned_malloc](../c-runtime-library/reference/aligned-malloc.md)lub [_aligned_offset_malloc —](../c-runtime-library/reference/aligned-offset-malloc.md).|
|[_aligned_free_dbg](../c-runtime-library/reference/aligned-free-dbg.md)|Zwalnia blok pamięci, która została przydzielona za pomocą [_aligned_malloc](../c-runtime-library/reference/aligned-malloc.md) lub [_aligned_offset_malloc —](../c-runtime-library/reference/aligned-offset-malloc.md) (tylko debugowanie).|
|[_aligned_malloc](../c-runtime-library/reference/aligned-malloc.md)|Przydziela pamięć na określonej granicy wyrównania.|
|[_aligned_malloc_dbg](../c-runtime-library/reference/aligned-malloc-dbg.md)|Przydziela pamięć na określonej granicy wyrównania z dodatkowym miejscem dla nagłówka debugowania i zastąpienia buforów (tylko wersja debugowania).|
|[_aligned_msize](../c-runtime-library/reference/aligned-msize.md)|Zwraca rozmiar bloku pamięci przydzielone w stosie.|
|[_aligned_msize_dbg](../c-runtime-library/reference/aligned-msize-dbg.md)|Zwraca rozmiar bloku pamięci przydzielony w stercie (tylko wersja debugowania).|
|[_aligned_offset_malloc](../c-runtime-library/reference/aligned-offset-malloc.md)|Przydziela pamięć na określonej granicy wyrównania.|
|[_aligned_offset_malloc_dbg](../c-runtime-library/reference/aligned-offset-malloc-dbg.md)|Przydziela pamięć na określonej granicy wyrównania (tylko w wersji do debugowania).|
|[_aligned_offset_realloc](../c-runtime-library/reference/aligned-offset-realloc.md)|Zmienia rozmiar bloku pamięci, która została przydzielona za pomocą [_aligned_malloc](../c-runtime-library/reference/aligned-malloc.md) lub [_aligned_offset_malloc —](../c-runtime-library/reference/aligned-offset-malloc.md).|
|[_aligned_offset_realloc_dbg](../c-runtime-library/reference/aligned-offset-realloc-dbg.md)|Zmienia rozmiar bloku pamięci, która została przydzielona za pomocą [_aligned_malloc](../c-runtime-library/reference/aligned-malloc.md) lub [_aligned_offset_malloc —](../c-runtime-library/reference/aligned-offset-malloc.md) (tylko wersja debugowania).|
|[_aligned_offset_recalloc](../c-runtime-library/reference/aligned-offset-recalloc.md)|Zmienia rozmiar bloku pamięci, która została przydzielona za pomocą [_aligned_malloc](../c-runtime-library/reference/aligned-malloc.md) lub [_aligned_offset_malloc —](../c-runtime-library/reference/aligned-offset-malloc.md) i inicjuje pamięć na 0.|
|[_aligned_offset_recalloc_dbg](../c-runtime-library/reference/aligned-offset-recalloc-dbg.md)|Zmienia rozmiar bloku pamięci, która została przydzielona za pomocą [_aligned_malloc](../c-runtime-library/reference/aligned-malloc.md) lub [_aligned_offset_malloc —](../c-runtime-library/reference/aligned-offset-malloc.md) i inicjuje pamięć na 0 (tylko wersja debugowania).|
|[_aligned_realloc](../c-runtime-library/reference/aligned-realloc.md)|Zmienia rozmiar bloku pamięci, która została przydzielona za pomocą [_aligned_malloc](../c-runtime-library/reference/aligned-malloc.md) lub [_aligned_offset_malloc —](../c-runtime-library/reference/aligned-offset-malloc.md).|
|[_aligned_realloc_dbg](../c-runtime-library/reference/aligned-realloc-dbg.md)|Zmienia rozmiar bloku pamięci, która została przydzielona za pomocą [_aligned_malloc](../c-runtime-library/reference/aligned-malloc.md) lub [_aligned_offset_malloc —](../c-runtime-library/reference/aligned-offset-malloc.md) (tylko wersja debugowania).|
|[_aligned_recalloc](../c-runtime-library/reference/aligned-recalloc.md)|Zmienia rozmiar bloku pamięci, która została przydzielona za pomocą [_aligned_malloc](../c-runtime-library/reference/aligned-malloc.md) lub [_aligned_offset_malloc —](../c-runtime-library/reference/aligned-offset-malloc.md) i inicjuje pamięć na 0.|
|[_aligned_recalloc_dbg](../c-runtime-library/reference/aligned-recalloc-dbg.md)|Zmienia rozmiar bloku pamięci, która została przydzielona za pomocą [_aligned_malloc](../c-runtime-library/reference/aligned-malloc.md) lub [_aligned_offset_malloc —](../c-runtime-library/reference/aligned-offset-malloc.md) i inicjuje pamięć na 0 (tylko wersja debugowania).|

## <a name="see-also"></a>Zobacz także

[Procedury czasu wykonywania języka Universal C według kategorii](../c-runtime-library/run-time-routines-by-category.md)<br/>
