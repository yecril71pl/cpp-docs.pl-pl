---
title: _execl, _wexecl
ms.date: 11/04/2016
api_name:
- _execl
- _wexecl
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
- _execl
- _wexecl
- wexecl
helpviewer_keywords:
- _execl function
- wexecl function
- _wexecl function
- execl function
ms.assetid: 81fefb8a-0a06-4221-b2bc-be18e38e89f4
ms.openlocfilehash: 714ef80c4909e92100c4fa869b7544239f8edeb7
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/12/2019
ms.locfileid: "70941949"
---
# <a name="_execl-_wexecl"></a>_execl, _wexecl

Ładuje i wykonuje nowe procesy podrzędne.

> [!IMPORTANT]
> Tego interfejsu API nie można używać w aplikacjach, które są wykonywane w środowisko wykonawcze systemu Windows. Aby uzyskać więcej informacji, zobacz [funkcje CRT nieobsługiwane w aplikacjach platforma uniwersalna systemu Windows](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md).

## <a name="syntax"></a>Składnia

```C
intptr_t _execl(
   const char *cmdname,
   const char *arg0,
   ... const char *argn,
   NULL
);
intptr_t _wexecl(
   const wchar_t *cmdname,
   const wchar_t *arg0,
   ... const wchar_t *argn,
   NULL
);
```

### <a name="parameters"></a>Parametry

*cmdname*<br/>
Ścieżka pliku, który ma zostać wykonany.

*arg0*,... *argN*<br/>
Lista wskaźników do parametrów.

## <a name="return-value"></a>Wartość zwracana

Jeśli to się powiedzie, te funkcje nie zwracają do procesu wywołującego. Zwracana wartość-1 wskazuje błąd, w którym to przypadku jest ustawiona zmienna globalna **errno** .

|errno wartość|Opis|
|-----------------|-----------------|
|**E2BIG**|Miejsce wymagane dla argumentów i ustawień środowiska przekracza 32 KB.|
|**EACCES**|Określony plik ma naruszenie zasad blokowania lub udostępniania.|
|**EINVAL**|Nieprawidłowy parametr (co najmniej jeden z parametrów był wskaźnikiem typu null lub ciągiem pustym).|
|**EMFILE**|Zbyt wiele plików jest otwartych (należy otworzyć określony plik, aby określić, czy jest to plik wykonywalny).|
|**ENOENT**|Nie znaleziono pliku lub ścieżki.|
|**ENOEXEC**|Określony plik nie jest wykonywalny lub ma nieprawidłowy format pliku wykonywalnego.|
|**ENOMEM**|Za mało dostępnej pamięci do wykonania nowego procesu; dostępna pamięć została uszkodzona; lub istnieje nieprawidłowy blok, wskazujący, że proces wywołujący nie został poprawnie przydzielony.|

## <a name="remarks"></a>Uwagi

Każda z tych funkcji ładuje i uruchamia nowy proces, przekazując każdy argument wiersza polecenia jako oddzielny parametr. Pierwszy argument jest poleceniem lub nazwą pliku wykonywalnego, a drugi argument powinien być taki sam jak pierwszy. Zostanie `argv[0]` ona przeprowadzony w procesie. Trzeci argument jest pierwszym argumentem `argv[1]`, z którego wykonywany jest proces.

Funkcje **_execl** sprawdzają poprawność swoich parametrów. Jeśli *cmdname* lub *arg0* jest wskaźnikiem o wartości null lub pustym ciągiem, te funkcje wywołują procedurę obsługi nieprawidłowego parametru, zgodnie z opisem w [walidacji parametru](../../c-runtime-library/parameter-validation.md) , jeśli wykonanie może być kontynuowane, te funkcje ustawiają **errno** na  **EINVAL** i Return-1. Żaden nowy proces nie jest wykonywany.

## <a name="requirements"></a>Wymagania

|Funkcja|Wymagany nagłówek|Opcjonalny nagłówek|
|--------------|---------------------|---------------------|
|**_execl**|\<process.h>|\<errno.h>|
|**_wexecl**|\<Process. h > lub \<WCHAR. h >|\<errno.h>|

Aby uzyskać więcej informacji o zgodności, zobacz [zgodność](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Przykład

Zobacz przykład w [_exec, _Wexec Functions](../../c-runtime-library/exec-wexec-functions.md).

## <a name="see-also"></a>Zobacz także

[Procedury kontroli środowiska](../../c-runtime-library/process-and-environment-control.md)<br/>
[_exec, _wexec, funkcje](../../c-runtime-library/exec-wexec-functions.md)<br/>
[abort](abort.md)<br/>
[atexit](atexit.md)<br/>
[exit, _Exit, _exit](exit-exit-exit.md)<br/>
[_onexit, _onexit_m](onexit-onexit-m.md)<br/>
[_spawn, _wspawn, funkcje](../../c-runtime-library/spawn-wspawn-functions.md)<br/>
[system, _wsystem](system-wsystem.md)<br/>
