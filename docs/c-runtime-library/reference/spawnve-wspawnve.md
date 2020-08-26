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
- api-ms-win-crt-private-l1-1-0.dll
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
ms.openlocfilehash: dc6a6195987c1d5b323a86671de09dc28df84665
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/25/2020
ms.locfileid: "88836120"
---
# <a name="_spawnve-_wspawnve"></a>_spawnve, _wspawnve

Tworzy i uruchamia nowy proces.

> [!IMPORTANT]
> Tego interfejsu API nie można używać w aplikacjach, które są wykonywane w środowisko wykonawcze systemu Windows. Aby uzyskać więcej informacji, zobacz [funkcje CRT nieobsługiwane w aplikacjach platforma uniwersalna systemu Windows](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md).

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

*wyst*<br/>
Tryb wykonywania dla procesu wywołującego.

*cmdname*<br/>
Ścieżka pliku, który ma zostać wykonany.

*argv*<br/>
Tablica wskaźników do argumentów. Argument *argv*[0] jest zwykle wskaźnikiem do ścieżki w trybie rzeczywistym lub do nazwy programu w trybie chronionym, a *argv*[1] do *argv*[**n**] są wskaźnikami do ciągów znaków tworzących nową listę argumentów. Argument *argv*[**n** + 1] musi być **pustym** wskaźnikiem, aby zaznaczyć koniec listy argumentów.

*envp*<br/>
Tablica wskaźników do ustawień środowiska.

## <a name="return-value"></a>Wartość zwracana

Wartość zwracana z synchronicznej **_spawnve** lub **_wspawnve** (**_P_WAIT** określona dla *trybu*) jest stanem wyjścia nowego procesu. Wartość zwracana z asynchronicznej **_spawnve** lub **_wspawnve** (**_P_NOWAIT** lub **_P_NOWAITO** określona dla *trybu*) to dojście do procesu. Stan zakończenia to 0, jeśli proces został przerwany normalnie. Można ustawić stan zakończenia na wartość różną od zera, jeśli proces duplikowany jawnie wywoła procedurę **Exit** z niezerowym argumentem. Jeśli nowy proces nie ustawił jawnie stanu wyjścia pozytywnego, stan wyjścia pozytywnego wskazuje nietypowe wyjście z przerwaniem lub przerwaniem. Zwracana wartość-1 wskazuje błąd (nowy proces nie jest uruchomiony). W tym przypadku **errno** jest ustawiony na jedną z następujących wartości.

| Wartość | Opis |
|-|-|
| **E2BIG** | Lista argumentów przekracza 1024 bajtów. |
| **EINVAL** | argument *trybu* jest nieprawidłowy. |
| **ENOENT** | Nie znaleziono pliku lub ścieżki. |
| **ENOEXEC** | Określony plik nie jest wykonywalny lub ma nieprawidłowy format pliku wykonywalnego. |
| **ENOMEM** | Za mało dostępnej pamięci, aby wykonać nowy proces. |

Aby uzyskać więcej informacji na temat tych i innych kodów powrotnych, zobacz [_doserrno, errno, _sys_errlist i _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

## <a name="remarks"></a>Uwagi

Każda z tych funkcji tworzy i uruchamia nowy proces, przekazując tablicę wskaźników do argumentów wiersza polecenia oraz tablicę wskaźników do ustawień środowiska.

Te funkcje sprawdzają poprawność swoich parametrów. Jeśli *cmdname* lub *argv* jest wskaźnikiem typu null lub jeśli *argv* wskazuje na wskaźnik o wartości null lub *argv*[0] jest pustym ciągiem, zostanie wywołana procedura obsługi nieprawidłowego parametru, zgodnie z opisem w [walidacji parametru](../../c-runtime-library/parameter-validation.md). Jeśli wykonanie może być kontynuowane, te funkcje ustawiają **errno** na **EINVAL**i zwracają-1. Nie jest duplikowany żaden nowy proces.

Domyślnie globalny stan tej funkcji jest objęty zakresem aplikacji. Aby to zmienić, zobacz [stan globalny w CRT](../global-state.md).

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|
|-------------|---------------------|
|**_spawnve**|\<stdio.h> lub \<process.h>|
|**_wspawnve**|\<stdio.h> lub \<wchar.h>|

Aby uzyskać więcej informacji o zgodności, zobacz [zgodność](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Przykład

Zobacz przykład w [_spawn, _Wspawn Functions](../../c-runtime-library/spawn-wspawn-functions.md).

## <a name="see-also"></a>Zobacz też

[Proces i kontrola środowiska](../../c-runtime-library/process-and-environment-control.md)<br/>
[_spawn, funkcje _wspawn](../../c-runtime-library/spawn-wspawn-functions.md)<br/>
[przerwij](abort.md)<br/>
[atexit](atexit.md)<br/>
[_exec, funkcje _wexec](../../c-runtime-library/exec-wexec-functions.md)<br/>
[exit, _Exit, _exit](exit-exit-exit.md)<br/>
[_flushall](flushall.md)<br/>
[_getmbcp](getmbcp.md)<br/>
[_onexit, _onexit_m](onexit-onexit-m.md)<br/>
[_setmbcp](setmbcp.md)<br/>
[system, _wsystem](system-wsystem.md)<br/>
