---
title: "_aligned_offset_recalloc_dbg — | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apiname: _aligned_offset_recalloc_dbg
apilocation:
- msvcrt.dll
- msvcr80.dll
- msvcr90.dll
- msvcr100.dll
- msvcr100_clr0400.dll
- msvcr110.dll
- msvcr110_clr0400.dll
- msvcr120.dll
- msvcr120_clr0400.dll
- ucrtbase.dll
apitype: DLLExport
f1_keywords:
- aligned_offset_recalloc_dbg
- _aligned_offset_recalloc_dbg
dev_langs: C++
helpviewer_keywords:
- aligned_offset_recalloc_dbg function
- _aligned_offset_recalloc_dbg function
ms.assetid: 7ab719c3-77e0-4d2e-934f-01529d062fbf
caps.latest.revision: "9"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 8701f2e2a52603f08727220e2638f06cc40b7aec
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="alignedoffsetrecallocdbg"></a>_aligned_offset_recalloc_dbg
Zmienia rozmiar blok pamięci przydzielony przy [_aligned_malloc —](../../c-runtime-library/reference/aligned-malloc.md) lub [_aligned_offset_malloc —](../../c-runtime-library/reference/aligned-offset-malloc.md) i inicjuje pamięci 0 (tylko wersja do debugowania).  
  
## <a name="syntax"></a>Składnia  
  
```  
void * _aligned_offset_recalloc_dbg(  
   void *memblock,   
   size_t num,   
   size_t size,   
   size_t alignment,  
   size_t offset,  
   const char *filename,  
   int linenumber  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 [in]`memblock`  
 Bieżący wskaźnik bloku pamięci.  
  
 [in]`num`  
 Liczba elementów.  
  
 [in]`size`  
 Długość w bajtach każdego elementu.  
  
 [in]`alignment`  
 Wartość wyrównania, która musi być całkowitą potęgą liczby 2.  
  
 [in]`offset`  
 Przesunięcie alokacji pamięci, aby wymusić wyrównanie.  
  
 [in]`filename`  
 Wskaźnik do nazwy pliku źródłowego, który zażądał `realloc` operacji ani mieć wartości NULL.  
  
 [in]`linenumber`  
 Numer wiersza na plik źródłowy gdzie `realloc` operacja była żądana ani mieć wartości NULL.  
  
## <a name="return-value"></a>Wartość zwracana  
 `_aligned_offset_recalloc_dbg`Zwraca typ void wskaźnik do bloku pamięci przydzielić (i prawdopodobnie przenoszenia). Wartość zwracana jest `NULL` rozmiar wynosi zero, jeśli argument bufor nie jest `NULL`, lub jeśli nie ma dostatecznej ilości dostępnej pamięci, aby rozwinąć blok na dany rozmiar. W pierwszym przypadku oryginalnego bloku zostanie zwolniona. W drugim przypadku oryginalnego bloku jest bez zmian. Wartości zwracanej wskazuje miejsce do magazynowania, które na pewno jest odpowiednio dopasowany do przechowywania obiekty dowolnego typu. Aby uzyskać wskaźnik do typu innego niż void, użyj typu rzutowania wartości zwracanej.  
  
## <a name="remarks"></a>Uwagi  
 `_aligned_offset_realloc_dbg`jest to wersja debugowania [_aligned_offset_recalloc —](../../c-runtime-library/reference/aligned-offset-recalloc.md) funkcji. Gdy [_DEBUG](../../c-runtime-library/debug.md) nie jest zdefiniowana, każde wywołanie `_aligned_offset_recalloc_dbg` zostanie zmniejszona do wywołania `_aligned_offset_recalloc`. Zarówno `_aligned_offset_recalloc` i `_aligned_offset_recalloc_dbg` ponownie przydzielić bloku pamięci w stercie podstawowy, ale `_aligned_offset_recalloc_dbg` bierze pod uwagę kilka funkcji debugowania: buforów po obu stronach części bloku do testowania przecieki, parametr typu bloku do śledzenia określonego użytkownika typy alokacji i `filename` / `linenumber` informacji do ustalenia źródła żądań alokacji.  
  
 `_aligned_offset_realloc_dbg`przydziela ponownie bloku pamięci określony nieco więcej miejsca niż żądany `newSize`. `newSize`może być większa lub mniejsza niż rozmiar bloku pierwotnie alokacji pamięci. Dodatkowe miejsce jest używane przez menedżera stosu debugowania, do łączenia bloków pamięci debugowania i do dostarczenia aplikacji informacji nagłówka debugowania i zastąpienia buforów. Ponowne przydzielenie może spowodować przeniesienie do innej lokalizacji w stercie oryginalnego bloku pamięci, jak również zmiana rozmiaru bloku pamięci. Jeśli blok pamięci jest przenoszony, zawartość oryginalnego bloku zostaną zastąpione.  
  
 Ta funkcja ustawia `errno` do `ENOMEM` czy alokacja pamięci nie powiodła się, czy żądany rozmiar (`num` * `size`) była większa niż `_HEAP_MAXREQ`. Aby uzyskać więcej informacji na temat `errno`, zobacz [errno _doserrno —, _sys_errlist — i _sys_nerr —](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md). `_aligned_offset_recalloc_dbg` również sprawdza poprawność parametrów. Jeśli `alignment` nie jest potęgą liczby 2 lub, jeśli `offset` jest większa niż lub równa żądany rozmiar i różną od zera, ta funkcja wywołuje program obsługi nieprawidłowych parametrów, zgodnie z opisem w [sprawdzanie poprawności parametru](../../c-runtime-library/parameter-validation.md). Jeśli jest dozwolone wykonywanie, aby kontynuować, ta funkcja zwraca `NULL` i ustawia `errno` do `EINVAL`.  
  
 Aby dowiedzieć się jak bloki pamięci są przydzielone, zainicjować i zarządzane w wersji podstawowej sterty debugowania, zobacz [szczegóły dotyczące sterty debugowania CRT](/visualstudio/debugger/crt-debug-heap-details). Informacje o typach bloku alokacji i sposobu ich używania, zobacz [typów bloków w stercie debugowania](/visualstudio/debugger/crt-debug-heap-details). Aby uzyskać informacje o różnicach między wywoływanie funkcji sterty standardowe i jego wersji do debugowania w kompilację debugowania aplikacji, zobacz [debugowania wersji z funkcji alokacji sterty](/visualstudio/debugger/debug-versions-of-heap-allocation-functions).  
  
## <a name="requirements"></a>Wymagania  
  
|Procedura|Wymagany nagłówek|  
|-------------|---------------------|  
|`_aligned_offset_recalloc_dbg`|\<malloc.h >|  
  
## <a name="see-also"></a>Zobacz też  
 [Wyrównywanie danych](../../c-runtime-library/data-alignment.md)