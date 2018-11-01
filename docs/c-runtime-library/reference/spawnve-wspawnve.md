---
title: _spawnve, _wspawnve
ms.date: 11/04/2016
apiname:
- _spawnve
- _wspawnve
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
- wspawnve
- _spawnve
- _wspawnve
- spawnve
helpviewer_keywords:
- _spawnve function
- spawnve function
- wspawnve function
- processes, creating
- _wspawnve function
- processes, executing new
- process creation
ms.assetid: 26d1713d-b551-4f21-a07b-e9891a2ae6cf
ms.openlocfilehash: 03fa25f5800928aad7185c98a331d06b1c39779b
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50562022"
---
# <a name="spawnve-wspawnve"></a>_spawnve, _wspawnve

Tworzy i uruchamia nowy proces.

> [!IMPORTANT]
> Tego API nie można używać w aplikacjach korzystających ze środowiska wykonawczego Windows. Aby uzyskać więcej informacji, zobacz [funkcje CRT nieobsługiwane w aplikacjach platformy uniwersalnej Windows](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md).

## <a name="syntax"></a>Składnia

```C
intptr_t _spawnve(
   int mode,
   const char *cmdname,
   const char *const *argv,
   const char *const *envp
);
intptr_t _wspawnve(
   int mode,
   const wchar_t *cmdname,
   const wchar_t *const *argv,
   const wchar_t *const *envp
);
```

### <a name="parameters"></a>Parametry

*Tryb*<br/>
Tryb wykonywania dla procesu wywołującego.

*cmdname*<br/>
Ścieżka pliku do wykonania.

*ARGV*<br/>
Tablica wskaźników do argumentów. Argument *argv*[0] jest zazwyczaj wskaźnikiem do ścieżki w trybie rzeczywistym lub nazwy programu w trybie chronionym i *argv*[1] za pomocą *argv*[**n**] są wskaźnikami do ciągów znaków tworzących nowe listy argumentów. Argument *argv*[**n** + 1] musi być **NULL** wskaźnik, aby zaznaczyć koniec listy argumentów.

*envp*<br/>
Tablica wskaźników do ustawienia środowiska.

## <a name="return-value"></a>Wartość zwracana

Wartość zwracana przez synchroniczny **_spawnve —** lub **_wspawnve —** (**_P_WAIT** określony dla *tryb*) jest stanem wyjścia nowego procesu . Wartość zwracana przez synchroniczny **_spawnve —** lub **_wspawnve —** (**_P_NOWAIT** lub **_P_NOWAITO** określony dla  *tryb*) jest dojściem do procesu. Stanem wyjścia wynosi 0, jeżeli proces zakończył się normalnie. Możesz ustawić stan wyjścia na wartość różną od zera, jeśli procesu rozmnożonego w szczególności wywołuje **wyjść** rutynę z argumentem wartość różną od zera. Jeśli nowy proces nie ustawi jawnie stanu wyjścia, stan wyjścia wskazuje nietypowe wyjście z porzuceniem lub przerwaniem. Zwracana wartość-1 wskazuje błąd (nowy proces nie jest uruchomiony). W tym przypadku **errno** jest ustawiony na jedną z następujących wartości.

|||
|-|-|
**E2BIG**|Argument w postaci listy przekracza 1024 bajty.
**EINVAL**|*tryb* argument jest nieprawidłowy.
**ENOENT**|Nie znaleziono pliku lub ścieżki.
**ENOEXEC**|Określony plik nie jest wykonywalny lub ma nieprawidłowy format pliku wykonywalnego.
**ENOMEM**|Nie ma wystarczającej ilości pamięci jest dostępna do wykonania nowego procesu.

Aby uzyskać więcej informacji na temat tych i innych kodach powrotnych, zobacz [_doserrno, errno, _sys_errlist i _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

## <a name="remarks"></a>Uwagi

Każda z tych funkcji tworzy i uruchamia nowy proces, przekazując tablicę wskaźników do argumentów wiersza polecenia oraz tablicę wskaźników do ustawienia środowiska.

Te funkcje sprawdzają poprawność swoich parametrów. Jeśli *cmdname* lub *argv* jest wskaźnikiem typu null, lub jeśli *argv* wskazuje na wskaźnik typu null, lub *argv*[0] to ciąg pusty, nieprawidłowy Procedura obsługi nieprawidłowego parametru zostanie wywołana, zgodnie z opisem w [Parameter Validation](../../c-runtime-library/parameter-validation.md). Jeśli wykonanie może być kontynuowane, te funkcje ustawiają **errno** do **EINVAL**i zwracają wartość -1. Żaden nowy proces nie jest rozprzestrzeniony.

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|
|-------------|---------------------|
|**_spawnve —**|\<stdio.h > lub \<process.h >|
|**_wspawnve**|\<stdio.h > lub \<wchar.h >|

Aby uzyskać więcej informacji na temat zgodności, zobacz [zgodności](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Przykład

Zobacz przykład w [_spawn, _wspawn — funkcje](../../c-runtime-library/spawn-wspawn-functions.md).

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
