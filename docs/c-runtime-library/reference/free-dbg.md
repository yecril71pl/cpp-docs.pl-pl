---
title: "_free_dbg — | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- _free_dbg
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
- _free_dbg
- free_dbg
dev_langs:
- C++
helpviewer_keywords:
- memory blocks, deallocating
- freeing memory
- _free_dbg function
- free_dbg function
ms.assetid: fc5e8299-616d-48a0-b979-e037117278c6
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: fa3df169a968313d2a29fbf9c08643748d3196d8
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/14/2018
---
# <a name="freedbg"></a>_free_dbg
Zwalnia blok pamięci sterty (tylko wersja do debugowania).  
  
## <a name="syntax"></a>Składnia  
  
```  
void _free_dbg(   
   void *userData,  
   int blockType   
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `userData`  
 Wskaźnik do bloku alokacji pamięci, który ma zostać zwolniony.  
  
 `blockType`  
 Typ blok pamięci przydzielony ma zostać zwolniony: `_CLIENT_BLOCK`, `_NORMAL_BLOCK`, lub `_IGNORE_BLOCK`.  
  
## <a name="remarks"></a>Uwagi  
 `_free_dbg` Funkcji jest wersja debugowania [wolnego](../../c-runtime-library/reference/free.md) funkcji. Gdy [_DEBUG](../../c-runtime-library/debug.md) nie jest zdefiniowana, każde wywołanie `_free_dbg` zostanie zmniejszona do wywołania `free`. Zarówno `free` i `_free_dbg` wolne blok pamięci w stosie podstawowy, ale `_free_dbg` bierze pod uwagę dwie funkcje debugowania: blokuje możliwość przechowywania zwolnionych w połączonej listy sterty symulacji niedobór pamięci i parametr typu bloku, aby zwolnić typy alokacji określone.  
  
 `_free_dbg` wykonuje sprawdzanie poprawności dla wszystkich określonych plików i lokalizacje bloku przed wykonaniem operacji wolne. Aplikacja nie powinien zapewniać te informacje. Gdy zostanie zwolniona blok pamięci, menedżera sterty debugowania automatycznie sprawdza spójność buforów po obu stronach części użytkownika i wystawia raportu o błędach, jeśli przeprowadzono zastępowanie. Jeśli `_CRTDBG_DELAY_FREE_MEM_DF` pola bitowego ze [_crtdbgflag —](../../c-runtime-library/crtdbgflag.md) flaga jest ustawiona, zwolnionych bloku jest wypełniony przypisanej wartości 0xDD, `_FREE_BLOCK` blokować typu i przechowywane w stercie połączonej listy bloków pamięci.  
  
 W przypadku wystąpienia błędu w zwolnić pamięć, `errno` ustawiono informacje z systemu operacyjnego od charakteru błędu. Aby uzyskać więcej informacji, zobacz [errno _doserrno —, _sys_errlist — i _sys_nerr —](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).  
  
 Aby dowiedzieć się jak bloki pamięci są przydzielone, zainicjować i zarządzane w wersji podstawowej sterty debugowania, zobacz [szczegóły dotyczące sterty debugowania CRT](/visualstudio/debugger/crt-debug-heap-details). Informacje o typach bloku alokacji i sposobu ich używania, zobacz [typów bloków w stercie debugowania](/visualstudio/debugger/crt-debug-heap-details). Aby uzyskać informacje o różnicach między wywoływanie funkcji sterty standardowe i jego wersji do debugowania w kompilację debugowania aplikacji, zobacz [debugowania wersji z funkcji alokacji sterty](/visualstudio/debugger/debug-versions-of-heap-allocation-functions).  
  
## <a name="requirements"></a>Wymagania  
  
|Procedura|Wymagany nagłówek|  
|-------------|---------------------|  
|`_free_dbg`|\<crtdbg.h>|  
  
 Aby uzyskać więcej informacji o zgodności, zobacz [zgodności](../../c-runtime-library/compatibility.md) we wprowadzeniu.  
  
## <a name="example"></a>Przykład  
 Przykładowe zastosowania `_free_dbg`, zobacz [crt_dbg2](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/crt/crt_dbg2).  
  
## <a name="see-also"></a>Zobacz też  
 [Procedury debugowania](../../c-runtime-library/debug-routines.md)   
 [_malloc_dbg](../../c-runtime-library/reference/malloc-dbg.md)