---
title: _execlp —, _wexeclp — | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- _wexeclp
- _execlp
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
- _wexeclp
- wexeclp
- _execlp
dev_langs:
- C++
helpviewer_keywords:
- execlp function
- _execlp function
- _wexeclp function
- wexeclp function
ms.assetid: 7b179163-4bcd-4d6a-8baf-68f886791928
caps.latest.revision: 22
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 460b37a2c9e14536efa56e6a4d27c74efee7799a
ms.sourcegitcommit: ef859ddf5afea903711e36bfd89a72389a12a8d6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/20/2018
---
# <a name="execlp-wexeclp"></a>_execlp, _wexeclp

Ładuje i wykonuje nowych procesów podrzędnych.

> [!IMPORTANT]
> Nie można używać tego interfejsu API w aplikacjach, które są wykonywane w środowisku wykonawczym systemu Windows. Aby uzyskać więcej informacji, zobacz [funkcje CRT, nie są obsługiwane w aplikacjach platformy uniwersalnej systemu Windows](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md).

## <a name="syntax"></a>Składnia

```C
intptr_t _execlp(
   const char *cmdname,
   const char *arg0,
   ... const char *argn,
   NULL
);
intptr_t _wexeclp(
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

|**errno** wartości|Opis|
|-------------------|-----------------|
|**E2BIG —**|Miejsce wymagane do argumentów i ustawienia środowiska przekracza 32 KB.|
|**EACCES**|Określony plik ma blokowania lub udostępniania naruszenie.|
|**EINVAL —**|Nieprawidłowy parametr.|
|**EMFILE —**|Za dużo plików Otwórz (czy jest pliku wykonywalnego musi można otworzyć określonego pliku).|
|**ENOENT —**|Plik lub nie można odnaleźć ścieżki.|
|**ENOEXEC —**|Określony plik nie jest wykonywalne lub ma nieprawidłowy format pliku wykonywalnego.|
|**ENOMEM —**|Za mało pamięci jest dostępna do wykonania w nowym procesie; dostępna pamięć jest uszkodzona; lub istnieje nieprawidłowy blok, wskazujący, że proces wywołujący nie został poprawnie przydzielony.|

Aby uzyskać więcej informacji na temat tych i innych kody powrotu, zobacz [_doserrno —, errno, _sys_errlist — i _sys_nerr —](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

## <a name="remarks"></a>Uwagi

Każda z tych funkcji ładuje i wykonuje nowego procesu przekazywania każdy argument wiersza polecenia jako osobny parametr i przy użyciu **ścieżki** zmiennej środowiskowej można znaleźć pliku do wykonania.

**_Execlp —** funkcje walidację ich parametrów. Jeśli *cmdname* lub *arg0* wskaźnika o wartości null lub pusty ciąg, te funkcje Wywołaj program obsługi nieprawidłowych parametrów, zgodnie z opisem w [sprawdzanie poprawności parametru](../../c-runtime-library/parameter-validation.md). Jeśli dozwolone jest wykonywanie aby kontynuować, ustawianie tych funkcji **errno** do **einval —** i zwróć -1. Żaden nowy proces jest uruchomiony.

## <a name="requirements"></a>Wymagania

|Funkcja|Wymagany nagłówek|Opcjonalne nagłówki|
|--------------|---------------------|---------------------|
|**_execlp —**|\<process.h >|\<errno.h>|
|**_wexeclp**|\<process.h > lub \<wchar.h >|\<errno.h>|

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
