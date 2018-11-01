---
title: _spawnl, _wspawnl
ms.date: 11/04/2016
apiname:
- _wspawnl
- _spawnl
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
- spawnl
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
ms.openlocfilehash: 4dbc8fab611d98f7f87529196b0e10e85196faa9
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50518082"
---
# <a name="spawnl-wspawnl"></a>_spawnl, _wspawnl

Tworzy i uruchamia nowy proces.

> [!IMPORTANT]
> Tego API nie można używać w aplikacjach korzystających ze środowiska wykonawczego Windows. Aby uzyskać więcej informacji, zobacz [funkcje CRT nieobsługiwane w aplikacjach platformy uniwersalnej Windows](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md).

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

*Tryb*<br/>
Tryb wykonywania dla procesu wywołującego.

*cmdname*<br/>
Ścieżka pliku do wykonania.

*arg0*, *arg1*,... *argn*<br/>
Lista wskaźników do argumentów. *Arg0* argument jest zazwyczaj wskaźnikiem do *cmdname*. Argumenty *arg1* za pośrednictwem *argn* są wskaźnikami do ciągów znaków tworzących nowe listy argumentów. Następujące *argn*, musi istnieć **NULL** wskaźnik, aby zaznaczyć koniec listy argumentów.

## <a name="return-value"></a>Wartość zwracana

Wartość zwracana przez synchroniczny **_spawnl** lub **_wspawnl —** (**_P_WAIT** określony dla *tryb*) jest stanem wyjścia nowego procesu. Wartość zwracana przez synchroniczny **_spawnl** lub **_wspawnl —** (**_P_NOWAIT** lub **_P_NOWAITO** określony dla *tryb* ) jest dojściem do procesu. Stanem wyjścia wynosi 0, jeżeli proces zakończył się normalnie. Możesz ustawić stan wyjścia na wartość różną od zera, jeśli procesu rozmnożonego w szczególności wywołuje **wyjść** rutynę z argumentem wartość różną od zera. Jeśli nowy proces nie ustawi jawnie stanu wyjścia, stan wyjścia wskazuje nietypowe wyjście z porzuceniem lub przerwaniem. Zwracana wartość-1 wskazuje błąd (nowy proces nie jest uruchomiony). W tym przypadku **errno** jest ustawiony na jedną z następujących wartości.

|||
|-|-|
**E2BIG**|Argument w postaci listy przekracza 1024 bajty.
**EINVAL**|*tryb* argument jest nieprawidłowy.
**ENOENT**|Nie znaleziono pliku lub ścieżki.
**ENOEXEC**|Określony plik nie jest wykonywalny lub ma nieprawidłowy format pliku wykonywalnego.
**ENOMEM**|Nie ma wystarczającej ilości pamięci jest dostępna do wykonania nowego procesu.

Aby uzyskać więcej informacji na temat tych i innych kodach powrotnych, zobacz [_doserrno, errno, _sys_errlist i _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

Te funkcje sprawdzają poprawność swoich parametrów. Jeśli *cmdname* lub *arg0* jest pustym ciągiem lub wskaźnikiem typu null, procedura obsługi nieprawidłowego parametru zostanie wywołana, zgodnie z opisem w [Parameter Validation](../../c-runtime-library/parameter-validation.md). Jeśli wykonanie może być kontynuowane, te funkcje ustawiają **errno** do **EINVAL**i zwracają wartość -1. Żaden nowy proces nie jest rozprzestrzeniony.

## <a name="remarks"></a>Uwagi

Każda z tych funkcji tworzy i uruchamia nowy proces, przekazując każdy argument wiersza polecenia jako oddzielny parametr.

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|
|-------------|---------------------|
|**_spawnl**|\<process.h >|
|**_wspawnl —**|\<stdio.h > lub \<wchar.h >|

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
