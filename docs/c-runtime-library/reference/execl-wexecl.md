---
title: _execl —, _wexecl — | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- _execl
- _wexecl
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
- _execl
- _wexecl
- wexecl
dev_langs:
- C++
helpviewer_keywords:
- _execl function
- wexecl function
- _wexecl function
- execl function
ms.assetid: 81fefb8a-0a06-4221-b2bc-be18e38e89f4
caps.latest.revision: 23
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 234a4f1b495c6cbfbcb047af58b6eec0f579ea61
ms.sourcegitcommit: ef859ddf5afea903711e36bfd89a72389a12a8d6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/20/2018
---
# <a name="execl-wexecl"></a>_execl, _wexecl

Ładuje i wykonuje nowych procesów podrzędnych.

> [!IMPORTANT]
> Nie można używać tego interfejsu API w aplikacjach, które są wykonywane w środowisku wykonawczym systemu Windows. Aby uzyskać więcej informacji, zobacz [funkcje CRT, nie są obsługiwane w aplikacjach platformy uniwersalnej systemu Windows](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md).

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
Ścieżka pliku do wykonania.

*arg0*,... *argn*<br/>
Lista wskaźników do parametrów.

## <a name="return-value"></a>Wartość zwracana

W przypadku powodzenia tych funkcji nie powróci do procesu wywołującego. Zwracana wartość -1 wskazuje błąd, w którym to przypadku **errno** ustawiono zmiennej globalnej.

|errno wartość|Opis|
|-----------------|-----------------|
|**E2BIG —**|Miejsce wymagane do argumentów i ustawienia środowiska przekracza 32 KB.|
|**EACCES**|Określony plik ma blokowania lub udostępniania naruszenie.|
|**EINVAL —**|Nieprawidłowy parametr (co najmniej jeden z parametrów jest wskaźnika o wartości null lub pusty ciąg).|
|**EMFILE —**|Za dużo plików Otwórz (czy jest pliku wykonywalnego musi można otworzyć określonego pliku).|
|**ENOENT —**|Nie znaleziono pliku lub ścieżki.|
|**ENOEXEC —**|Określony plik nie jest wykonywalne lub ma nieprawidłowy format pliku wykonywalnego.|
|**ENOMEM —**|Za mało pamięci jest dostępna do wykonania w nowym procesie; dostępna pamięć jest uszkodzona; lub istnieje nieprawidłowy blok, wskazujący, że proces wywołujący nie został poprawnie przydzielony.|

## <a name="remarks"></a>Uwagi

Każda z tych funkcji ładuje i wykonuje nowy proces, przekazywanie jako osobny parametr każdy argument wiersza polecenia. Pierwszy argument jest polecenia lub nazwa pliku wykonywalnego, a drugi argument powinna być taka sama jak pierwsza. Staje się on `argv[0]` wykonanie procesu. Trzeci argument jest pierwszy argument `argv[1]`, wykonywana procesu.

**_Execl —** funkcje walidację ich parametrów. Jeśli dowolny *cmdname* lub *arg0* wskaźnika o wartości null lub pusty ciąg, te funkcje Wywołaj program obsługi nieprawidłowych parametrów, zgodnie z opisem w [sprawdzanie poprawności parametru](../../c-runtime-library/parameter-validation.md) Jeśli wykonywania będzie mógł kontynuować, ustawianie tych funkcji **errno** do **einval —** i zwróć -1. Żaden nowy proces jest wykonywany.

## <a name="requirements"></a>Wymagania

|Funkcja|Wymagany nagłówek|Opcjonalne nagłówki|
|--------------|---------------------|---------------------|
|**_execl**|\<process.h >|\<errno.h>|
|**_wexecl**|\<process.h > lub \<wchar.h >|\<errno.h>|

Aby uzyskać więcej informacji o zgodności, zobacz [zgodności](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Przykład

Zapoznaj się z przykładem w [_execwexec — funkcje](../../c-runtime-library/exec-wexec-functions.md).

## <a name="see-also"></a>Zobacz także

[Procedury kontroli środowiska](../../c-runtime-library/process-and-environment-control.md)<br/>
[_exec, _wexec, funkcje](../../c-runtime-library/exec-wexec-functions.md)<br/>
[abort](abort.md)<br/>
[atexit](atexit.md)<br/>
[exit, _Exit, _exit](exit-exit-exit.md)<br/>
[_onexit, _onexit_m](onexit-onexit-m.md)<br/>
[_spawn, _wspawn, funkcje](../../c-runtime-library/spawn-wspawn-functions.md)<br/>
[system, _wsystem](system-wsystem.md)<br/>
