---
title: "Wyrównywanie danych | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: data.alignment
dev_langs: C++
helpviewer_keywords: data alignment [C++]
ms.assetid: 35ac3d2d-a4b3-421b-954f-b7372b1f18e1
caps.latest.revision: "9"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 2dcbb5c484e92089f7a669426b9a6727d205b45d
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="data-alignment"></a>Wyrównywanie danych
Następujące funkcje wykonawcze języka C obsługują wyrównanie danych.  
  
### <a name="data-alignment-routines"></a>Wyrównywanie danych procedury  
  
|Procedura|Zastosowanie|  
|-------------|---------|  
|[_aligned_free —](../c-runtime-library/reference/aligned-free.md)|Zwalnia blok pamięci przydzielony przy [_aligned_malloc —](../c-runtime-library/reference/aligned-malloc.md)lub [_aligned_offset_malloc —](../c-runtime-library/reference/aligned-offset-malloc.md).|  
|[_aligned_free_dbg —](../c-runtime-library/reference/aligned-free-dbg.md)|Zwalnia blok pamięci przydzielony przy [_aligned_malloc —](../c-runtime-library/reference/aligned-malloc.md) lub [_aligned_offset_malloc —](../c-runtime-library/reference/aligned-offset-malloc.md) (tylko debugowanie).|  
|[_aligned_malloc —](../c-runtime-library/reference/aligned-malloc.md)|Przydziela pamięć na określonej granicy wyrównania.|  
|[_aligned_malloc_dbg —](../c-runtime-library/reference/aligned-malloc-dbg.md)|Przydziela pamięć na określonej granicy wyrównania z dodatkowym miejscem dla nagłówka debugowania i zastąpić buforów (tylko wersja do debugowania).|  
|[_aligned_msize —](../c-runtime-library/reference/aligned-msize.md)|Zwraca rozmiar bloku pamięci przydzielić w stercie.|  
|[_aligned_msize_dbg](../c-runtime-library/reference/aligned-msize-dbg.md)|Zwraca rozmiar bloku pamięci przydzielić w stercie (tylko wersja do debugowania).|  
|[_aligned_offset_malloc —](../c-runtime-library/reference/aligned-offset-malloc.md)|Przydziela pamięć na określonej granicy wyrównania.|  
|[_aligned_offset_malloc_dbg —](../c-runtime-library/reference/aligned-offset-malloc-dbg.md)|Przydziela pamięć na określonej granicy wyrównania (tylko w wersji do debugowania).|  
|[_aligned_offset_realloc —](../c-runtime-library/reference/aligned-offset-realloc.md)|Zmienia rozmiar blok pamięci przydzielony przy [_aligned_malloc —](../c-runtime-library/reference/aligned-malloc.md) lub [_aligned_offset_malloc —](../c-runtime-library/reference/aligned-offset-malloc.md).|  
|[_aligned_offset_realloc_dbg —](../c-runtime-library/reference/aligned-offset-realloc-dbg.md)|Zmienia rozmiar blok pamięci przydzielony przy [_aligned_malloc —](../c-runtime-library/reference/aligned-malloc.md) lub [_aligned_offset_malloc —](../c-runtime-library/reference/aligned-offset-malloc.md) (tylko wersja do debugowania).|  
|[_aligned_offset_recalloc —](../c-runtime-library/reference/aligned-offset-recalloc.md)|Zmienia rozmiar blok pamięci przydzielony przy [_aligned_malloc —](../c-runtime-library/reference/aligned-malloc.md) lub [_aligned_offset_malloc —](../c-runtime-library/reference/aligned-offset-malloc.md) i inicjuje pamięci na 0.|  
|[_aligned_offset_recalloc_dbg —](../c-runtime-library/reference/aligned-offset-recalloc-dbg.md)|Zmienia rozmiar blok pamięci przydzielony przy [_aligned_malloc —](../c-runtime-library/reference/aligned-malloc.md) lub [_aligned_offset_malloc —](../c-runtime-library/reference/aligned-offset-malloc.md) i inicjuje pamięci 0 (tylko wersja do debugowania).|  
|[_aligned_realloc —](../c-runtime-library/reference/aligned-realloc.md)|Zmienia rozmiar blok pamięci przydzielony przy [_aligned_malloc —](../c-runtime-library/reference/aligned-malloc.md) lub [_aligned_offset_malloc —](../c-runtime-library/reference/aligned-offset-malloc.md).|  
|[_aligned_realloc_dbg —](../c-runtime-library/reference/aligned-realloc-dbg.md)|Zmienia rozmiar blok pamięci przydzielony przy [_aligned_malloc —](../c-runtime-library/reference/aligned-malloc.md) lub [_aligned_offset_malloc —](../c-runtime-library/reference/aligned-offset-malloc.md) (tylko wersja do debugowania).|  
|[_aligned_recalloc —](../c-runtime-library/reference/aligned-recalloc.md)|Zmienia rozmiar blok pamięci przydzielony przy [_aligned_malloc —](../c-runtime-library/reference/aligned-malloc.md) lub [_aligned_offset_malloc —](../c-runtime-library/reference/aligned-offset-malloc.md) i inicjuje pamięci na 0.|  
|[_aligned_recalloc_dbg —](../c-runtime-library/reference/aligned-recalloc-dbg.md)|Zmienia rozmiar blok pamięci przydzielony przy [_aligned_malloc —](../c-runtime-library/reference/aligned-malloc.md) lub [_aligned_offset_malloc —](../c-runtime-library/reference/aligned-offset-malloc.md) i inicjuje pamięci 0 (tylko wersja do debugowania).|  
  
## <a name="see-also"></a>Zobacz też  
 [Procedury czasu wykonywania według kategorii](../c-runtime-library/run-time-routines-by-category.md)