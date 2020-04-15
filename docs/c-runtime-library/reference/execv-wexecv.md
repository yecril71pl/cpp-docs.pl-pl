---
title: _execv, _wexecv
ms.date: 4/2/2020
api_name:
- _wexecv
- _execv
- _o__execv
- _o__wexecv
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
- _execv
- _wexecv
- wexecv
helpviewer_keywords:
- _wexecv function
- _execv function
- wexecv function
- execv function
ms.assetid: 8dbaf7bc-9040-4316-a0c1-db7e866b52af
ms.openlocfilehash: 638364afa75fa1b04b598370473dee48964c5763
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81347892"
---
# <a name="_execv-_wexecv"></a>_execv, _wexecv

Ładuje i wykonuje nowe procesy podrzędne.

> [!IMPORTANT]
> Tego interfejsu API nie można używać w aplikacjach wykonywanych w czasie wykonywania systemu Windows. Aby uzyskać więcej informacji, zobacz [funkcje CRT nieobjęte w aplikacjach platformy uniwersalnej systemu Windows](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md).

## <a name="syntax"></a>Składnia

```C
intptr_t _execv(
   const char *cmdname,
   const char *const *argv
);
intptr_t _wexecv(
   const wchar_t *cmdname,
   const wchar_t *const *argv
);
```

### <a name="parameters"></a>Parametry

*nazwa cmd*<br/>
Ścieżka pliku do wykonania.

*Argv*<br/>
Tablica wskaźników do parametrów.

## <a name="return-value"></a>Wartość zwracana

Jeśli się powiedzie, te funkcje nie powrócić do procesu wywołującego. Zwracana wartość -1 wskazuje błąd, w którym to przypadku ustawiona jest zmienna globalna **errno.**

|**wartość errno**|Opis|
|-------------------|-----------------|
|**E2BIG ( E2BIG )**|Miejsce wymagane dla argumentów i ustawień środowiska przekracza 32 KB.|
|**EACCES ( EACCES )**|Określony plik ma naruszenie blokowania lub udostępniania.|
|**Einval**|Nieprawidłowy parametr.|
|**EMFILE (EMFILE)**|Zbyt wiele otwartych plików (określony plik musi zostać otwarty, aby ustalić, czy jest wykonywalny).|
|**Enoent**|Nie znaleziono pliku lub ścieżki.|
|**ENOEXEC ( ENOEXEC )**|Określony plik nie jest wykonywalny lub ma nieprawidłowy format pliku wykonywalnego.|
|**ENOMEM ( ENOMEM )**|Za mało pamięci jest dostępna do wykonania nowego procesu; dostępna pamięć została uszkodzona; lub istnieje nieprawidłowy blok, co oznacza, że proces wywołujący nie został prawidłowo przydzielony.|

Aby uzyskać więcej informacji na temat tych i innych kodów zwrotnych, zobacz [_doserrno, errno, _sys_errlist i _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

## <a name="remarks"></a>Uwagi

Każda z tych funkcji ładuje i wykonuje nowy proces, przekazując tablicę wskaźników do argumentów wiersza polecenia.

Funkcje **_execv** sprawdzają poprawność ich parametrów. Jeśli *cmdname* jest wskaźnikiem null lub jeśli *argv* jest wskaźnikiem null, wskaźnik do pustej tablicy lub jeśli tablica zawiera pusty ciąg jako pierwszy argument, **_execv** funkcje wywołać nieprawidłowy program obsługi parametrów, jak opisano w [weryfikacji parametrów](../../c-runtime-library/parameter-validation.md). Jeśli wykonanie jest dozwolone, te funkcje ustawić **errno** na **EINVAL** i zwracać -1. Żaden proces nie jest uruchamiany.

Domyślnie stan globalny tej funkcji jest ograniczony do aplikacji. Aby to zmienić, zobacz [Stan globalny w crt](../global-state.md).

## <a name="requirements"></a>Wymagania

|Funkcja|Wymagany nagłówek|Opcjonalny nagłówek|
|--------------|---------------------|---------------------|
|**_execv**|\<> proces.h|\<> errno.h|
|**_wexecv**|\<> process.h lub \<wchar.h>|\<> errno.h|

Aby uzyskać więcej informacji o zgodności, zobacz [Zgodność](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Przykład

Zobacz przykład w [_exec, _wexec Funkcje](../../c-runtime-library/exec-wexec-functions.md).

## <a name="see-also"></a>Zobacz też

[Kontrola procesu i środowiska](../../c-runtime-library/process-and-environment-control.md)<br/>
[_exec, funkcje _wexec](../../c-runtime-library/exec-wexec-functions.md)<br/>
[Przerwać](abort.md)<br/>
[atexit](atexit.md)<br/>
[exit, _Exit, _exit](exit-exit-exit.md)<br/>
[_onexit, _onexit_m](onexit-onexit-m.md)<br/>
[_spawn, _wspawn, funkcje](../../c-runtime-library/spawn-wspawn-functions.md)<br/>
[system, _wsystem](system-wsystem.md)<br/>
