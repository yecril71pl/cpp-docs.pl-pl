---
title: "_Crtmemdifference — | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apiname: _CrtMemDifference
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
- _CrtMemDifference
- CrtMemDifference
dev_langs: C++
helpviewer_keywords:
- CrtMemDifference function
- _CrtMemDifference function
ms.assetid: 0f327278-b551-482f-958b-76941f796ba4
caps.latest.revision: "16"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 4ba4dc873fbb0e77f3b2f939c9d62533849dab76
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="crtmemdifference"></a>_CrtMemDifference
Porównuje dwa pamięci Stany i zwraca różnice między nimi (tylko wersja do debugowania).  
  
## <a name="syntax"></a>Składnia  
  
```  
int _CrtMemDifference(   
   _CrtMemState *stateDiff,  
   const _CrtMemState *oldState,  
   const _CrtMemState *newState   
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `stateDiff`  
 Wskaźnik do `_CrtMemState` struktury, która jest używana do przechowywania różnice między Stanami dwóch pamięci (zwrócone).  
  
 `oldState`  
 Wskaźnik do wcześniejszego stanu pamięci (`_CrtMemState` struktury).  
  
 `newState`  
 Wskaźnik do nowszej stanu pamięci (`_CrtMemState` struktury).  
  
## <a name="return-value"></a>Wartość zwracana  
 Jeśli ilość pamięci są różne, `_CrtMemDifference` zwraca wartość TRUE. W przeciwnym razie funkcja zwraca wartość FALSE.  
  
## <a name="remarks"></a>Uwagi  
 `_CrtMemDifference` Funkcji porównuje `oldState` i `newState` i przechowuje różnice między nimi w `stateDiff`, które mogą następnie służyć przez aplikację wykrywanie przecieków pamięci i inne problemy z pamięcią. Gdy [_DEBUG](../../c-runtime-library/debug.md) nie jest zdefiniowany, wywołań `_CrtMemDifference` są usuwane podczas przetwarzania wstępnego.  
  
 `newState`i `oldState` muszą być prawidłowe wskaźnik do `_CrtMemState` struktury zdefiniowane w Crtdbg.h, który ma zostać wypełnione podczas [_crtmemcheckpoint —](../../c-runtime-library/reference/crtmemcheckpoint.md) przed wywołaniem `_CrtMemDifference`. `stateDiff`musi być wskaźnikiem do wcześniej alokowanego wystąpienia elementu `_CrtMemState` struktury. Jeśli `stateDiff`, `newState`, lub `oldState` jest `NULL`, program obsługi nieprawidłowych parametrów zostanie wywołany, zgodnie z opisem w [sprawdzanie poprawności parametru](../../c-runtime-library/parameter-validation.md). Jeśli jest dozwolone wykonywanie, aby kontynuować, [errno _doserrno —, _sys_errlist — i _sys_nerr —](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md) ustawiono `EINVAL` i funkcja zwraca wartość FALSE.  
  
 `_CrtMemDifference`porównuje `_CrtMemState` pola wartości bloków w `oldState` określone w `newState` i przechowuje wyniki w `stateDiff`. Stany liczba przydzielonych typy bloku lub całkowita liczba bloków przydzielonego dla każdego typu różni się między Stanami dwóch pamięci, są określane jako się znacznie różnić. Różnica między największe kiedykolwiek przydzielone jednocześnie dwa stany i różnica między całkowita alokacje na dwa stany są także przechowywane w `stateDiff`.  
  
 Domyślnie wewnętrzny bloki wykonawcze języka C (`_CRT_BLOCK`) nie są uwzględnione w operacji stan pamięci. [_Crtsetdbgflag —](../../c-runtime-library/reference/crtsetdbgflag.md) funkcji można włączyć `_CRTDBG_CHECK_CRT_DF` bit z `_crtDbgFlag` do dołączenia te bloki wykrywania przecieków i innych operacji stan pamięci. Zwolnienie bloki pamięci (`_FREE_BLOCK`), nie powodują `_CrtMemDifference` aby zwrócić wartość TRUE.  
  
 Aby uzyskać więcej informacji na temat funkcji stanu sterty i `_CrtMemState` struktury, zobacz [funkcje raportowania stanu sterty](/visualstudio/debugger/crt-debug-heap-details). Aby dowiedzieć się jak bloki pamięci są przydzielone, zainicjować i zarządzane w wersji podstawowej sterty debugowania, zobacz [szczegóły dotyczące sterty debugowania CRT](/visualstudio/debugger/crt-debug-heap-details).  
  
## <a name="requirements"></a>Wymagania  
  
|Procedura|Wymagany nagłówek|Opcjonalne nagłówki|  
|-------------|---------------------|---------------------|  
|`_CrtMemDifference`|\<crtdbg.h >|\<errno.h >|  
  
 Aby uzyskać więcej informacji o zgodności, zobacz [zgodności](../../c-runtime-library/compatibility.md) we wprowadzeniu.  
  
 **Biblioteki:** wersja debugowania [Biblioteka CRT — funkcje](../../c-runtime-library/crt-library-features.md) tylko.  
  
## <a name="see-also"></a>Zobacz też  
 [Procedury debugowania](../../c-runtime-library/debug-routines.md)   
 [_crtDbgFlag](../../c-runtime-library/crtdbgflag.md)