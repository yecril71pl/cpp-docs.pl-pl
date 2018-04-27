---
title: _Crtmemdifference — | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- _CrtMemDifference
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
dev_langs:
- C++
helpviewer_keywords:
- CrtMemDifference function
- _CrtMemDifference function
ms.assetid: 0f327278-b551-482f-958b-76941f796ba4
caps.latest.revision: 16
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 27fb436c438daac7415ba3c0e7581611414c9c4a
ms.sourcegitcommit: ef859ddf5afea903711e36bfd89a72389a12a8d6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/20/2018
---
# <a name="crtmemdifference"></a>_CrtMemDifference

Porównuje dwa pamięci Stany i zwraca różnice między nimi (tylko wersja do debugowania).

## <a name="syntax"></a>Składnia

```C
int _CrtMemDifference(
   _CrtMemState *stateDiff,
   const _CrtMemState *oldState,
   const _CrtMemState *newState
);
```

### <a name="parameters"></a>Parametry

*stateDiff*<br/>
Wskaźnik do **_crtmemstate —** struktury, która jest używana do przechowywania różnice między Stanami dwóch pamięci (zwrócone).

*oldState*<br/>
Wskaźnik do wcześniejszego stanu pamięci (**_crtmemstate —** struktury).

*Nowy stan*<br/>
Wskaźnik do nowszej stanu pamięci (**_crtmemstate —** struktury).

## <a name="return-value"></a>Wartość zwracana

Jeśli ilość pamięci są różne, **_crtmemdifference —** zwraca wartość TRUE. W przeciwnym razie funkcja zwraca wartość FALSE.

## <a name="remarks"></a>Uwagi

**_Crtmemdifference —** funkcji porównuje *oldState* i *nowy stan* i przechowuje różnice między nimi w *stateDiff*, który można następnie używany przez aplikację wykrywanie przecieków pamięci i inne problemy z pamięcią. Gdy [_DEBUG](../../c-runtime-library/debug.md) nie jest zdefiniowany, wywołań **_crtmemdifference —** są usuwane podczas przetwarzania wstępnego.

*Nowy stan* i *oldState* muszą być prawidłowe wskaźnik do **_crtmemstate —** struktury zdefiniowane w Crtdbg.h, który ma zostać wypełnione podczas [_crtmemcheckpoint —](crtmemcheckpoint.md)przed wywołaniem **_crtmemdifference —**. *stateDiff* musi być wskaźnikiem do wcześniej alokowanego wystąpienia elementu **_crtmemstate —** struktury. Jeśli *stateDiff*, *nowy stan*, lub *oldState* jest **NULL**, program obsługi nieprawidłowych parametrów zostanie wywołany, zgodnie z opisem w [ Sprawdzanie poprawności parametru](../../c-runtime-library/parameter-validation.md). Jeśli jest dozwolone wykonywanie, aby kontynuować, [errno _doserrno —, _sys_errlist — i _sys_nerr —](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md) ustawiono **einval —** i funkcja zwraca wartość FALSE.

**_Crtmemdifference —** porównuje **_crtmemstate —** pola wartości bloków w *oldState* określone w *nowy stan* i przechowuje wyniki w *stateDiff*. Stany liczba przydzielonych typy bloku lub całkowita liczba bloków przydzielonego dla każdego typu różni się między Stanami dwóch pamięci, są określane jako się znacznie różnić. Różnica między największe kiedykolwiek przydzielone jednocześnie dwa stany i różnica między całkowita alokacje na dwa stany są także przechowywane w *stateDiff*.

Domyślnie wewnętrzny bloki wykonawcze języka C (**_crt_block —**) nie są uwzględnione w operacji stan pamięci. [_Crtsetdbgflag —](crtsetdbgflag.md) funkcji można włączyć **_crtdbg_check_crt_df —** bit z **_crtdbgflag —** do dołączenia te bloki wykrywania przecieków i inny stan pamięci operacje. Zwolnienie bloki pamięci (**_free_block —**), nie powodują **_crtmemdifference —** aby zwrócić wartość TRUE.

Aby uzyskać więcej informacji na temat funkcji stanu sterty i **_crtmemstate —** struktury, zobacz [funkcje raportowania stanu sterty](/visualstudio/debugger/crt-debug-heap-details). Aby dowiedzieć się jak bloki pamięci są przydzielone, zainicjować i zarządzane w wersji podstawowej sterty debugowania, zobacz [szczegóły dotyczące sterty debugowania CRT](/visualstudio/debugger/crt-debug-heap-details).

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|Opcjonalne nagłówki|
|-------------|---------------------|---------------------|
|**_CrtMemDifference**|\<crtdbg.h>|\<errno.h>|

Aby uzyskać więcej informacji o zgodności, zobacz [zgodności](../../c-runtime-library/compatibility.md).

**Biblioteki:** wersja debugowania [Biblioteka CRT — funkcje](../../c-runtime-library/crt-library-features.md) tylko.

## <a name="see-also"></a>Zobacz także

[Procedury debugowania](../../c-runtime-library/debug-routines.md)<br/>
[_crtDbgFlag](../../c-runtime-library/crtdbgflag.md)<br/>
