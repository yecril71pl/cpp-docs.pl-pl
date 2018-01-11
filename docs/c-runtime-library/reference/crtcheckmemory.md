---
title: "_Crtcheckmemory — | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apiname: _CrtCheckMemory
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
- CrtCheckMemory
- _CrtCheckMemory
dev_langs: C++
helpviewer_keywords:
- _CrtCheckMemory function
- CrtCheckMemory function
ms.assetid: 457cc72e-60fd-4177-ab5c-6ae26a420765
caps.latest.revision: "12"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 60909079a4d7c30b3a3e6c00257d882d76467585
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="crtcheckmemory"></a>_CrtCheckMemory
Potwierdza integralność bloki pamięci przydzielić w stercie debugowania (tylko wersja do debugowania).  
  
## <a name="syntax"></a>Składnia  
  
```  
  
int _CrtCheckMemory( void );  
```  
  
## <a name="return-value"></a>Wartość zwracana  
 W przypadku powodzenia `_CrtCheckMemory` zwraca wartość PRAWDA; w przeciwnym razie funkcja zwraca wartość FALSE.  
  
## <a name="remarks"></a>Uwagi  
 `_CrtCheckMemory` Funkcja weryfikuje pamięci przydzielonej przez menedżera sterty debugowania przez sprawdzanie poprawności podstawowej sterty podstawowej i sprawdzania każdego bloku pamięci. Po napotkaniu niespójność pamięci lub błąd w podstawowej sterty podstawowej, informacje o nagłówku debugowania lub buforów Zastąp `_CrtCheckMemory` generuje raport debugowania informacje opisujące warunku błędu. Gdy [_DEBUG](../../c-runtime-library/debug.md) nie jest zdefiniowany, wywołań `_CrtCheckMemory` są usuwane podczas przetwarzania wstępnego.  
  
 Zachowanie `_CrtCheckMemory` mogą być kontrolowane przez ustawienie pola bitowego [_crtdbgflag —](../../c-runtime-library/crtdbgflag.md) Flaga przy użyciu [_crtsetdbgflag —](../../c-runtime-library/reference/crtsetdbgflag.md) funkcji. Włączanie **_crtdbg_check_always_df —** bit powoduje ON pole `_CrtCheckMemory` wywoływana za każdym razem, gdy zażądano operacji alokacji pamięci. Mimo że ta metoda spowalnia wykonywania, jest przydatne w przypadku przechwytywania błędów szybko. Włączanie **_crtdbg_alloc_mem_df —** bit przyczyny OFF pola `_CrtCheckMemory` Sprawdź stos i natychmiast zwraca **TRUE**.  
  
 Ponieważ ta funkcja zwraca **TRUE** lub **FALSE**, mogą być przekazywane do jednego z [_ASSERT](../../c-runtime-library/reference/assert-asserte-assert-expr-macros.md) makra, aby utworzyć prosty błąd debugowania mechanizmu obsługi. Poniższy przykład powoduje błąd potwierdzenia wykryje uszkodzenie w stercie:  
  
```  
_ASSERTE( _CrtCheckMemory( ) );  
```  
  
 Aby uzyskać więcej informacji o tym, jak `_CrtCheckMemory` może być używany z innymi funkcjami debugowania, zobacz [funkcje raportowania stanu sterty](/visualstudio/debugger/crt-debug-heap-details). Omówienie zarządzania pamięcią i sterty debugowania, zobacz [szczegóły dotyczące sterty debugowania CRT](/visualstudio/debugger/crt-debug-heap-details).  
  
## <a name="requirements"></a>Wymagania  
  
|Procedura|Wymagany nagłówek|  
|-------------|---------------------|  
|`_CrtCheckMemory`|\<crtdbg.h >|  
  
 Aby uzyskać więcej informacji o zgodności, zobacz [zgodności](../../c-runtime-library/compatibility.md) we wprowadzeniu.  
  
## <a name="libraries"></a>Biblioteki  
 Wersja debugowania [biblioteki wykonawcze języka C](../../c-runtime-library/crt-library-features.md) tylko.  
  
## <a name="example"></a>Przykład  
 Przykładowe zastosowania `_CrtCheckMemory`, zobacz [crt_dbg1](http://msdn.microsoft.com/en-us/17b4b20c-e849-48f5-8eb5-dca6509cbaf9).  
  
## <a name="see-also"></a>Zobacz też  
 [Procedury debugowania](../../c-runtime-library/debug-routines.md)   
 [_crtdbgflag —](../../c-runtime-library/crtdbgflag.md)   
 [_CrtSetDbgFlag](../../c-runtime-library/reference/crtsetdbgflag.md)