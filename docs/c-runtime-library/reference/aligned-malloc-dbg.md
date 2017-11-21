---
title: "_aligned_malloc_dbg — | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apiname: _aligned_malloc_dbg
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
- _aligned_malloc_dbg
- aligned_malloc_dbg
dev_langs: C++
helpviewer_keywords:
- aligned_malloc_dbg function
- _aligned_malloc_dbg function
ms.assetid: fb0429c3-685d-4826-9075-2515c5bdc5c6
caps.latest.revision: "8"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: aca23722103b75c6420ed14132d1fdac9cd097f6
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="alignedmallocdbg"></a>_aligned_malloc_dbg
Przydziela pamięć na określonej granicy wyrównania z dodatkowym miejscem dla nagłówka debugowania i zastąpić buforów (tylko wersja do debugowania).  
  
## <a name="syntax"></a>Składnia  
  
```  
void * _aligned_malloc_dbg(  
    size_t size,   
    size_t alignment,  
   const char *filename,  
   int linenumber   
);  
```  
  
#### <a name="parameters"></a>Parametry  
 [in]`size`  
 Rozmiar żądanej alokacji pamięci.  
  
 [in]`alignment`  
 Wartość wyrównania, która musi być całkowitą potęgą liczby 2.  
  
 [in]`filename`  
 Wskaźnik na nazwę pliku źródłowego, który zażądał operacji alokacji lub NULL.  
  
 [in]`linenumber`  
 Numer wiersza w pliku źródłowym, gdzie zażądano operacji alokacji lub NULL.  
  
## <a name="return-value"></a>Wartość zwracana  
 Wskaźnik do bloku pamięci, która została przydzielona lub `NULL` Jeśli działanie nie powiodło się.  
  
## <a name="remarks"></a>Uwagi  
 `_aligned_malloc_dbg`jest to wersja debugowania [_aligned_malloc —](../../c-runtime-library/reference/aligned-malloc.md) funkcji. Gdy [_DEBUG](../../c-runtime-library/debug.md) nie jest zdefiniowana, każde wywołanie `_aligned_malloc_dbg` zostanie zmniejszona do wywołania `_aligned_malloc`. Zarówno `_aligned_malloc` i `_aligned_malloc_dbg` przydzielić bloku pamięci w stosie podstawowej, ale `_aligned_malloc_dbg` oferuje kilka funkcji debugowania: buforów po obu stronach użytkownika część bloku do testowania przecieki, i `filename` / `linenumber` informacji do ustalenia źródła żądań alokacji.  
  
 `_aligned_malloc_dbg` alokuje blok pamięci z nieco większą ilością miejsca niż żądane `size`. Dodatkowe miejsce jest używane przez menedżera stosu debugowania, do łączenia bloków pamięci debugowania i do dostarczenia aplikacji informacji nagłówka debugowania i zastąpienia buforów. Gdy blok zostanie przydzielony, część użytkownika bloku jest wypełniania wartościami 0xCD a każdy bufor zastąpienia jest wypełniany wartościami 0xFD.  
  
 `_aligned_malloc_dbg`Ustawia `errno` do `ENOMEM` Jeśli alokacja pamięci nie powiedzie się lub jeśli przekracza ilość pamięci potrzebnej (łącznie z czynności wymienionych wcześniej) `_HEAP_MAXREQ`. Aby uzyskać informacji dotyczących tego i innych kodów błędów, zobacz [errno _doserrno —, _sys_errlist — i _sys_nerr —](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md). `_aligned_malloc_dbg` również sprawdza poprawność parametrów. Jeśli `alignment` nie jest potęgą liczby 2 lub `size` wynosi zero, ta funkcja wywołuje program obsługi nieprawidłowych parametrów, zgodnie z opisem w [sprawdzanie poprawności parametru](../../c-runtime-library/parameter-validation.md). Jeśli jest dozwolone wykonywanie, aby kontynuować, ta funkcja zwraca `NULL` i ustawia `errno` do `EINVAL`.  
  
 Aby dowiedzieć się jak bloki pamięci są przydzielone, zainicjować i zarządzane w wersji podstawowej sterty debugowania, zobacz [szczegóły dotyczące sterty debugowania CRT](/visualstudio/debugger/crt-debug-heap-details). Informacje o typach bloku alokacji i sposobu ich używania, zobacz [typów bloków w stercie debugowania](/visualstudio/debugger/crt-debug-heap-details). Aby uzyskać informacje o różnicach między wywoływanie funkcji sterty standardowe i jego wersji do debugowania w kompilację debugowania aplikacji, zobacz [debugowania wersji z funkcji alokacji sterty](/visualstudio/debugger/debug-versions-of-heap-allocation-functions).  
  
## <a name="requirements"></a>Wymagania  
  
|Procedura|Wymagany nagłówek|  
|-------------|---------------------|  
|`_aligned_malloc_dbg`|\<crtdbg.h >|  
  
 Aby uzyskać więcej informacji o zgodności, zobacz [zgodności](../../c-runtime-library/compatibility.md) we wprowadzeniu.  
  
## <a name="libraries"></a>Biblioteki  
 Wersja debugowania [biblioteki wykonawcze języka C](../../c-runtime-library/crt-library-features.md) tylko.  
  
## <a name="see-also"></a>Zobacz też  
 [Procedury debugowania](../../c-runtime-library/debug-routines.md)