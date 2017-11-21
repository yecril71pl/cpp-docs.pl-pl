---
title: "_recalloc_dbg — | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apiname: _recalloc_dbg
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
- recalloc_dbg
- _recalloc_dbg
dev_langs: C++
helpviewer_keywords:
- _recalloc_dbg function
- recalloc_dbg function
ms.assetid: 43c3e9b2-be6d-4508-9b0f-3220c8a47ca3
caps.latest.revision: "8"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 02ac41e22a5080576339b00e54f339bb878a794d
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="recallocdbg"></a>_recalloc_dbg
Przydziela ponownie tablicy i inicjuje jej elementy 0 (tylko wersja do debugowania).  
  
## <a name="syntax"></a>Składnia  
  
```  
void *_recalloc_dbg(   
   void *userData,  
   size_t num,  
   size_t size,  
   int blockType,  
   const char *filename,  
   int linenumber   
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `userData`  
 Wskaźnik do bloku wcześniej alokacji pamięci.  
  
 `num`  
 Żądana liczba bloków pamięci.  
  
 `size`  
 Żądany rozmiar każdego bloku pamięci (w bajtach).  
  
 `blockType`  
 Żądany typ bloku pamięci: `_CLIENT_BLOCK` lub `_NORMAL_BLOCK`.  
  
 Informacje o typach bloku alokacji i sposobu ich używania, zobacz [typów bloków w stercie debugowania](/visualstudio/debugger/crt-debug-heap-details).  
  
 `filename`  
 Wskaźnik do nazwy pliku źródłowego, który żądanej operacji alokacji lub `NULL`.  
  
 `linenumber`  
 Numer w pliku źródłowym, której zażądano operacji alokacji wiersza lub `NULL`.  
  
 `filename` i `linenumber` parametry są dostępne tylko podczas `_recalloc_dbg` została jawnie wywołana lub [_crtdbg_map_alloc —](../../c-runtime-library/crtdbg-map-alloc.md) stała preprocesora została zdefiniowana.  
  
## <a name="return-value"></a>Wartość zwracana  
 Po pomyślnym ukończeniu ta funkcja zwraca wskaźnik do użytkownika części bloku przydzielić pamięci, nowych funkcji programu obsługi albo zwraca wartość NULL. Pełny opis zwracany zachowania zobacz sekcję poniżej uwagi. Aby uzyskać więcej informacji o sposobie korzystania z nowych funkcji programu obsługi, zobacz [_recalloc —](../../c-runtime-library/reference/recalloc.md) funkcji.  
  
## <a name="remarks"></a>Uwagi  
 `_recalloc_dbg`jest to wersja debugowania [_recalloc —](../../c-runtime-library/reference/recalloc.md) funkcji. Gdy [_DEBUG](../../c-runtime-library/debug.md) nie jest zdefiniowana, każde wywołanie `_recalloc_dbg` zostanie zmniejszona do wywołania `_recalloc`. Zarówno `_recalloc` i `_recalloc_dbg` ponownie przydzielić bloku pamięci w stercie podstawowy, ale `_recalloc_dbg` bierze pod uwagę kilka funkcji debugowania: buforów po obu stronach części bloku do testowania przecieki, parametr typu bloku do śledzenia określonego użytkownika typy alokacji i `filename` / `linenumber` informacji do ustalenia źródła żądań alokacji.  
  
 `_recalloc_dbg`przydziela ponownie bloku nieco więcej miejsca niż żądany rozmiar pamięci określony (`num` * `size`) co może być większa lub mniejsza niż rozmiar bloku pierwotnie alokacji pamięci. Dodatkowe miejsce jest używane przez menedżera stosu debugowania, do łączenia bloków pamięci debugowania i do dostarczenia aplikacji informacji nagłówka debugowania i zastąpienia buforów. Ponowne przydzielenie może spowodować przeniesienie do innej lokalizacji w stercie oryginalnego bloku pamięci, jak również zmiana rozmiaru bloku pamięci. Użytkownik część bloku jest wypełnione wartością 0xCD i każdego buforów Zastąp wypełniane 0xFD.  
  
 `_recalloc_dbg`Ustawia `errno` do `ENOMEM` Jeśli alokacja pamięci nie powiodło się; `EINVAL` jest zwracany, jeśli ilość pamięci potrzebnej (łącznie z czynności wymienionych wcześniej) przekracza `_HEAP_MAXREQ`. Aby uzyskać informacji dotyczących tego i innych kodów błędów, zobacz [errno _doserrno —, _sys_errlist — i _sys_nerr —](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).  
  
 Aby dowiedzieć się jak bloki pamięci są przydzielone, zainicjować i zarządzane w wersji podstawowej sterty debugowania, zobacz [szczegóły dotyczące sterty debugowania CRT](/visualstudio/debugger/crt-debug-heap-details). Aby uzyskać informacje o różnicach między wywoływanie funkcji sterty standardowe i jego wersji do debugowania w kompilację debugowania aplikacji, zobacz [debugowania wersji z funkcji alokacji sterty](/visualstudio/debugger/debug-versions-of-heap-allocation-functions).  
  
## <a name="requirements"></a>Wymagania  
  
|Procedura|Wymagany nagłówek|  
|-------------|---------------------|  
|`_recalloc_dbg`|\<crtdbg.h >|  
  
 Aby uzyskać więcej informacji o zgodności, zobacz [zgodności](../../c-runtime-library/compatibility.md) we wprowadzeniu.  
  
## <a name="libraries"></a>Biblioteki  
 Wersja debugowania [biblioteki wykonawcze języka C](../../c-runtime-library/crt-library-features.md) tylko.  
  
## <a name="see-also"></a>Zobacz też  
 [Procedury debugowania](../../c-runtime-library/debug-routines.md)