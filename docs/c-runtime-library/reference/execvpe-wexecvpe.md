---
title: _execvpe, _wexecvpe
ms.date: 11/04/2016
apiname:
- _execvpe
- _wexecvpe
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
- wexecvpe
- execvpe
- _wexecvpe
- _execvpe
helpviewer_keywords:
- wexecvpe function
- execvpe function
- _wexecvpe function
- _execvpe function
ms.assetid: c0c3c986-d9c0-4814-a96c-10f0b3092766
ms.openlocfilehash: 064f8b94a9a97795015c09c11cd56e0370dcc60c
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50431697"
---
# <a name="execvpe-wexecvpe"></a>_execvpe, _wexecvpe

Ładuje i uruchamia procesy podrzędne.

> [!IMPORTANT]
> Tego API nie można używać w aplikacjach korzystających ze środowiska wykonawczego Windows. Aby uzyskać więcej informacji, zobacz [funkcje CRT nieobsługiwane w aplikacjach platformy uniwersalnej Windows](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md).

## <a name="syntax"></a>Składnia

```C
intptr_t _execvpe(
   const char *cmdname,
   const char *const *argv,
   const char *const *envp
);
intptr_t _wexecvpe(
   const wchar_t *cmdname,
   const wchar_t *const *argv,
   const wchar_t *const *envp
);
```

### <a name="parameters"></a>Parametry

*cmdname*<br/>
Ścieżka pliku do wykonania.

*ARGV*<br/>
Tablica wskaźników do parametrów.

*envp*<br/>
Tablica wskaźników do ustawienia środowiska.

## <a name="return-value"></a>Wartość zwracana

W przypadku powodzenia, te funkcje nie zwracają procesu wywołującego. Zwracana wartość -1 wskazuje błąd, w którym to przypadku **errno** zmienna globalna jest ustawiona.

|**errno** wartość|Opis|
|-------------------|-----------------|
|**E2BIG**|Miejsce, które są wymagane dla argumentów i ustawień środowiska przekracza 32 KB.|
|**EACCES**|Określony plik ma naruszenie zasad współużytkowania lub blokowania.|
|**EMFILE**|Zbyt wiele plików są otwarte. (Do ustalenia, czy jest wykonywalny musi można otworzyć określonego pliku.)|
|**ENOENT**|Nie znaleziono pliku lub ścieżki.|
|**ENOEXEC**|Określony plik nie jest wykonywalny lub ma nieprawidłowy format pliku wykonywalnego.|
|**ENOMEM**|Jest dostępna do wykonania nowego procesu; nie ma wystarczającej ilości pamięci dostępna pamięć jest uszkodzona; lub istnieje nieprawidłowy blok, który wskazuje, że proces wywołujący nie został poprawnie przydzielony.|

Aby uzyskać więcej informacji na temat tych i innych kodach powrotnych, zobacz [errno, _doserrno, _sys_errlist i _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

## <a name="remarks"></a>Uwagi

Każda z tych funkcji ładuje i uruchamia nowy proces i przekazuje tablicę wskaźników do argumentów wiersza polecenia oraz tablicę wskaźników do ustawienia środowiska. Te funkcje używają **ścieżki** zmiennej środowiskowej, aby znaleźć plik do wykonania.

**_Execvpe** funkcje sprawdzają poprawność swoich parametrów. Jeśli *cmdname* jest wskaźnikiem typu null, lub jeśli *argv* jest wskaźnikiem typu null, wskaźnikiem do pustej tablicy lub wskaźnika do tablicy, która zawiera pusty ciąg jako pierwszy argument, funkcje te wywołują nieprawidłowy Procedura obsługi nieprawidłowego parametru, zgodnie z opisem w [Parameter Validation](../../c-runtime-library/parameter-validation.md). Jeśli wykonanie może być kontynuowane, te funkcje ustawiają **errno** do **EINVAL** i zwracają wartość -1. Żaden proces jest uruchamiany.

## <a name="requirements"></a>Wymagania

|Funkcja|Wymagany nagłówek|Opcjonalne nagłówki|
|--------------|---------------------|---------------------|
|**_execvpe**|\<process.h >|\<errno.h>|
|**_wexecvpe**|\<process.h > lub \<wchar.h >|\<errno.h>|

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
