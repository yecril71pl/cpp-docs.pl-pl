---
title: _chdrive — | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
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
dev_langs:
- C++
helpviewer_keywords:
- drives, changing
- _chdrive function
- chdrive function
ms.assetid: 212a1a4b-4fa8-444e-9677-7fca4c8c47e3
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 8f95169f62fa2eaf9c562bff463ad84c0827db9a
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
ms.locfileid: "32394425"
---
# <a name="chdrive"></a>_chdrive

Zmienia bieżący stacji roboczych.

> [!IMPORTANT]
> Nie można używać tego interfejsu API w aplikacjach, które są wykonywane w środowisku wykonawczym systemu Windows. Aby uzyskać więcej informacji, zobacz [funkcje CRT, nie są obsługiwane w aplikacjach platformy uniwersalnej systemu Windows](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md).

## <a name="syntax"></a>Składnia

```C
int _chdrive(
   int drive
);
```

### <a name="parameters"></a>Parametry

*Dysk*<br/>
Liczba całkowita od 1 do 26, który określa bieżący roboczy dysku (1 = A, 2 = B i tak dalej).

## <a name="return-value"></a>Wartość zwracana

Wartość zero (0), jeśli pomyślnie; zmieniono bieżącej stacji roboczych w przeciwnym razie wartość -1.

## <a name="remarks"></a>Uwagi

Jeśli *dysku* jest nie jest w zakresie od 1 do 26 obsługi nieprawidłowy parametr jest wywoływany, zgodnie z opisem w [sprawdzanie poprawności parametru](../../c-runtime-library/parameter-validation.md). Jeśli jest dozwolone wykonywanie, aby kontynuować, **_chdrive —** funkcja zwraca wartość -1, **errno** ustawiono **eacces —**, i **_doserrno —** ma ustawioną wartość  **ERROR_INVALID_DRIVE**.

**_Chdrive —** funkcja nie jest bezpieczne wątkowo, ponieważ zależy on od **SetCurrentDirectory** funkcji, która jest elementem nie wątkowo. Aby użyć **_chdrive —** bezpiecznie w aplikacji wielowątkowej, musisz podać własne synchronizacja wątku. Aby uzyskać więcej informacji, przejdź do [biblioteki MSDN Library](http://go.microsoft.com/fwlink/p/?linkid=150542) , a następnie wyszukaj **SetCurrentDirectory**.

**_Chdrive —** funkcja zmienia tylko bieżący pracy dysk;  **_chdir —** zmienia bieżący katalog roboczy.

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
