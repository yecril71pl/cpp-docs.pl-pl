---
title: "_Crtsetallochook — | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- _CrtSetAllocHook
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
- _CrtSetAllocHook
- CrtSetAllocHook
dev_langs:
- C++
helpviewer_keywords:
- _CrtSetAllocHook function
- CrtSetAllocHook function
ms.assetid: 405df37b-2fd1-42c8-83bc-90887f17f29d
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 6168081aff668a3b613b4844be3c50b841f5bc07
ms.sourcegitcommit: 185e11ab93af56ffc650fe42fb5ccdf1683e3847
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/29/2018
---
# <a name="crtsetallochook"></a>_CrtSetAllocHook
Instaluje funkcję alokacji zdefiniowaną przez klienta przez podłączenie jej do procesu alokacji pamięci debugowania w czasie wykonywania C (tylko wersja debug).  
  
## <a name="syntax"></a>Składnia  
  
```  
_CRT_ALLOC_HOOK _CrtSetAllocHook(  
   _CRT_ALLOC_HOOK allocHook   
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `allocHook`  
 Nowa funkcja alokacji zdefiniowana przez klienta do podłączenia do procesu alokacji pamięci debugowania w czasie wykonywania C.  
  
## <a name="return-value"></a>Wartość zwracana  
 Zwraca wartość zdefiniowanej wcześniej funkcji podłączania alokacji lub `NULL` jeśli `allocHook` jest `NULL`.  
  
## <a name="remarks"></a>Uwagi  
 `_CrtSetAllocHook` pozwala aplikacji podłączyć własną funkcję alokacji w proces alokacji pamięci biblioteki debugowania C w czasie wykonywania. W rezultacie, każde wywołanie funkcji alokacji debugowania do przydzielania, ponownego przydzielenia lub zwolnienia bloku pamięci wyzwala wywołanie funkcji podłączania aplikacji. `_CrtSetAllocHook` dostarcza aplikacji prostą metodę do testowania, jak aplikacja obsługuje sytuacje braku pamięci, możliwość zbadania wzorców przydziału i możliwość rejestrowania informacji o alokacji do późniejszej analizy. Gdy [_DEBUG](../../c-runtime-library/debug.md) nie jest zdefiniowany, wywołań `_CrtSetAllocHook` są usuwane podczas przetwarzania wstępnego.  
  
 Funkcja `_CrtSetAllocHook` instaluje nową funkcję alokacji zdefiniowaną przez klienta, określoną w `allocHook` i zwraca funkcję wcześniej zdefiniowaną funkcję podłączania. Poniższy przykład ilustruje, jak powinny być prototypowane zdefiniowane przez klienta funkcje punktu zaczepienia alokacji:  
  
```  
int YourAllocHook( int allocType, void *userData, size_t size, int   
blockType, long requestNumber, const unsigned char *filename, int   
lineNumber);  
```  
  
 Argument `allocType` określa typ operacji alokacji `(_HOOK_ALLOC`, `_HOOK_REALLOC`, i `_HOOK_FREE`) który wyzwolił wywołanie funkcji punktu zaczepienia alokacji. Gdy wyzwalający typ alokacji to `_HOOK_FREE`, `userData` jest wskaźnikiem na sekcję danych użytkownika bloku pamięci która będzie zwolniona. Jednak gdy wyzwalający typ alokacji to `_HOOK_ALLOC` lub `_HOOK_REALLOC`, `userData` jest `NULL` ponieważ blok pamięci nie został jeszcze przydzielony.  
  
 `size` określa rozmiar bloku pamięci w bajtach, `blockType` wskazuje typ bloku pamięci, `requestNumber` jest numerem porządkowym obiektu alokacji bloku pamięci i jeśli to możliwe, `filename` i `lineNumber` określają nazwę pliku źródła i numer linii w której zainicjowano wyzwolenie operacji alokacji.  
  
 Po zakończeniu przetwarzania funkcji podłączania, musi ona zwracać wartość logiczną, która wskazuje głównemu procesowi alokacji środowiska uruchomieniowego C sposób kontynuowania. Kiedy funkcja podłączania chce aby główny proces alokacji kontynuował, jeśli funkcja podłączania nigdy nie została wywołana, to funkcja podłączania powinna zwracać `TRUE`. Powoduje to, że oryginalna operacja wyzwalania alokacji zostanie wykonana. Przy użyciu tej implementacji, funkcja podłączania może gromadzić i zapisywać informacje dotyczące alokacji do późniejszej analizy, bez zakłócania bieżącej operacji alokacji lub stanu sterty debugowania.  
  
 Kiedy funkcja podłączania chce aby główny proces alokacji kontynuował tak, jakby wyzwalająca operacja alokacji nie powiodła się to funkcja podłączania powinna zwrócić `FALSE`. Przy użyciu tej implementacji, funkcja podłączania można symulować cały szereg warunków pamięci i stanów sterty do testowania, jak aplikacja obsługuje każdą sytuację.  
  
 Aby wyczyścić funkcję podłączania, należy przekazać `NULL` do `_CrtSetAllocHook`.  
  
 Aby uzyskać więcej informacji o tym, jak `_CrtSetAllocHook` może być używany z innymi funkcje zarządzania pamięcią lub zapisać funkcji zdefiniowanej przez klienta punktu zaczepienia, zobacz [debugowania pisanie funkcji punktów zaczepienia](/visualstudio/debugger/debug-hook-function-writing).  
  
> [!NOTE]
>  Parametr `_CrtSetAllocHook` nie jest obsługiwany przez `/clr:pure`. **/CLR: pure** i **/CLR: Safe** — opcje kompilatora zostały uznane za przestarzałe w programie Visual Studio 2015.  
  
## <a name="requirements"></a>Wymagania  
  
|Procedura|Wymagany nagłówek|  
|-------------|---------------------|  
|`_CrtSetAllocHook`|\<crtdbg.h>|  
  
 Aby uzyskać więcej informacji o zgodności, zobacz [zgodności](../../c-runtime-library/compatibility.md) we wprowadzeniu.  
  
## <a name="libraries"></a>Biblioteki  
 Wersja debugowania [biblioteki wykonawcze języka C](../../c-runtime-library/crt-library-features.md) tylko.  
  
## <a name="example"></a>Przykład  
 Przykładowe zastosowania `_CrtSetAllocHook`, zobacz [crt_dbg2](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/crt/crt_dbg2).  
  
## <a name="see-also"></a>Zobacz też  
 [Procedury debugowania](../../c-runtime-library/debug-routines.md)   
 [_CrtGetAllocHook](../../c-runtime-library/reference/crtgetallochook.md)