---
title: _chdrive
ms.date: 11/04/2016
apiname:
- _chdrive
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
- api-ms-win-crt-filesystem-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- chdrive
- _chdrive
helpviewer_keywords:
- drives, changing
- _chdrive function
- chdrive function
ms.assetid: 212a1a4b-4fa8-444e-9677-7fca4c8c47e3
ms.openlocfilehash: 963b7b7b40b632981abfc1529beb9c48a5b991ba
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50602309"
---
# <a name="chdrive"></a>_chdrive

Zmienia bieżący dysk roboczy.

> [!IMPORTANT]
> Tego API nie można używać w aplikacjach korzystających ze środowiska wykonawczego Windows. Aby uzyskać więcej informacji, zobacz [funkcje CRT nieobsługiwane w aplikacjach platformy uniwersalnej Windows](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md).

## <a name="syntax"></a>Składnia

```C
int _chdrive(
   int drive
);
```

### <a name="parameters"></a>Parametry

*Dysk*<br/>
Liczba całkowita z zakresu od 1 do 26, która określa bieżący działający napęd (1 = A, 2 = B i tak dalej).

## <a name="return-value"></a>Wartość zwracana

Zero (0), jeśli bieżący dysk pracy został zmieniona pomyślnie; w przeciwnym razie, wartość -1.

## <a name="remarks"></a>Uwagi

Jeśli *dysku* jest nie jest w zakresie od 1 do 26, zostanie wywołany nieprawidłowy — parametr uchwytu, zgodnie z opisem w [Parameter Validation](../../c-runtime-library/parameter-validation.md). Jeśli wykonanie może być kontynuowane, **_chdrive —** funkcja zwraca wartość -1, **errno** ustawiono **EACCES**, i **_doserrno** jest ustawiona na  **ERROR_INVALID_DRIVE**.

**_Chdrive —** funkcja nie jest bezpieczna dla wątków, ponieważ zależy ona **SetCurrentDirectory** funkcja, która sama nie metodą o bezpiecznych wątkach. Aby użyć **_chdrive —** bezpiecznie w przypadku aplikacji wielowątkowych, należy dostarczyć własnej synchronizacji wątków. Aby uzyskać więcej informacji, zobacz [SetCurrentDirectory](/windows/desktop/api/winbase/nf-winbase-setcurrentdirectory).

**_Chdrive —** funkcji zmienia tylko bieżącą pracę dysku;  **_chdir —** zmienia bieżący katalog roboczy.

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|
|-------------|---------------------|
|**_chdrive**|\<direct.h>|

Aby uzyskać więcej informacji, zobacz [zgodności](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Przykład

Zobacz przykład [_getdrive —](getdrive.md).

## <a name="see-also"></a>Zobacz także

[Kontrola katalogu](../../c-runtime-library/directory-control.md)<br/>
[_chdir, _wchdir](chdir-wchdir.md)<br/>
[_fullpath, _wfullpath](fullpath-wfullpath.md)<br/>
[_getcwd, _wgetcwd](getcwd-wgetcwd.md)<br/>
[_getdrive](getdrive.md)<br/>
[_mkdir, _wmkdir](mkdir-wmkdir.md)<br/>
[_rmdir, _wrmdir](rmdir-wrmdir.md)<br/>
[system, _wsystem](system-wsystem.md)<br/>
