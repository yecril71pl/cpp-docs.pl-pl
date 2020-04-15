---
title: _spawnve, _wspawnve
ms.date: 4/2/2020
api_name:
- _spawnve
- _wspawnve
- _o__spawnve
- _o__wspawnve
api_location:
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
- api-ms-win-crt-private-l1-1-0
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- wspawnve
- _spawnve
- _wspawnve
helpviewer_keywords:
- _spawnve function
- spawnve function
- wspawnve function
- processes, creating
- _wspawnve function
- processes, executing new
- process creation
ms.assetid: 26d1713d-b551-4f21-a07b-e9891a2ae6cf
ms.openlocfilehash: 0f546185039bb1503af40d5f690fd8d8c172a679
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81355859"
---
# <a name="_spawnve-_wspawnve"></a>_spawnve, _wspawnve

Tworzy i wykonuje nowy proces.

> [!IMPORTANT]
> Tego interfejsu API nie można używać w aplikacjach wykonywanych w czasie wykonywania systemu Windows. Aby uzyskać więcej informacji, zobacz [funkcje CRT nieobjęte w aplikacjach platformy uniwersalnej systemu Windows](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md).

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

*nazwa cmd*<br/>
Ścieżka pliku, który ma zostać wykonany.

*Argv*<br/>
Tablica wskaźników do argumentów. Argument *argv*[0] jest zwykle wskaźnikiem do ścieżki w trybie rzeczywistym lub do nazwy programu w trybie chronionym, a *argv*[1] przez *argv*[**n**] są wskaźnikami do ciągów znaków tworzących nową listę argumentów. Argument *argv*[**n** +1] musi być wskaźnikiem **NULL,** aby oznaczyć koniec listy argumentów.

*Envp*<br/>
Tablica wskaźników do ustawień środowiska.

## <a name="return-value"></a>Wartość zwracana

Wartość zwracana z synchroniczowego **_spawnve** lub **_wspawnve** (**_P_WAIT** określony dla *trybu)* jest stanem zakończenia nowego procesu. Wartość zwracana z asynchronii **_spawnve** lub **_wspawnve** (**_P_NOWAIT** lub **_P_NOWAITO** określony dla *trybu)* jest uchwytem procesu. Stan zakończenia wynosi 0, jeśli proces został zakończony normalnie. Można ustawić stan zakończenia na wartość niezerową, jeśli zduplikowany proces w szczególności wywołuje procedurę **zakończenia** z argumentem niezerowym. Jeśli nowy proces nie ustawił jawnie dodatniego stanu zakończenia, stan wyjścia dodatniego wskazuje nieprawidłowe wyjście z przerwaniem lub przerwaniem. Zwracana wartość -1 wskazuje błąd (nowy proces nie jest uruchamiany). W takim przypadku **errno** jest ustawiona na jedną z następujących wartości.

|||
|-|-|
| **E2BIG ( E2BIG )** | Lista argumentów przekracza 1024 bajtów. |
| **Einval** | argument *mode* jest nieprawidłowy. |
| **Enoent** | Nie znaleziono pliku lub ścieżki. |
| **ENOEXEC ( ENOEXEC )** | Określony plik nie jest wykonywalny lub ma nieprawidłowy format pliku wykonywalnego. |
| **ENOMEM ( ENOMEM )** | Za mało pamięci jest dostępna do wykonania nowego procesu. |

Aby uzyskać więcej informacji na temat tych i innych kodów zwrotnych, zobacz [_doserrno, errno, _sys_errlist i _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

## <a name="remarks"></a>Uwagi

Każda z tych funkcji tworzy i wykonuje nowy proces, przekazując tablicę wskaźników do argumentów wiersza polecenia i tablicę wskaźników do ustawień środowiska.

Te funkcje sprawdzają ich parametry. Jeśli *cmdname* lub *argv* jest wskaźnikiem null lub jeśli *argv* wskazuje na wskaźnik null lub *argv*[0] jest pustym ciągiem, wywoływany jest nieprawidłowy program obsługi parametrów, zgodnie z opisem w [programie Sprawdzanie poprawności parametru.](../../c-runtime-library/parameter-validation.md) Jeśli wykonanie jest dozwolone, te funkcje ustawić **errno** na **EINVAL**i zwracać -1. Żaden nowy proces nie jest zrodzony.

Domyślnie stan globalny tej funkcji jest ograniczony do aplikacji. Aby to zmienić, zobacz [Stan globalny w crt](../global-state.md).

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|
|-------------|---------------------|
|**_spawnve**|\<stdio.h> lub \<process.h>|
|**_wspawnve**|\<stdio.h> lub \<wchar.h>|

Aby uzyskać więcej informacji o zgodności, zobacz [Zgodność](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Przykład

Zobacz przykład w [_spawn, _wspawn Funkcje](../../c-runtime-library/spawn-wspawn-functions.md).

## <a name="see-also"></a>Zobacz też

[Kontrola procesu i środowiska](../../c-runtime-library/process-and-environment-control.md)<br/>
[_spawn, _wspawn, funkcje](../../c-runtime-library/spawn-wspawn-functions.md)<br/>
[Przerwać](abort.md)<br/>
[atexit](atexit.md)<br/>
[_exec, funkcje _wexec](../../c-runtime-library/exec-wexec-functions.md)<br/>
[exit, _Exit, _exit](exit-exit-exit.md)<br/>
[_flushall](flushall.md)<br/>
[_getmbcp](getmbcp.md)<br/>
[_onexit, _onexit_m](onexit-onexit-m.md)<br/>
[_setmbcp](setmbcp.md)<br/>
[system, _wsystem](system-wsystem.md)<br/>
