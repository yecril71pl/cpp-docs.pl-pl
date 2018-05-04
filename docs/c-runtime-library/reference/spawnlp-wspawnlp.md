---
title: _spawnlp —, _wspawnlp — | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
apiname:
- _wspawnlp
- _spawnlp
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
- api-ms-win-crt-process-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- _wspawnlp
- wspawnlp
- _spawnlp
dev_langs:
- C++
helpviewer_keywords:
- wspawnlp function
- _spawnlp function
- processes, creating
- processes, executing new
- _wspawnlp function
- process creation
- spawnlp function
ms.assetid: 74fc6e7a-4f24-4103-9387-7177875875e6
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 4f894fc32631052e275a78cd279f750628b3258f
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
---
# <a name="spawnlp-wspawnlp"></a>_spawnlp, _wspawnlp

Tworzy i wykonuje nowego procesu.

> [!IMPORTANT]
> Nie można używać tego interfejsu API w aplikacjach, które są wykonywane w środowisku wykonawczym systemu Windows. Aby uzyskać więcej informacji, zobacz [funkcje CRT, nie są obsługiwane w aplikacjach platformy uniwersalnej systemu Windows](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md).

## <a name="syntax"></a>Składnia

```C
intptr_t _spawnlp(
   int mode,
   const char *cmdname,
   const char *arg0,
   const char *arg1,
   ... const char *argn,
   NULL
);
intptr_t _wspawnlp(
   int mode,
   const wchar_t *cmdname,
   const wchar_t *arg0,
   const wchar_t *arg1,
   ... const wchar_t *argn,
   NULL
);
```

### <a name="parameters"></a>Parametry

*Tryb*<br/>
Tryb wykonywania dla procesu wywołującego.

*cmdname*<br/>
Ścieżka pliku do wykonania.

*arg0*, *arg1*,... *argn*<br/>
Lista wskaźników do argumentów. *Arg0* argument jest zwykle wskaźnik do *cmdname*. Argumenty *arg1* za pośrednictwem *argn* są wskaźnikami do ciągów znaków tworzących nowe listy argumentów. Po *argn*, musi istnieć **NULL** wskaźnik do znaku na końcu listy argumentów.

## <a name="return-value"></a>Wartość zwracana

Wartość zwrócona przez synchronicznego **_spawnlp —** lub **_wspawnlp —** (**_p_wait —** określona dla *tryb*) jest stan zakończenia nowego procesu . Wartość zwrócona przez asynchronicznego **_spawnlp —** lub **_wspawnlp —** (**_p_nowait —** lub **_p_nowaito —** określona dla  *tryb*) jest uchwytu procesu. Stan zakończenia to 0, jeśli proces zakończony normalnie. Stan zakończenia można ustawić na wartość niezerową działania zduplikowanego procesu w szczególności wywołuje **zakończyć** rutynowych z argumentem różną od zera. Jeśli nowy proces nie zostanie jawnie ustawiona stanu zakończenia dodatnią, stan zakończenia dodatnią wskazuje nietypowe wyjście z przerwania lub przerwania. Zwracana wartość -1 wskazuje błąd (nie jest zainicjowany nowy proces). W takim przypadku **errno** ustawiono na jedną z następujących wartości.

|||
|-|-|
**E2BIG —**|Lista argumentów przekracza 1024 bajty.
**EINVAL —**|*tryb* argument jest nieprawidłowy.
**ENOENT —**|Nie znaleziono pliku lub ścieżki.
**ENOEXEC —**|Określony plik nie jest wykonywalne lub ma nieprawidłowy format pliku wykonywalnego.
**ENOMEM —**|Za mało pamięci jest dostępna do wykonania w nowym procesie.

Aby uzyskać więcej informacji na temat tych i innych kody powrotu, zobacz [_doserrno —, errno, _sys_errlist — i _sys_nerr —](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

## <a name="remarks"></a>Uwagi

Każda z tych funkcji tworzy i wykonuje nowego procesu przekazywania każdy argument wiersza polecenia jako osobny parametr i przy użyciu **ścieżki** zmiennej środowiskowej można znaleźć pliku do wykonania.

Te funkcje walidację ich parametrów. Jeśli dowolny *cmdname* lub *arg0* jest ciągiem pustym lub wskaźnika o wartości null, te funkcje wygeneruje wyjątek nieprawidłowy parametr, zgodnie z opisem w [sprawdzanie poprawności parametru](../../c-runtime-library/parameter-validation.md). Jeśli dozwolone jest wykonywanie aby kontynuować, ustawianie tych funkcji **errno** do **einval —**i zwróć -1. Nie nowego procesu jest zduplikowany.

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|
|-------------|---------------------|
|**_spawnlp —**|\<process.h >|
|**_wspawnlp —**|\<stdio.h > lub \<wchar.h >|

Aby uzyskać więcej informacji o zgodności, zobacz [zgodności](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Przykład

Zapoznaj się z przykładem w [_spawn, _wspawn — funkcje](../../c-runtime-library/spawn-wspawn-functions.md).

## <a name="see-also"></a>Zobacz także

[Procedury kontroli środowiska](../../c-runtime-library/process-and-environment-control.md)<br/>
[_spawn, _wspawn, funkcje](../../c-runtime-library/spawn-wspawn-functions.md)<br/>
[abort](abort.md)<br/>
[atexit](atexit.md)<br/>
[_exec, _wexec, funkcje](../../c-runtime-library/exec-wexec-functions.md)<br/>
[exit, _Exit, _exit](exit-exit-exit.md)<br/>
[_flushall](flushall.md)<br/>
[_getmbcp](getmbcp.md)<br/>
[_onexit, _onexit_m](onexit-onexit-m.md)<br/>
[_setmbcp](setmbcp.md)<br/>
[system, _wsystem](system-wsystem.md)<br/>
