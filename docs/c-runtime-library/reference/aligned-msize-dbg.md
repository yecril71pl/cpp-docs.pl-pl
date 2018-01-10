---
title: _aligned_msize_dbg | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apiname: _aligned_msize_dbg
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
f1_keywords: _aligned_msize_dbg
dev_langs: C++
helpviewer_keywords: _aligned_msize_dbg
ms.assetid: f1c44af0-3f66-4033-81d1-d71d3afecba0
caps.latest.revision: "8"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 7f09b6429b8ffd4ecb34af1213ebb62100238af8
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="alignedmsizedbg"></a>_aligned_msize_dbg
Zwraca rozmiar bloku pamięci przydzielić w stercie (tylko wersja do debugowania).  
  
## <a name="syntax"></a>Składnia  
  
```  
size_t _aligned_msize_dbg(  
   void *memblock,  
   size_t alignment,  
   size_t offset  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 [in]`memblock`  
 Wskaźnik do bloku pamięci.  
  
 [in]`alignment`  
 Wartość wyrównania, która musi być całkowitą potęgą liczby 2.  
  
 [in]`offset`  
 Przesunięcie alokacji pamięci, aby wymusić wyrównanie.  
  
## <a name="return-value"></a>Wartość zwracana  
 Zwraca rozmiar (w bajtach) jako liczbę całkowitą bez znaku.  
  
## <a name="remarks"></a>Uwagi  
 `alignment` i `offset` wartości musi być taka sama jak wartości przekazane do funkcji, która przydzielony blok.  
  
 `_aligned_msize_dbg`jest to wersja debugowania [_aligned_msize —](../../c-runtime-library/reference/aligned-msize.md) funkcji. Gdy [_DEBUG](../../c-runtime-library/debug.md) nie jest zdefiniowana, każde wywołanie `_aligned_msize_dbg` zostanie zmniejszona do wywołania `_aligned_msize`. Zarówno `_aligned_msize` i `_aligned_msize_dbg` Oblicz rozmiar bloku pamięci w stercie podstawowy, ale `_aligned_msize_dbg` dodaje funkcję debugowania: rozmiar zwróconego zawiera buforów po obu stronach użytkownika część bloku pamięci.  
  
 Ta funkcja weryfikuje jej parametr. Jeśli `memblock` jest wskaźnika o wartości null lub `alignment` nie jest potęgą liczby 2, `_msize` wywołuje program obsługi nieprawidłowych parametrów, zgodnie z opisem w [sprawdzanie poprawności parametru](../../c-runtime-library/parameter-validation.md). Jeśli ten błąd jest obsługiwane, funkcja ustawia `errno` do `EINVAL` i zwraca wartość -1.  
  
 Aby dowiedzieć się jak bloki pamięci są przydzielone, zainicjować i zarządzane w wersji podstawowej sterty debugowania, zobacz [szczegóły dotyczące sterty debugowania CRT](/visualstudio/debugger/crt-debug-heap-details). Informacje o typach bloku alokacji i sposobu ich używania, zobacz [typów bloków w stercie debugowania](/visualstudio/debugger/crt-debug-heap-details). Aby uzyskać informacje o różnicach między wywoływanie funkcji sterty standardowe i jego wersji do debugowania w kompilację debugowania aplikacji, zobacz [debugowania wersji z funkcji alokacji sterty](/visualstudio/debugger/debug-versions-of-heap-allocation-functions).  
  
## <a name="requirements"></a>Wymagania  
  
|Procedura|Wymagany nagłówek|  
|-------------|---------------------|  
|`_aligned_msize_dbg`|\<crtdbg.h >|  
  
 Aby uzyskać więcej informacji o zgodności, zobacz [zgodności](../../c-runtime-library/compatibility.md) we wprowadzeniu.  
  
## <a name="libraries"></a>Biblioteki  
 Wersja debugowania [biblioteki wykonawcze języka C](../../c-runtime-library/crt-library-features.md) tylko.  
  
## <a name="see-also"></a>Zobacz też  
 [Alokacja pamięci](../../c-runtime-library/memory-allocation.md)