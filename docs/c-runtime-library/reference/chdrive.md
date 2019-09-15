---
title: _chdrive
ms.date: 11/04/2016
api_name:
- _chdrive
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
- api-ms-win-crt-filesystem-l1-1-0.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- chdrive
- _chdrive
helpviewer_keywords:
- drives, changing
- _chdrive function
- chdrive function
ms.assetid: 212a1a4b-4fa8-444e-9677-7fca4c8c47e3
ms.openlocfilehash: 3ee292c03c9d31944e0a555c2159d7a5dd2cd0eb
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/12/2019
ms.locfileid: "70939245"
---
# <a name="_chdrive"></a>_chdrive

Zmienia bieżący dysk roboczy.

> [!IMPORTANT]
> Tego interfejsu API nie można używać w aplikacjach, które są wykonywane w środowisko wykonawcze systemu Windows. Aby uzyskać więcej informacji, zobacz [funkcje CRT nieobsługiwane w aplikacjach platforma uniwersalna systemu Windows](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md).

## <a name="syntax"></a>Składnia

```C
int _chdrive(
   int drive
);
```

### <a name="parameters"></a>Parametry

*litera*<br/>
Liczba całkowita z zakresu od 1 do 26 określająca bieżący dysk roboczy (1 = A, 2 = B i tak dalej).

## <a name="return-value"></a>Wartość zwracana

Zero (0), jeśli bieżący dysk roboczy został pomyślnie zmieniony; w przeciwnym razie-1.

## <a name="remarks"></a>Uwagi

Jeśli *dysk* nie należy do zakresu od 1 do 26, procedura obsługi nieprawidłowego parametru jest wywoływana, zgodnie z opisem w [walidacji parametru](../../c-runtime-library/parameter-validation.md). Jeśli wykonanie może być kontynuowane, funkcja **_chdrive** zwraca wartość-1, **errno** jest ustawiona na wartość **EACCES**, a **_doserrno** jest ustawiona na **ERROR_INVALID_DRIVE**.

Funkcja **_chdrive** nie jest bezpieczna wątkowo, ponieważ zależy od funkcji **SetCurrentDirectory** , która sama nie jest bezpieczna wątkowo. Aby bezpiecznie używać **_chdrive** w aplikacji wielowątkowej, musisz zapewnić synchronizację własnych wątków. Aby uzyskać więcej informacji, zobacz [SetCurrentDirectory](/windows/win32/api/winbase/nf-winbase-setcurrentdirectory).

Funkcja **_chdrive** zmienia tylko bieżący dysk roboczy;  **_chdir** zmienia bieżący katalog roboczy.

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|
|-------------|---------------------|
|**_chdrive**|\<direct.h>|

Aby uzyskać więcej informacji, zobacz [zgodność](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Przykład

Zobacz przykład dla [_getdrive](getdrive.md).

## <a name="see-also"></a>Zobacz także

[Kontrola katalogu](../../c-runtime-library/directory-control.md)<br/>
[_chdir, _wchdir](chdir-wchdir.md)<br/>
[_fullpath, _wfullpath](fullpath-wfullpath.md)<br/>
[_getcwd, _wgetcwd](getcwd-wgetcwd.md)<br/>
[_getdrive](getdrive.md)<br/>
[_mkdir, _wmkdir](mkdir-wmkdir.md)<br/>
[_rmdir, _wrmdir](rmdir-wrmdir.md)<br/>
[system, _wsystem](system-wsystem.md)<br/>
