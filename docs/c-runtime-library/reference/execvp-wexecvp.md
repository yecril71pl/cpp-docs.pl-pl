---
title: _execvp, _wexecvp
ms.date: 4/2/2020
api_name:
- _execvp
- _wexecvp
- _o__execvp
- _o__wexecvp
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
- _execvp
- wexecvp
- _wexecvp
helpviewer_keywords:
- _execvp function
- _wexecvp function
- wexecvp function
- execvp function
ms.assetid: a4db15df-b204-4987-be7c-de84c3414380
ms.openlocfilehash: 75b5c0ebe47c8f82ab8ad328dd21505c458a6ac8
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81347799"
---
# <a name="_execvp-_wexecvp"></a>_execvp, _wexecvp

Ładuje i wykonuje nowe procesy podrzędne.

> [!IMPORTANT]
> Tego interfejsu API nie można używać w aplikacjach wykonywanych w czasie wykonywania systemu Windows. Aby uzyskać więcej informacji, zobacz [funkcje CRT nieobjęte w aplikacjach platformy uniwersalnej systemu Windows](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md).

## <a name="syntax"></a>Składnia

```C
intptr_t _execvp(
   const char *cmdname,
   const char *const *argv
);
intptr_t _wexecvp(
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

Każda z tych funkcji ładuje i wykonuje nowy proces, przekazując tablicę wskaźników do argumentów wiersza polecenia i używając zmiennej środowiskowej **PATH,** aby znaleźć plik do wykonania.

Funkcje **_execvp** sprawdzają poprawność ich parametrów. Jeśli *cmdname* jest wskaźnik null lub *argv* jest wskaźnik null, wskaźnik do pustej tablicy lub jeśli tablica zawiera pusty ciąg jako pierwszy argument, funkcje te wywołać nieprawidłowy program obsługi parametrów, jak opisano w [sprawdzanie poprawności parametru](../../c-runtime-library/parameter-validation.md). Jeśli wykonanie jest dozwolone, te funkcje ustawić **errno** na **EINVAL** i zwracać -1. Żaden proces nie jest uruchamiany.

Domyślnie stan globalny tej funkcji jest ograniczony do aplikacji. Aby to zmienić, zobacz [Stan globalny w crt](../global-state.md).

## <a name="requirements"></a>Wymagania

|Funkcja|Wymagany nagłówek|Opcjonalny nagłówek|
|--------------|---------------------|---------------------|
|**_execvp**|\<> proces.h|\<> errno.h|
|**_wexecvp**|\<> process.h lub \<wchar.h>|\<> errno.h|

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
