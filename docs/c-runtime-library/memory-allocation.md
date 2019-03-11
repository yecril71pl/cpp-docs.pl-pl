---
title: Alokacja pamięci
ms.date: 11/04/2016
f1_keywords:
- c.memory
helpviewer_keywords:
- memory allocation, routines
- memory, managing
- memory, allocation
ms.assetid: b4470556-a128-4782-9943-2ccf7a7d9979
ms.openlocfilehash: bcc9865b149c2289f99f6ee13f31179ae58a15e1
ms.sourcegitcommit: dedd4c3cb28adec3793329018b9163ffddf890a4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/11/2019
ms.locfileid: "57742794"
---
# <a name="memory-allocation"></a>Alokacja pamięci

Użyj tych procedur, aby przydzielić wolnej i ponownego przydzielenia pamięci.

## <a name="memory-allocation-routines"></a>Procedur alokacji pamięci

|Procedura|Zastosowanie|
|-------------|---------|
|[_alloca](../c-runtime-library/reference/alloca.md), [_malloca](../c-runtime-library/reference/malloca.md)|Przydzielanie pamięci ze stosu|
|[calloc](../c-runtime-library/reference/calloc.md)|Przydziel magazyn do tablicy, inicjowanie każdego bajtu przydzielonego bloku na 0|
|[_calloc_dbg](../c-runtime-library/reference/calloc-dbg.md)|Debuguj wersję **calloc**; jest dostępna tylko w wersji debugowania bibliotek wykonawczych|
|[Usuwanie operatora](../c-runtime-library/operator-delete-crt.md)|Zwolnij przydzielony blok|
|[Usuwanie operatora&#91;&#93;](../c-runtime-library/delete-operator-crt.md)|Zwolnij przydzielony blok|
|[_expand](../c-runtime-library/reference/expand.md)|Powiększanie i zmniejszanie bloku pamięci bez przenoszenia go|
|[_expand_dbg](../c-runtime-library/reference/expand-dbg.md)|Debuguj wersję **_rozwiń**; jest dostępna tylko w wersji debugowania bibliotek wykonawczych|
|[free](../c-runtime-library/reference/free.md)|Zwolnij przydzielony blok|
|[_free_dbg](../c-runtime-library/reference/free-dbg.md)|Debuguj wersję **bezpłatne**; jest dostępna tylko w wersji debugowania bibliotek wykonawczych|
|[_freea](../c-runtime-library/reference/freea.md)|Zwolnij przydzielony blok ze stosu|
|[_get_heap_handle](../c-runtime-library/reference/get-heap-handle.md)|Uzyskaj Win32 UCHWYT sterty CRT.|
|[_heapadd](../c-runtime-library/heapadd.md)|Zwiększ ilość pamięci do sterty|
|[_heapchk](../c-runtime-library/reference/heapchk.md)|Sprawdzanie sterty w celu zachowania spójności|
|[_heapmin](../c-runtime-library/reference/heapmin.md)|Zwolnij nieużywanej pamięci w stercie|
|[_heapset](../c-runtime-library/heapset.md)|Wypełnienie wpisy bezpłatne sterty określoną wartość|
|[_heapwalk](../c-runtime-library/reference/heapwalk.md)|Zwraca informacje dotyczące każdej pozycji w stosie|
|[malloc](../c-runtime-library/reference/malloc.md)|Przydzielanie bloków pamięci ze stosu|
|[_malloc_dbg](../c-runtime-library/reference/malloc-dbg.md)|Debuguj wersję **— funkcja malloc**; jest dostępna tylko w wersji debugowania bibliotek wykonawczych|
|[_msize](../c-runtime-library/reference/msize.md)|Zwraca rozmiar zaalokowanego bloku|
|[_msize_dbg](../c-runtime-library/reference/msize-dbg.md)|Debuguj wersję **_msize —**; jest dostępna tylko w wersji debugowania bibliotek wykonawczych|
|[new](../c-runtime-library/operator-new-crt.md)|Przydzielanie bloków pamięci ze stosu|
|[new&#91;&#93;](../c-runtime-library/new-operator-crt.md)|Przydzielanie bloków pamięci ze stosu|
|[_query_new_handler](../c-runtime-library/reference/query-new-handler.md)|Zwraca adres bieżącej nową procedurę obsługi zgodnie z ustawieniem **_set_new_handler**|
|[_query_new_mode](../c-runtime-library/reference/query-new-mode.md)|Zwracany liczbę całkowitą, wskazującą nowy tryb obsługi ustawione przez **_set_new_mode** dla **— funkcja malloc**|
|[realloc](../c-runtime-library/reference/realloc.md)|Ponowne przydzielenie nowy rozmiar bloku|
|[_realloc_dbg](../c-runtime-library/reference/realloc-dbg.md)|Debuguj wersję **realloc**; jest dostępna tylko w wersji debugowania bibliotek wykonawczych|
|[_set_new_handler](../c-runtime-library/reference/set-new-handler.md)|Włącz mechanizm obsługi błędów podczas **nowe** operator nie powiedzie się (na przykład można przydzielić pamięci) i Włącz zbiór standardowych bibliotek C++|
|[_set_new_mode](../c-runtime-library/reference/set-new-mode.md)|Ustaw nowy tryb obsługi dla **— funkcja malloc**|

## <a name="see-also"></a>Zobacz także

[Procedury czasu wykonywania języka Universal C według kategorii](../c-runtime-library/run-time-routines-by-category.md)<br/>
