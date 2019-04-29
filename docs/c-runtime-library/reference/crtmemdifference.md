---
title: _CrtMemDifference
ms.date: 11/04/2016
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
helpviewer_keywords:
- CrtMemDifference function
- _CrtMemDifference function
ms.assetid: 0f327278-b551-482f-958b-76941f796ba4
ms.openlocfilehash: f2c6306bf604737d0ace142674b21845a08e2dee
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62339471"
---
# <a name="crtmemdifference"></a>_CrtMemDifference

Porównuje dwa stany pamięci i zwraca ich różnice (tylko wersja debugowania).

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
Wskaźnik do **_CrtMemState** strukturę, która jest używana do przechowywania różnic pomiędzy stanami dwóch pamięci (zwrócone).

*oldState*<br/>
Wskaźnik na wcześniejszy stan pamięci (**_CrtMemState** struktury).

*Nowy stan*<br/>
Wskaźnik do późniejszego stanu pamięci (**_CrtMemState** struktury).

## <a name="return-value"></a>Wartość zwracana

Jeśli stany pamięci są znacząco różne **_crtmemdifference —** zwraca wartość TRUE. W przeciwnym razie funkcja zwraca wartość FALSE.

## <a name="remarks"></a>Uwagi

**_Crtmemdifference —** funkcja porównuje *oldState* i *newState* i przechowuje te różnice w *stateDiff*, który można następnie używany przez aplikację do wykrywania przecieków pamięci i innych problemów z pamięcią. Gdy [_DEBUG](../../c-runtime-library/debug.md) nie jest zdefiniowany, wywołania **_crtmemdifference —** są usuwane podczas przetwarzania wstępnego.

*Nowy stan* i *oldState* muszą być ważnym wskaźnik do **_CrtMemState** struktury, zdefiniowanego w Crtdbg.h, która ma zostać wypełnione podczas [_crtmemcheckpoint —](crtmemcheckpoint.md)przed wywołaniem **_crtmemdifference —**. *stateDiff* musi być wskaźnikiem do poprzednio przydzielonego wystąpienia **_CrtMemState** struktury. Jeśli *stateDiff*, *newState*, lub *oldState* jest **NULL**, procedura obsługi nieprawidłowego parametru zostanie wywołana, zgodnie z opisem w [ Walidacja parametru](../../c-runtime-library/parameter-validation.md). Jeśli wykonanie może być kontynuowane, [errno, _doserrno, _sys_errlist i _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md) ustawiono **EINVAL** i funkcja zwraca wartość FALSE.

**_Crtmemdifference —** porównuje **_CrtMemState** wartości bloków w pola *oldState* do tych w *newState* i zapisuje wynik w *stateDiff*. Gdy liczba przydzielonych typów bloków lub całkowita liczba bloków przydzielonego dla każdego typu różni się pomiędzy stanami dwóch pamięci, Stany są określone jako znacząco różne. Różnica między największą kwotę kiedykolwiek przydzieloną na raz dla dwóch stanów i różnica między całkowitą alokacji dla dwóch stanów jest również przechowywana w *stateDiff*.

Domyślnie wewnętrzne bloki wykonywania C (**_CRT_BLOCK**) nie są objęte operacjami stanu pamięci. [_CrtSetDbgFlag](crtsetdbgflag.md) funkcja może służyć do włączyć **_CRTDBG_CHECK_CRT_DF** trochę **_crtDbgFlag** aby objąć te bloki wykrywania przecieków i innych stan pamięci operacje. Uwolnione bloki pamięci (**_FREE_BLOCK**) nie powodują **_crtmemdifference —** zwraca wartość TRUE.

Aby uzyskać więcej informacji o funkcjach stanu sterty i **_CrtMemState** struktury, zobacz [funkcje raportowania stanu sterty](/visualstudio/debugger/crt-debug-heap-details). Aby dowiedzieć się jak bloki pamięci są przydzielane, inicjowane i zarządzane w wersji debugowania podstawowej sterty, zobacz [szczegóły dotyczące sterty debugowania CRT](/visualstudio/debugger/crt-debug-heap-details).

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|Opcjonalne nagłówki|
|-------------|---------------------|---------------------|
|**_CrtMemDifference**|\<crtdbg.h>|\<errno.h>|

Aby uzyskać więcej informacji na temat zgodności, zobacz [zgodności](../../c-runtime-library/compatibility.md).

**Biblioteki:** Debuguj wersje [funkcje biblioteki CRT](../../c-runtime-library/crt-library-features.md) tylko.

## <a name="see-also"></a>Zobacz także

[Procedury debugowania](../../c-runtime-library/debug-routines.md)<br/>
[_crtDbgFlag](../../c-runtime-library/crtdbgflag.md)<br/>
