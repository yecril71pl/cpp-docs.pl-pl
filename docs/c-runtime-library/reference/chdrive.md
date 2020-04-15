---
title: _chdrive
ms.date: 4/2/2020
api_name:
- _chdrive
- _o__chdrive
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
- api-ms-win-crt-private-l1-1-0
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
ms.openlocfilehash: 0c19fefcf6a766842ee2e25cbe6bdb61bbf48e7d
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81333348"
---
# <a name="_chdrive"></a>_chdrive

Zmienia bieżący dysk roboczy.

> [!IMPORTANT]
> Tego interfejsu API nie można używać w aplikacjach wykonywanych w czasie wykonywania systemu Windows. Aby uzyskać więcej informacji, zobacz [funkcje CRT nieobjęte w aplikacjach platformy uniwersalnej systemu Windows](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md).

## <a name="syntax"></a>Składnia

```C
int _chdrive(
   int drive
);
```

### <a name="parameters"></a>Parametry

*Dysku*<br/>
Liczba całkowita od 1 do 26, która określa bieżący dysk roboczy (1 =A, 2=B i tak dalej).

## <a name="return-value"></a>Wartość zwracana

Zero (0), jeśli bieżący dysk roboczy został pomyślnie zmieniony; w przeciwnym razie -1.

## <a name="remarks"></a>Uwagi

Jeśli *dysk* nie znajduje się w zakresie od 1 do 26, program obsługi nieprawidłowego parametru jest wywoływany zgodnie z opisem w [weryfikacji parametrów](../../c-runtime-library/parameter-validation.md). Jeśli wykonanie jest dozwolone, funkcja **_chdrive** zwraca wartość -1, **errno** jest ustawiona na **EACCES,** a **_doserrno** jest ustawiona **na ERROR_INVALID_DRIVE**.

Funkcja **_chdrive** nie jest bezpieczna dla wątków, ponieważ zależy od funkcji **SetCurrentDirectory,** która sama w sobie nie jest bezpieczna dla wątków. Aby bezpiecznie używać **_chdrive** w aplikacji wielowątkowej, należy podać własną synchronizację wątków. Aby uzyskać więcej informacji, zobacz [SetCurrentDirectory](/windows/win32/api/winbase/nf-winbase-setcurrentdirectory).

Funkcja **_chdrive** zmienia tylko bieżący dysk roboczy;  **_chdir** zmienia bieżący katalog roboczy.

Domyślnie stan globalny tej funkcji jest ograniczony do aplikacji. Aby to zmienić, zobacz [Stan globalny w crt](../global-state.md).

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|
|-------------|---------------------|
|**_chdrive**|\<direct.h>|

Aby uzyskać więcej informacji, zobacz [Zgodność](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Przykład

Zobacz przykład [_getdrive](getdrive.md).

## <a name="see-also"></a>Zobacz też

[Kontrola katalogu](../../c-runtime-library/directory-control.md)<br/>
[_chdir, _wchdir](chdir-wchdir.md)<br/>
[_fullpath, _wfullpath](fullpath-wfullpath.md)<br/>
[_getcwd, _wgetcwd](getcwd-wgetcwd.md)<br/>
[_getdrive](getdrive.md)<br/>
[_mkdir, _wmkdir](mkdir-wmkdir.md)<br/>
[_rmdir, _wrmdir](rmdir-wrmdir.md)<br/>
[system, _wsystem](system-wsystem.md)<br/>
