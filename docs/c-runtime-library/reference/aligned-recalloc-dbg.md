---
title: "_aligned_recalloc_dbg — | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apiname: _aligned_recalloc_dbg
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
- _aligned_recalloc_dbg
- aligned_recalloc_dbg
dev_langs: C++
helpviewer_keywords:
- aligned_recalloc_dbg function
- _aligned_recalloc_dbg function
ms.assetid: 55c3c27e-561c-4d6b-9bf9-1e34cc556e4b
caps.latest.revision: "7"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: f434c09e22933859b227f2517e124e9ca668e2cf
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="alignedrecallocdbg"></a>_aligned_recalloc_dbg
Zmienia rozmiar blok pamięci przydzielony przy [_aligned_malloc —](../../c-runtime-library/reference/aligned-malloc.md) lub [_aligned_offset_malloc —](../../c-runtime-library/reference/aligned-offset-malloc.md) i inicjuje pamięci 0 (tylko wersja do debugowania).  
  
## <a name="syntax"></a>Składnia  
  
```  
void * _aligned_recalloc_dbg(  
   void * memblock,   
   size_t num,  
   size_t size,   
   size_t alignment,  
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
 Rozmiar w bajtach każdego elementu.  
  
 [in]`alignment`  
 Wartość wyrównania, która musi być całkowitą potęgą liczby 2.  
  
 [in]`filename`  
 Wskaźnik do nazwy pliku źródłowego, który żądanej operacji alokacji lub `NULL`.  
  
 [in]`linenumber`  
 Numer w pliku źródłowym, której zażądano operacji alokacji wiersza lub `NULL`.  
  
## <a name="return-value"></a>Wartość zwracana  
 `_aligned_recalloc_dbg`Zwraca typ void wskaźnik do bloku pamięci przydzielić (i prawdopodobnie przenoszenia). Wartość zwracana jest `NULL` rozmiar wynosi zero, jeśli argument bufor nie jest `NULL`, lub jeśli nie ma dostatecznej ilości dostępnej pamięci, aby rozwinąć blok na dany rozmiar. W pierwszym przypadku oryginalnego bloku zostanie zwolniona. W drugim przypadku oryginalnego bloku jest bez zmian. Wartości zwracanej wskazuje miejsce do magazynowania, które na pewno jest odpowiednio dopasowany do przechowywania obiekty dowolnego typu. Aby uzyskać wskaźnik do typu innego niż void, użyj typu rzutowania wartości zwracanej.  
  
 Jest błędem ponowne przydzielenie pamięci i zmienić wyrównania bloku.  
  
## <a name="remarks"></a>Uwagi  
 `_aligned_recalloc_dbg`jest to wersja debugowania [_aligned_recalloc —](../../c-runtime-library/reference/aligned-recalloc.md) funkcji. Gdy [_DEBUG](../../c-runtime-library/debug.md) nie jest zdefiniowana, każde wywołanie `_aligned_recalloc_dbg` zostanie zmniejszona do wywołania `_aligned_recalloc`. Zarówno `_aligned_recalloc` i `_aligned_recalloc_dbg` ponownie przydzielić bloku pamięci w stercie podstawowy, ale `_aligned_recalloc_dbg` bierze pod uwagę kilka funkcji debugowania: buforów po obu stronach części bloku do testowania przecieki, parametr typu bloku do śledzenia określonego użytkownika typy alokacji i `filename` / `linenumber` informacji do ustalenia źródła żądań alokacji.  
  
 `_aligned_recalloc_dbg`przydziela ponownie bloku nieco więcej miejsca niż żądany rozmiar pamięci określony (`num` * `size`) co może być większa lub mniejsza niż rozmiar bloku pierwotnie alokacji pamięci. Dodatkowe miejsce jest używane przez menedżera stosu debugowania, do łączenia bloków pamięci debugowania i do dostarczenia aplikacji informacji nagłówka debugowania i zastąpienia buforów. Ponowne przydzielenie może spowodować przeniesienie do innej lokalizacji w stercie oryginalnego bloku pamięci, jak również zmiana rozmiaru bloku pamięci. Użytkownik część bloku jest wypełnione wartością 0xCD i Zastąp buforów wypełniane 0xFD.  
  
 `_aligned_recalloc_dbg`Ustawia `errno` do `ENOMEM` Jeśli alokacja pamięci nie powiodło się; `EINVAL` jest zwracany, jeśli ilość pamięci potrzebnej (łącznie z czynności wymienionych wcześniej) przekracza `_HEAP_MAXREQ`. Aby uzyskać informacji dotyczących tego i innych kodów błędów, zobacz [errno _doserrno —, _sys_errlist — i _sys_nerr —](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).  
  
 `_aligned_recalloc_dbg` również sprawdza poprawność parametrów. Jeśli `alignment` nie jest potęgą 2, ta funkcja wywołuje program obsługi nieprawidłowych parametrów, zgodnie z opisem w [sprawdzanie poprawności parametru](../../c-runtime-library/parameter-validation.md). Jeśli jest dozwolone wykonywanie, aby kontynuować, ta funkcja zwraca `NULL` i ustawia `errno` do `EINVAL`.  
  
 Aby dowiedzieć się jak bloki pamięci są przydzielone, zainicjować i zarządzane w wersji podstawowej sterty debugowania, zobacz [szczegóły dotyczące sterty debugowania CRT](/visualstudio/debugger/crt-debug-heap-details). Informacje o typach bloku alokacji i sposobu ich używania, zobacz [typów bloków w stercie debugowania](/visualstudio/debugger/crt-debug-heap-details). Aby uzyskać informacje o różnicach między wywoływanie funkcji sterty standardowe i jego wersji do debugowania w kompilację debugowania aplikacji, zobacz [debugowania wersji z funkcji alokacji sterty](/visualstudio/debugger/debug-versions-of-heap-allocation-functions).  
  
## <a name="requirements"></a>Wymagania  
  
|Procedura|Wymagany nagłówek|  
|-------------|---------------------|  
|`_aligned_recalloc_dbg`|\<crtdbg.h >|  
  
 Aby uzyskać więcej informacji o zgodności, zobacz [zgodności](../../c-runtime-library/compatibility.md) we wprowadzeniu.  
  
## <a name="libraries"></a>Biblioteki  
 Wersja debugowania [biblioteki wykonawcze języka C](../../c-runtime-library/crt-library-features.md) tylko.  
  
## <a name="see-also"></a>Zobacz też  
 [Procedury debugowania](../../c-runtime-library/debug-routines.md)