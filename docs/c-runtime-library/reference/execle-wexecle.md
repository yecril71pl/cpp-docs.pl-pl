---
title: _execle, _wexecle
ms.date: 11/04/2016
apiname:
- _execle
- _wexecle
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
- wexecle
- _execle
- _wexecle
helpviewer_keywords:
- wexecle function
- execle function
- _wexecle function
- _execle function
ms.assetid: 75efa9c5-96b7-4e23-acab-06258901f63a
ms.openlocfilehash: dbd84dd8d8e150a063dad4dc89a572c317bce544
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62288165"
---
# <a name="execle-wexecle"></a>_execle, _wexecle

Ładuje i uruchamia procesy podrzędne.

> [!IMPORTANT]
> Tego API nie można używać w aplikacjach korzystających ze środowiska wykonawczego Windows. Aby uzyskać więcej informacji, zobacz [funkcje CRT nieobsługiwane w aplikacjach platformy uniwersalnej Windows](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md).

## <a name="syntax"></a>Składnia

```C
intptr_t _execle(
   const char *cmdname,
   const char *arg0,
   ... const char *argn,
   NULL,
   const char *const *envp
);
intptr_t _wexecle(
   const wchar_t *cmdname,
   const wchar_t *arg0,
   ... const wchar_t *argn,
   NULL,
   const char *const *envp
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
|**E2BIG**|Miejsce, które są wymagane dla argumentów i ustawień środowiska przekracza 32 KB.|
|**EACCES**|Określony plik ma naruszenie zasad współużytkowania lub blokowania.|
|**EINVAL**|Nieprawidłowy parametr.|
|**EMFILE**|Zbyt wiele plików są otwarte. (Do ustalenia, czy jest wykonywalny musi można otworzyć określonego pliku.)|
|**ENOENT**|Nie znaleziono pliku lub ścieżki.|
|**ENOEXEC**|Określony plik nie jest wykonywalny lub ma nieprawidłowy format pliku wykonywalnego.|
|**ENOMEM**|Jest dostępna do wykonania nowego procesu; nie ma wystarczającej ilości pamięci dostępna pamięć jest uszkodzona; lub istnieje nieprawidłowy blok, który wskazuje, że proces wywołujący nie został poprawnie przydzielony.|

Aby uzyskać więcej informacji na temat tych kodów powrotnych, zobacz [_doserrno, errno, _sys_errlist i _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

## <a name="remarks"></a>Uwagi

Każda z tych funkcji ładuje i uruchamia nowy proces i przekazuje każdy argument wiersza polecenia jako oddzielny parametr i przekazuje tablicę wskaźników do ustawienia środowiska.

**_Execle —** funkcje sprawdzają poprawność swoich parametrów. Jeśli *cmdname* lub *arg0* jest wskaźnikiem typu null lub pustym ciągiem, funkcje te wywołują procedurę obsługi nieprawidłowego parametru, zgodnie z opisem w [Parameter Validation](../../c-runtime-library/parameter-validation.md). Jeśli wykonanie może być kontynuowane, te funkcje ustawiają **errno** do **EINVAL** i zwracają wartość -1. Żaden nowy proces zostanie uruchomiony.

## <a name="requirements"></a>Wymagania

|Funkcja|Wymagany nagłówek|Opcjonalne nagłówki|
|--------------|---------------------|---------------------|
|**_execle**|\<process.h>|\<errno.h>|
|**_wexecle**|\<process.h > lub \<wchar.h >|\<errno.h>|

Aby uzyskać więcej informacji, zobacz [zgodności](../../c-runtime-library/compatibility.md).

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
