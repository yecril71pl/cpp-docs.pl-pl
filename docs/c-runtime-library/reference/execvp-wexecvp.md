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
- api-ms-win-crt-private-l1-1-0.dll
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
ms.openlocfilehash: 224649abffd836667641f3c83e5f777f8752d7bd
ms.sourcegitcommit: 5a069c7360f75b7c1cf9d4550446ec2fa2eb2293
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/07/2020
ms.locfileid: "82915920"
---
# <a name="_execvp-_wexecvp"></a>_execvp, _wexecvp

Ładuje i wykonuje nowe procesy podrzędne.

> [!IMPORTANT]
> Tego interfejsu API nie można używać w aplikacjach, które są wykonywane w środowisko wykonawcze systemu Windows. Aby uzyskać więcej informacji, zobacz [funkcje CRT nieobsługiwane w aplikacjach platforma uniwersalna systemu Windows](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md).

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

*cmdname*<br/>
Ścieżka pliku do wykonania.

*argv*<br/>
Tablica wskaźników do parametrów.

## <a name="return-value"></a>Wartość zwracana

Jeśli to się powiedzie, te funkcje nie zwracają do procesu wywołującego. Zwracana wartość-1 wskazuje błąd, w którym to przypadku jest ustawiona zmienna globalna **errno** .

|**errno** wartość|Opis|
|-------------------|-----------------|
|**E2BIG**|Miejsce wymagane dla argumentów i ustawień środowiska przekracza 32 KB.|
|**EACCES**|Określony plik ma naruszenie zasad blokowania lub udostępniania.|
|**EINVAL**|Nieprawidłowy parametr.|
|**EMFILE**|Zbyt wiele plików jest otwartych (należy otworzyć określony plik, aby określić, czy jest to plik wykonywalny).|
|**ENOENT**|Nie znaleziono pliku lub ścieżki.|
|**ENOEXEC**|Określony plik nie jest wykonywalny lub ma nieprawidłowy format pliku wykonywalnego.|
|**ENOMEM**|Za mało dostępnej pamięci do wykonania nowego procesu; dostępna pamięć została uszkodzona; lub istnieje nieprawidłowy blok, wskazujący, że proces wywołujący nie został poprawnie przydzielony.|

Aby uzyskać więcej informacji na temat tych i innych kodów powrotnych, zobacz [_doserrno, errno, _sys_errlist i _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

## <a name="remarks"></a>Uwagi

Każda z tych funkcji ładuje i uruchamia nowy proces, przekazując tablicę wskaźników do argumentów wiersza polecenia i używając zmiennej środowiskowej **Path** do znalezienia pliku do wykonania.

Funkcje **_execvp** sprawdzają poprawność swoich parametrów. Jeśli *cmdname* jest wskaźnikiem typu null, lub *argv* jest wskaźnikiem typu null, wskaźnikiem do pustej tablicy, lub jeśli tablica zawiera pusty ciąg jako pierwszy argument, te funkcje wywołują procedurę obsługi nieprawidłowego parametru, zgodnie z opisem w [walidacji parametru](../../c-runtime-library/parameter-validation.md). Jeśli wykonanie może być kontynuowane, te funkcje ustawiają **errno** na **EINVAL** i Return-1. Żaden proces nie jest uruchamiany.

Domyślnie globalny stan tej funkcji jest objęty zakresem aplikacji. Aby to zmienić, zobacz [stan globalny w CRT](../global-state.md).

## <a name="requirements"></a>Wymagania

|Funkcja|Wymagany nagłówek|Opcjonalny nagłówek|
|--------------|---------------------|---------------------|
|**_execvp**|\<proces. h>|\<errno. h>|
|**_wexecvp**|\<Process. h> lub \<WCHAR. h>|\<errno. h>|

Aby uzyskać więcej informacji o zgodności, zobacz [zgodność](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Przykład

Zobacz przykład w [_exec, _Wexec Functions](../../c-runtime-library/exec-wexec-functions.md).

## <a name="see-also"></a>Zobacz też

[Proces i kontrola środowiska](../../c-runtime-library/process-and-environment-control.md)<br/>
[_exec, funkcje _wexec](../../c-runtime-library/exec-wexec-functions.md)<br/>
[Anuluj](abort.md)<br/>
[atexit](atexit.md)<br/>
[exit, _Exit, _exit](exit-exit-exit.md)<br/>
[_onexit, _onexit_m](onexit-onexit-m.md)<br/>
[_spawn, _wspawn, funkcje](../../c-runtime-library/spawn-wspawn-functions.md)<br/>
[system, _wsystem](system-wsystem.md)<br/>
