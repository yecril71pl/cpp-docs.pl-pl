---
title: "_realloc_dbg — | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apiname: _realloc_dbg
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
- _realloc_dbg
- realloc_dbg
dev_langs: C++
helpviewer_keywords:
- reallocating memory blocks
- realloc_dbg function
- memory blocks, reallocating
- memory, reallocating
- _realloc_dbg function
ms.assetid: 7c3cb780-51ed-4d9c-9929-cdde606d846a
caps.latest.revision: "15"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: edaebfb8fb3e4ec6d9b4fc0aa92253057f0aa6c5
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="reallocdbg"></a>_realloc_dbg
Przydziela ponownie określony blok pamięci w stercie przez przeniesienie lub zmiana rozmiaru bloku (tylko wersja do debugowania).  
  
## <a name="syntax"></a>Składnia  
  
```  
void *_realloc_dbg(  
   void *userData,  
   size_t newSize,  
   int blockType,  
   const char *filename,  
   int linenumber   
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `userData`  
 Wskaźnik do bloku wcześniej alokacji pamięci.  
  
 `newSize`  
 Żądany rozmiar bloku reallocated (w bajtach).  
  
 `blockType`  
 Żądany typ bloku reallocated: `_CLIENT_BLOCK` lub `_NORMAL_BLOCK`.  
  
 `filename`  
 Wskaźnik do nazwy pliku źródłowego, który zażądał `realloc` operacji ani mieć wartości NULL.  
  
 `linenumber`  
 Numer wiersza na plik źródłowy gdzie `realloc` operacja była żądana ani mieć wartości NULL.  
  
 `filename` i `linenumber` parametry są dostępne tylko podczas `_realloc_dbg` została jawnie wywołana lub [_crtdbg_map_alloc —](../../c-runtime-library/crtdbg-map-alloc.md) stała preprocesora została zdefiniowana.  
  
## <a name="return-value"></a>Wartość zwracana  
 Po pomyślnym ukończeniu ta funkcja zwraca wskaźnik do użytkownika części bloku przydzielić pamięci, nowych funkcji programu obsługi albo zwraca wartość NULL. Pełny opis zwracany zachowania zobacz sekcję poniżej uwagi. Aby uzyskać więcej informacji o sposobie korzystania z nowych funkcji programu obsługi, zobacz [realloc](../../c-runtime-library/reference/realloc.md) funkcji.  
  
## <a name="remarks"></a>Uwagi  
 `_realloc_dbg`jest to wersja debugowania [realloc](../../c-runtime-library/reference/realloc.md) funkcji. Gdy [_DEBUG](../../c-runtime-library/debug.md) nie jest zdefiniowana, każde wywołanie `_realloc_dbg` zostanie zmniejszona do wywołania `realloc`. Zarówno `realloc` i `_realloc_dbg` ponownie przydzielić bloku pamięci w stercie podstawowy, ale `_realloc_dbg` bierze pod uwagę kilka funkcji debugowania: buforów po obu stronach części bloku do testowania przecieki, parametr typu bloku do śledzenia określonego użytkownika typy alokacji i `filename` / `linenumber` informacji do ustalenia źródła żądań alokacji.  
  
 `_realloc_dbg`przydziela ponownie bloku pamięci określony nieco więcej miejsca niż żądany `newSize`. `newSize`może być większa lub mniejsza niż rozmiar bloku pierwotnie alokacji pamięci. Dodatkowe miejsce jest używane przez menedżera stosu debugowania, do łączenia bloków pamięci debugowania i do dostarczenia aplikacji informacji nagłówka debugowania i zastąpienia buforów. Ponowne przydzielenie może spowodować przeniesienie do innej lokalizacji w stercie oryginalnego bloku pamięci, jak również zmiana rozmiaru bloku pamięci. Jeśli blok pamięci jest przenoszony, zawartość oryginalnego bloku zostaną zastąpione.  
  
 `_realloc_dbg`Ustawia `errno` do `ENOMEM` Jeśli alokacja pamięci nie powiedzie się lub jeśli przekracza ilość pamięci potrzebnej (łącznie z czynności wymienionych wcześniej) `_HEAP_MAXREQ`. Aby uzyskać informacji dotyczących tego i innych kodów błędów, zobacz [errno _doserrno —, _sys_errlist — i _sys_nerr —](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).  
  
 Aby dowiedzieć się jak bloki pamięci są przydzielone, zainicjować i zarządzane w wersji podstawowej sterty debugowania, zobacz [szczegóły dotyczące sterty debugowania CRT](/visualstudio/debugger/crt-debug-heap-details). Informacje o typach bloku alokacji i sposobu ich używania, zobacz [typów bloków w stercie debugowania](/visualstudio/debugger/crt-debug-heap-details). Aby uzyskać informacje o różnicach między wywoływanie funkcji sterty standardowe i jego wersji do debugowania w kompilację debugowania aplikacji, zobacz [debugowania wersji z funkcji alokacji sterty](/visualstudio/debugger/debug-versions-of-heap-allocation-functions).  
  
## <a name="requirements"></a>Wymagania  
  
|Procedura|Wymagany nagłówek|  
|-------------|---------------------|  
|`_realloc_dbg`|\<crtdbg.h >|  
  
 Aby uzyskać więcej informacji o zgodności, zobacz [zgodności](../../c-runtime-library/compatibility.md) we wprowadzeniu.  
  
## <a name="libraries"></a>Biblioteki  
 Wersja debugowania [biblioteki wykonawcze języka C](../../c-runtime-library/crt-library-features.md) tylko.  
  
## <a name="example"></a>Przykład  
 Zapoznaj się z przykładem w [_msize_dbg —](../../c-runtime-library/reference/msize-dbg.md) tematu.  
  
## <a name="see-also"></a>Zobacz też  
 [Procedury debugowania](../../c-runtime-library/debug-routines.md)   
 [_malloc_dbg —](../../c-runtime-library/reference/malloc-dbg.md)