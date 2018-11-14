---
title: _spawnvpe, _wspawnvpe
ms.date: 11/04/2016
apiname:
- _spawnvpe
- _wspawnvpe
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
- _spawnvpe
- wspawnvpe
- spawnvpe
- _wspawnvpe
helpviewer_keywords:
- _wspawnvpe function
- processes, creating
- _spawnvpe function
- processes, executing new
- wspawnvpe function
- process creation
- spawnvpe function
ms.assetid: 3db6394e-a955-4837-97a1-fab1db1e6092
ms.openlocfilehash: a98cc3c441261a92876b94e1231e66bb71e9d3d9
ms.sourcegitcommit: 1819bd2ff79fba7ec172504b9a34455c70c73f10
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/09/2018
ms.locfileid: "51326605"
---
# <a name="spawnvpe-wspawnvpe"></a>_spawnvpe, _wspawnvpe

Tworzy i uruchamia nowy proces.

> [!IMPORTANT]
> Tego API nie można używać w aplikacjach korzystających ze środowiska wykonawczego Windows. Aby uzyskać więcej informacji, zobacz [funkcje CRT nieobsługiwane w aplikacjach platformy uniwersalnej Windows](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md).

## <a name="syntax"></a>Składnia

```C
intptr_t _spawnvpe(
   int mode,
   const char *cmdname,
   const char *const *argv,
   const char *const *envp
);
intptr_t _wspawnvpe(
   int mode,
   const wchar_t *cmdname,
   const wchar_t *const *argv,
   const wchar_t *const *envp
);
```

### <a name="parameters"></a>Parametry

*Tryb*<br/>
Tryb wykonywania dla procesu wywołującego

*cmdname*<br/>
Ścieżka pliku do wykonania

*ARGV*<br/>
Tablica wskaźników do argumentów. Argument *argv*[0] jest zazwyczaj wskaźnikiem do ścieżki w trybie rzeczywistym lub nazwy programu w trybie chronionym i *argv*[1] za pomocą *argv*[**n**] są wskaźnikami do ciągów znaków tworzących nowe listy argumentów. Argument *argv*[**n** + 1] musi być **NULL** wskaźnik, aby zaznaczyć koniec listy argumentów.

*envp*<br/>
Tablica wskaźników do ustawienia środowiska

## <a name="return-value"></a>Wartość zwracana

Wartość zwracana przez synchroniczny **_spawnvpe** lub **_wspawnvpe —** (**_P_WAIT** określony dla *tryb*) jest stanem wyjścia nowego proces. Wartość zwracana przez synchroniczny **_spawnvpe** lub **_wspawnvpe —** (**_P_NOWAIT** lub **_P_NOWAITO** określony dla  *tryb*) jest dojściem do procesu. Stanem wyjścia wynosi 0, jeżeli proces zakończył się normalnie. Możesz ustawić stan wyjścia na wartość różną od zera, jeśli procesu rozmnożonego w szczególności wywołuje **wyjść** rutynę z argumentem wartość różną od zera. Jeśli nowy proces nie ustawi jawnie stanu wyjścia, stan wyjścia wskazuje nietypowe wyjście z porzuceniem lub przerwaniem. Zwracana wartość-1 wskazuje błąd (nowy proces nie jest uruchomiony). W tym przypadku **errno** jest ustawiony na jedną z następujących wartości:

|||
|-|-|
| **E2BIG** | Argument w postaci listy przekracza 1024 bajty. |
| **EINVAL** | *tryb* argument jest nieprawidłowy. |
| **ENOENT** | Nie znaleziono pliku lub ścieżki. |
| **ENOEXEC** | Określony plik nie jest wykonywalny lub ma nieprawidłowy format pliku wykonywalnego. |
| **ENOMEM** | Nie ma wystarczającej ilości pamięci jest dostępna do wykonania nowego procesu. |

Zobacz [_doserrno, errno, _sys_errlist i _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md) kody powrotne — Aby uzyskać więcej informacji na temat tych i innych.

## <a name="remarks"></a>Uwagi

Każda z tych funkcji tworzy i uruchamia nowy proces, przekazując tablicę wskaźników do argumentów wiersza polecenia oraz tablicę wskaźników do ustawienia środowiska. Te funkcje używają **ścieżki** zmiennej środowiskowej, aby znaleźć plik do wykonania.

Te funkcje sprawdzają poprawność swoich parametrów. Jeśli *cmdname* lub *argv* jest wskaźnikiem typu null, lub jeśli *argv* wskazuje na wskaźnik typu null, lub *argv*[0] to ciąg pusty, nieprawidłowy Procedura obsługi nieprawidłowego parametru zostanie wywołana, zgodnie z opisem w [Parameter Validation](../../c-runtime-library/parameter-validation.md) . Jeśli wykonanie może być kontynuowane, te funkcje ustawiają **errno** do **EINVAL**i zwracają wartość -1. Żaden nowy proces nie jest rozprzestrzeniony.

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|
|-------------|---------------------|
|**_spawnvpe**|\<stdio.h > lub \<process.h >|
|**_wspawnvpe —**|\<stdio.h > lub \<wchar.h >|

Aby uzyskać dodatkowe informacje o zgodności, zobacz [zgodności](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Przykład

Zobacz przykład w [_spawn, _wspawn — funkcje](../../c-runtime-library/spawn-wspawn-functions.md).

## <a name="see-also"></a>Zobacz także

[abort](abort.md)<br/>
[atexit](atexit.md)<br/>
[_exec, _wexec, funkcje](../../c-runtime-library/exec-wexec-functions.md)<br/>
[exit, _Exit, _exit](exit-exit-exit.md)<br/>
[_flushall](flushall.md)<br/>
[_getmbcp](getmbcp.md)<br/>
[_onexit, _onexit_m](onexit-onexit-m.md)<br/>
[_setmbcp](setmbcp.md)<br/>
[system, _wsystem](system-wsystem.md)<br/>
