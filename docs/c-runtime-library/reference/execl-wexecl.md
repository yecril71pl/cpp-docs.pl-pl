---
title: _execl, _wexecl
ms.date: 11/04/2016
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
helpviewer_keywords:
- _execl function
- wexecl function
- _wexecl function
- execl function
ms.assetid: 81fefb8a-0a06-4221-b2bc-be18e38e89f4
ms.openlocfilehash: 3d736849f90782425e6e1c1cff04536972318c91
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50530315"
---
# <a name="execl-wexecl"></a>_execl, _wexecl

Ładuje i uruchamia procesy podrzędne.

> [!IMPORTANT]
> Tego API nie można używać w aplikacjach korzystających ze środowiska wykonawczego Windows. Aby uzyskać więcej informacji, zobacz [funkcje CRT nieobsługiwane w aplikacjach platformy uniwersalnej Windows](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md).

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

W przypadku powodzenia, te funkcje nie zwracają procesu wywołującego. Zwracana wartość -1 wskazuje błąd, w którym to przypadku **errno** zmienna globalna jest ustawiona.

|errno wartość|Opis|
|-----------------|-----------------|
|**E2BIG**|Miejsce wymagane dla argumentów i ustawień środowiska przekracza 32 KB.|
|**EACCES**|Określony plik ma naruszenie zasad współużytkowania lub blokowania.|
|**EINVAL**|Nieprawidłowy parametr (jeden lub więcej parametrów było wskaźnikiem typu null lub pusty ciąg znaków).|
|**EMFILE**|Za dużo plików otwartych (do ustalenia, czy jest wykonywalny musi można otworzyć określonego pliku).|
|**ENOENT**|Nie znaleziono pliku lub ścieżki.|
|**ENOEXEC**|Określony plik nie jest wykonywalny lub ma nieprawidłowy format pliku wykonywalnego.|
|**ENOMEM**|Jest dostępna do wykonania nowego procesu; nie ma wystarczającej ilości pamięci dostępna pamięć jest uszkodzona; lub istnieje nieprawidłowy blok, wskazujący, że proces wywołujący nie został poprawnie przydzielony.|

## <a name="remarks"></a>Uwagi

Każda z tych funkcji ładuje i uruchamia nowy proces, przekazując każdy argument wiersza polecenia jako oddzielny parametr. Pierwszy argument jest poleceniem lub nazwą pliku wykonywalnego, a drugi argument funkcji powinna być taka sama, jak pierwsza. Staje się `argv[0]` w procesie wykonanym. Trzeci argument jest pierwszym argumentem, `argv[1]`, proces jest wykonywany.

**_Execl** funkcje sprawdzają poprawność swoich parametrów. Jeśli *cmdname* lub *arg0* jest wskaźnikiem typu null lub pustym ciągiem, funkcje te wywołują procedurę obsługi nieprawidłowego parametru, zgodnie z opisem w [Parameter Validation](../../c-runtime-library/parameter-validation.md) Jeśli wykonywania może być kontynuowane, te funkcje ustawiają **errno** do **EINVAL** i zwracają wartość -1. Żaden nowy proces jest wykonywany.

## <a name="requirements"></a>Wymagania

|Funkcja|Wymagany nagłówek|Opcjonalne nagłówki|
|--------------|---------------------|---------------------|
|**_execl**|\<process.h >|\<errno.h>|
|**_wexecl**|\<process.h > lub \<wchar.h >|\<errno.h>|

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
