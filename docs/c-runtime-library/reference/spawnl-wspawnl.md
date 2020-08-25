---
title: _spawnl, _wspawnl
ms.date: 11/04/2016
api_name:
- _wspawnl
- _spawnl
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
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- wspawnl
- _wspawnl
- _spawnl
helpviewer_keywords:
- spawnl function
- processes, creating
- _spawnl function
- processes, executing new
- _wspawnl function
- wspawnl function
- process creation
ms.assetid: dd4584c9-7173-4fc5-b93a-6e7d3c2316d7
ms.openlocfilehash: 4b51faae4ba6f371f712e4c39374ae9717c90bed
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/25/2020
ms.locfileid: "88834378"
---
# <a name="_spawnl-_wspawnl"></a>_spawnl, _wspawnl

Tworzy i uruchamia nowy proces.

> [!IMPORTANT]
> Tego interfejsu API nie można używać w aplikacjach, które są wykonywane w środowisko wykonawcze systemu Windows. Aby uzyskać więcej informacji, zobacz [funkcje CRT nieobsługiwane w aplikacjach platforma uniwersalna systemu Windows](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md).

## <a name="syntax"></a>Składnia

```C
intptr_t _spawnl(
   int mode,
   const char *cmdname,
   const char *arg0,
   const char *arg1,
   ... const char *argn,
   NULL
);
intptr_t _wspawnl(
   int mode,
   const wchar_t *cmdname,
   const wchar_t *arg0,
   const wchar_t *arg1,
   ... const wchar_t *argn,
   NULL
);
```

### <a name="parameters"></a>Parametry

*wyst*<br/>
Tryb wykonywania dla procesu wywołującego.

*cmdname*<br/>
Ścieżka pliku, który ma zostać wykonany.

*arg0*, *arg1*,... *argN*<br/>
Lista wskaźników do argumentów. Argument *arg0* jest zwykle wskaźnikiem do *cmdname*. Argumenty *arg1* przez *argN* są wskaźnikami do ciągów znaków tworzących nową listę argumentów. Po *argN*, aby oznaczyć koniec listy argumentów, musi istnieć **pusty** wskaźnik.

## <a name="return-value"></a>Wartość zwracana

Wartość zwracana z synchronicznej **_spawnl** lub **_wspawnl** (**_P_WAIT** określona dla *trybu*) jest stanem wyjścia nowego procesu. Wartość zwracana z asynchronicznej **_spawnl** lub **_wspawnl** (**_P_NOWAIT** lub **_P_NOWAITO** określona dla *trybu*) to dojście do procesu. Stan zakończenia to 0, jeśli proces został przerwany normalnie. Można ustawić stan zakończenia na wartość różną od zera, jeśli proces duplikowany jawnie wywoła procedurę **Exit** z niezerowym argumentem. Jeśli nowy proces nie ustawił jawnie stanu wyjścia pozytywnego, stan wyjścia pozytywnego wskazuje nietypowe wyjście z przerwaniem lub przerwaniem. Zwracana wartość-1 wskazuje błąd (nowy proces nie jest uruchomiony). W tym przypadku **errno** jest ustawiony na jedną z następujących wartości.

| Wartość | Opis |
|--|--|
| **E2BIG** | Lista argumentów przekracza 1024 bajtów. |
| **EINVAL** | argument *trybu* jest nieprawidłowy. |
| **ENOENT** | Nie znaleziono pliku lub ścieżki. |
| **ENOEXEC** | Określony plik nie jest wykonywalny lub ma nieprawidłowy format pliku wykonywalnego. |
| **ENOMEM** | Za mało dostępnej pamięci, aby wykonać nowy proces. |

Aby uzyskać więcej informacji na temat tych i innych kodów powrotnych, zobacz [_doserrno, errno, _sys_errlist i _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

Te funkcje sprawdzają poprawność swoich parametrów. Jeśli *cmdname* lub *arg0* jest pustym ciągiem lub pustym wskaźnikiem, zostanie wywołana procedura obsługi nieprawidłowego parametru, zgodnie z opisem w [walidacji parametru](../../c-runtime-library/parameter-validation.md). Jeśli wykonanie może być kontynuowane, te funkcje ustawiają **errno** na **EINVAL**i zwracają-1. Nie jest duplikowany żaden nowy proces.

## <a name="remarks"></a>Uwagi

Każda z tych funkcji tworzy i uruchamia nowy proces, przekazując każdy argument wiersza polecenia jako oddzielny parametr.

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|
|-------------|---------------------|
|**_spawnl**|\<process.h>|
|**_wspawnl**|\<stdio.h> lub \<wchar.h>|

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
