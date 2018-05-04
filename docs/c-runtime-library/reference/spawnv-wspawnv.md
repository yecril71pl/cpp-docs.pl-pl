---
title: _spawnv —, _wspawnv — | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
apiname:
- _wspawnv
- _spawnv
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
- wspawnv
- _spawnv
- _wspawnv
dev_langs:
- C++
helpviewer_keywords:
- wspawnv function
- processes, creating
- _spawnv function
- processes, executing new
- process creation
- _wspawnv function
- spawnv function
ms.assetid: 72360ef4-dfa9-44c1-88c1-b3ecb660aa7d
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: ba46190ddf3707761ecf1e8537c336015426776d
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
---
# <a name="spawnv-wspawnv"></a>_spawnv, _wspawnv

Tworzy i wykonuje nowego procesu.

> [!IMPORTANT]
> Nie można używać tego interfejsu API w aplikacjach, które są wykonywane w środowisku wykonawczym systemu Windows. Aby uzyskać więcej informacji, zobacz [funkcje CRT, nie są obsługiwane w aplikacjach platformy uniwersalnej systemu Windows](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md).

## <a name="syntax"></a>Składnia

```C
intptr_t _spawnv(
   int mode,
   const char *cmdname,
   const char *const *argv
);
intptr_t _wspawnv(
   int mode,
   const wchar_t *cmdname,
   const wchar_t *const *argv
);
```

### <a name="parameters"></a>Parametry

*Tryb*<br/>
Tryb wykonywania dla procesu wywołującego.

*cmdname*<br/>
Ścieżka pliku do wykonania.

*ARGV —*<br/>
Tablicy wskaźników do argumentów. Argument *ARGV —*[0] jest zwykle wskaźnik do ścieżki w trybie rzeczywistym lub nazwę programu w trybie chronionym i *ARGV —*[1] za pomocą *ARGV —*[**n**] są wskaźnikami do ciągów znaków tworzących nowe listy argumentów. Argument *ARGV —*[**n** + 1] musi być **NULL** wskaźnik do znaku na końcu listy argumentów.

## <a name="return-value"></a>Wartość zwracana

Wartość zwrócona przez synchronicznego **_spawnv —** lub **_wspawnv —** (**_p_wait —** określona dla *tryb*) jest stan zakończenia nowego procesu. Wartość zwrócona przez asynchronicznego **_spawnv —** lub **_wspawnv —** (**_p_nowait —** lub **_p_nowaito —** określona dla *tryb* ) jest uchwytu procesu. Stan zakończenia to 0, jeśli proces zakończony normalnie. Stan zakończenia można ustawić na wartość niezerową działania zduplikowanego procesu w szczególności wywołuje **zakończyć** rutynowych z argumentem różną od zera. Jeśli nowy proces nie zostanie jawnie ustawiona stanu zakończenia dodatnią, stan zakończenia dodatnią wskazuje nietypowe wyjście z przerwania lub przerwania. Zwracana wartość -1 wskazuje błąd (nie jest zainicjowany nowy proces). W takim przypadku **errno** ustawiono na jedną z następujących wartości.

|||
|-|-|
**E2BIG —**|Lista argumentów przekracza 1024 bajty.
**EINVAL —**|*tryb* argument jest nieprawidłowy.
**ENOENT —**|Nie znaleziono pliku lub ścieżki.
**ENOEXEC —**|Określony plik nie jest wykonywalne lub ma nieprawidłowy format pliku wykonywalnego.
**ENOMEM —**|Za mało pamięci jest dostępna do wykonania w nowym procesie.

Aby uzyskać więcej informacji na temat tych i innych kody powrotu, zobacz [_doserrno —, errno, _sys_errlist — i _sys_nerr —](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

## <a name="remarks"></a>Uwagi

Każda z tych funkcji tworzy i wykonuje nowy proces, przekazanie tablicy wskaźników do argumentów wiersza polecenia.

Te funkcje walidację ich parametrów. Jeśli dowolny *cmdname* lub *ARGV —* jest wskaźnika o wartości null, lub jeśli *ARGV —* wskazuje wskaźnika o wartości null, lub *ARGV —*[0] to ciąg pusty, nieprawidłowy Parametr program obsługi zostanie wywołany, zgodnie z opisem w [sprawdzanie poprawności parametru](../../c-runtime-library/parameter-validation.md). Jeśli dozwolone jest wykonywanie aby kontynuować, ustawianie tych funkcji **errno** do **einval —**i zwróć -1. Nie nowego procesu jest zduplikowany.

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|
|-------------|---------------------|
|**_spawnv —**|\<stdio.h > lub \<process.h >|
|**_wspawnv —**|\<stdio.h > lub \<wchar.h >|

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
