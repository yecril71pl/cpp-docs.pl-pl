---
title: "Alokacja pamięci | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: c.memory
dev_langs: C++
helpviewer_keywords:
- memory allocation, routines
- memory, managing
- memory, allocation
ms.assetid: b4470556-a128-4782-9943-2ccf7a7d9979
caps.latest.revision: "10"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: cdaf9fe5b2d41491683d34ea029a546433cd709d
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="memory-allocation"></a>Alokacja pamięci
Użyj tych procedur można przydzielić wolne i ponownie przydzielić pamięci.  
  
### <a name="memory-allocation-routines"></a>Procedury Alokacja pamięci  
  
|Procedura|Zastosowanie|  
|-------------|---------|  
|[_alloca](../c-runtime-library/reference/alloca.md), [_malloca —](../c-runtime-library/reference/malloca.md)|Przydzielenie pamięci ze stosu|  
|[calloc —](../c-runtime-library/reference/calloc.md)|Przydziel magazyn do tablicy, inicjowanie każdego bajtu w bloku przydzielonego na 0|  
|[_calloc_dbg —](../c-runtime-library/reference/calloc-dbg.md)|Debugować wersję `calloc`; dostępne tylko w wersjach debugowania biblioteki wykonawczej|  
|[Usuwanie operatora](../c-runtime-library/operator-delete-crt.md)|Bezpłatne przydzielony blok|  
|[Usuwanie operatora &#91; &#93;](../c-runtime-library/delete-operator-crt.md)|Bezpłatne przydzielony blok|  
|[_rozszerz lokację](../c-runtime-library/reference/expand.md)|Zwiększania lub zmniejszania bloku pamięci bez przenoszenia go|  
|[_expand_dbg —](../c-runtime-library/reference/expand-dbg.md)|Debugować wersję `_expand`; dostępne tylko w wersjach debugowania biblioteki wykonawczej|  
|[w warstwie bezpłatna](../c-runtime-library/reference/free.md)|Bezpłatne przydzielony blok|  
|[_free_dbg —](../c-runtime-library/reference/free-dbg.md)|Debugować wersję `free`; dostępne tylko w wersjach debugowania biblioteki wykonawczej|  
|[_freea —](../c-runtime-library/reference/freea.md)|Bezpłatne przydzielony blok ze stosu|  
|[_get_heap_handle —](../c-runtime-library/reference/get-heap-handle.md)|Pobierz sterty CRT UCHWYT Win32.|  
|[_heapadd —](../c-runtime-library/heapadd.md)|Dodaj więcej pamięci do sterty|  
|[_heapchk —](../c-runtime-library/reference/heapchk.md)|Sprawdzanie sterty spójności|  
|[_heapmin —](../c-runtime-library/reference/heapmin.md)|Zwolnij nieużywanej pamięci w stercie|  
|[_heapset —](../c-runtime-library/heapset.md)|Wypełnij wpisy wolnego sterty określoną wartość|  
|[_heapwalk —](../c-runtime-library/reference/heapwalk.md)|Zwraca informacje dotyczące każdej pozycji w stercie|  
|[— funkcja malloc](../c-runtime-library/reference/malloc.md)|Przydziel bloku pamięci z sterty|  
|[_malloc_dbg —](../c-runtime-library/reference/malloc-dbg.md)|Debugować wersję `malloc`; dostępne tylko w wersjach debugowania biblioteki wykonawczej|  
|[_msize —](../c-runtime-library/reference/msize.md)|Zwraca rozmiar przydzielony blok|  
|[_msize_dbg —](../c-runtime-library/reference/msize-dbg.md)|Debugować wersję `_msize`; dostępne tylko w wersjach debugowania biblioteki wykonawczej|  
|[Nowy](../c-runtime-library/operator-new-crt.md)|Przydziel bloku pamięci z sterty|  
|[Nowy &#91; &#93;](../c-runtime-library/new-operator-crt.md)|Przydziel bloku pamięci z sterty|  
|[_query_new_handler —](../c-runtime-library/reference/query-new-handler.md)|Adres zwrotny bieżącego nowe procedury obsługi zgodnie z ustawieniami`_set_new_handler`|  
|[_query_new_mode —](../c-runtime-library/reference/query-new-mode.md)|Zwracany liczbę całkowitą wskazującą nowy tryb obsługi ustawione przez `_set_new_mode` dla`malloc`|  
|[realloc](../c-runtime-library/reference/realloc.md)|Ponowne przydzielenie bloku do nowego rozmiaru|  
|[_realloc_dbg —](../c-runtime-library/reference/realloc-dbg.md)|Debugować wersję `realloc`; dostępne tylko w wersjach debugowania biblioteki wykonawczej|  
|[_set_new_handler —](../c-runtime-library/reference/set-new-handler.md)|Włączyć mechanizm obsługi błędów podczas `new` operator nie powiedzie się (można przydzielić pamięci) i Włącz kompilacji standardowej biblioteki języka C++|  
|[_set_new_mode —](../c-runtime-library/reference/set-new-mode.md)|Ustaw nowy tryb obsługi dla`malloc`|  
  
## <a name="see-also"></a>Zobacz też  
 [Procedury czasu wykonywania według kategorii](../c-runtime-library/run-time-routines-by-category.md)