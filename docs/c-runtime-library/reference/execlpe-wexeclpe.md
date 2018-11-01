---
title: _execlpe, _wexeclpe
ms.date: 11/04/2016
apiname:
- _execlpe
- _wexeclpe
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
- _wexeclpe
- execlpe
- wexeclpe
- _execlpe
helpviewer_keywords:
- wexeclpe function
- _wexeclpe function
- _execlpe function
- execlpe function
ms.assetid: 07b861da-3e7e-4f1d-bb80-ad69b55e5162
ms.openlocfilehash: e3aa4189d2a384a0092c742909e97c5efc52b5ff
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50506863"
---
# <a name="execlpe-wexeclpe"></a>_execlpe, _wexeclpe

Ładuje i uruchamia procesy podrzędne.

> [!IMPORTANT]
> Tego API nie można używać w aplikacjach korzystających ze środowiska wykonawczego Windows. Aby uzyskać więcej informacji, zobacz [funkcje CRT nieobsługiwane w aplikacjach platformy uniwersalnej Windows](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md).

## <a name="syntax"></a>Składnia

```C
intptr_t _execlpe(
   const char *cmdname,
   const char *arg0,
   ... const char *argn,
   NULL,
   const char *const *envp
);
intptr_t _wexeclpe(
   const wchar_t *cmdname,
   const wchar_t *arg0,
   ... const wchar_t *argn,
   NULL,
   const wchar_t *const *envp
);
```

### <a name="parameters"></a>Parametry

*cmdname*<br/>
Ścieżka pliku do wykonania.

*arg0*,... *argn*<br/>
Lista wskaźników do parametrów.

*envp*<br/>
Tablica wskaźników do ustawienia środowiska.

## <a name="return-value"></a>Wartość zwracana

W przypadku powodzenia, te funkcje nie zwracają procesu wywołującego. Zwracana wartość -1 wskazuje błąd, w którym to przypadku **errno** zmienna globalna jest ustawiona.

|**errno** wartość|Opis|
|-------------------|-----------------|
|**E2BIG**|Miejsce wymagane dla argumentów i ustawień środowiska przekracza 32 KB.|
|**EACCES**|Określony plik ma naruszenie zasad współużytkowania lub blokowania.|
|**EINVAL**|Nieprawidłowy parametr.|
|**EMFILE**|Za dużo plików otwartych (do ustalenia, czy jest wykonywalny musi można otworzyć określonego pliku).|
|**ENOENT**|Plik lub nie można odnaleźć ścieżki.|
|**ENOEXEC**|Określony plik nie jest wykonywalny lub ma nieprawidłowy format pliku wykonywalnego.|
|**ENOMEM**|Jest dostępna do wykonania nowego procesu; nie ma wystarczającej ilości pamięci dostępna pamięć jest uszkodzona; lub istnieje nieprawidłowy blok, wskazujący, że proces wywołujący nie został poprawnie przydzielony.|

Aby uzyskać więcej informacji na temat tych i innych kodach powrotnych, zobacz [_doserrno, errno, _sys_errlist i _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

## <a name="remarks"></a>Uwagi

Każda z tych funkcji ładuje i uruchamia nowy proces, przekazując każdy argument wiersza polecenia jako oddzielny parametr i przekazując także tablicę wskaźników do ustawienia środowiska. Te funkcje używają **ścieżki** zmiennej środowiskowej, aby znaleźć plik do wykonania.

**_Execlpe —** funkcje sprawdzają poprawność swoich parametrów. Jeśli *cmdname* lub *arg0* są pustymi wskaźnikami lub pustym ciągiem, funkcje te wywołują procedurę obsługi nieprawidłowego parametru, zgodnie z opisem w [Parameter Validation](../../c-runtime-library/parameter-validation.md). Jeśli wykonanie może być kontynuowane, te funkcje ustawiają **errno** do **EINVAL** i zwracają wartość -1. Żaden nowy proces zostanie uruchomiony.

## <a name="requirements"></a>Wymagania

|Funkcja|Wymagany nagłówek|Opcjonalne nagłówki|
|--------------|---------------------|---------------------|
|**_execlpe**|\<process.h >|\<errno.h>|
|**_wexeclpe**|\<process.h > lub \<wchar.h >|\<errno.h>|

Aby uzyskać więcej informacji na temat zgodności, zobacz [zgodności](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Przykład

Zobacz przykład w [_exec, _wexec — funkcje](../../c-runtime-library/exec-wexec-functions.md).

## <a name="see-also"></a>Zobacz także

[Procedury kontroli środowiska](../../c-runtime-library/process-and-environment-control.md)<br/>
[_exec, _wexec, funkcje](../../c-runtime-library/exec-wexec-functions.md)<br/>
[abort](abort.md)<br/>
[atexit](atexit.md)<br/>
[exit, _Exit, _exit](exit-exit-exit.md)<br/>
[_onexit, _onexit_m](onexit-onexit-m.md)<br/>
[_spawn, _wspawn, funkcje](../../c-runtime-library/spawn-wspawn-functions.md)<br/>
[system, _wsystem](system-wsystem.md)<br/>
