---
title: _rmdir —, _wrmdir — | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
apiname:
- _wrmdir
- _rmdir
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
- trmdir
- _trmdir
- wrmdir
- _rmdir
- _wrmdir
dev_langs:
- C++
helpviewer_keywords:
- _rmdir function
- directories [C++], deleting
- rmdir function
- directories [C++], removing
- trmdir function
- _trmdir function
- _wrmdir function
- wrmdir function
ms.assetid: 652c2a5a-b0ac-4493-864e-1edf484333c5
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 11e6521060932bd1273b6a3888332ac2c8b2bb7b
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
ms.locfileid: "32406992"
---
# <a name="rmdir-wrmdir"></a>_rmdir, _wrmdir

Usuwa katalog.

## <a name="syntax"></a>Składnia

```C
int _rmdir(
   const char *dirname
);
int _wrmdir(
   const wchar_t *dirname
);
```

### <a name="parameters"></a>Parametry

*DirName*<br/>
Ścieżka katalogu, który ma zostać usunięty.

## <a name="return-value"></a>Wartość zwracana

Każda z tych funkcji zwraca wartość 0, jeśli katalog zostanie pomyślnie usunięty. Zwracana wartość -1 oznacza błąd i **errno** ustawiono na jedną z następujących wartości:

|errno wartość|Warunek|
|-|-|
**ENOTEMPTY**|Podana ścieżka nie jest katalogiem, katalog nie jest pusty lub katalog jest bieżący katalog roboczy lub katalogu głównego.
**ENOENT —**|Ścieżka jest nieprawidłowa.
**EACCES**|Program ma otwarte dojście do katalogu.

Aby uzyskać więcej informacji na temat tych i innych kody powrotu, zobacz [_doserrno —, errno, _sys_errlist — i _sys_nerr —](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

## <a name="remarks"></a>Uwagi

**_Rmdir —** funkcja usuwa katalogu określonego przez *dirname*. Katalog może być pusta i nie może być bieżący katalog roboczy lub katalogu głównego.

**_wrmdir —** jest wersja znaków dwubajtowych **_rmdir —**; *dirname* argument **_wrmdir —** jest ciągiem znaków dwubajtowych. **_wrmdir —** i **_rmdir —** zachowują się tak samo w przeciwnym razie wartość.

### <a name="generic-text-routine-mappings"></a>Mapowania procedur zwykłego tekstu

|Procedura tchar.h|_UNICODE i _MBCS niezdefiniowane|_MBCS zdefiniowano|_UNICODE zdefiniowano|
|---------------------|--------------------------------------|--------------------|-----------------------|
|**_trmdir —**|**_rmdir**|**_rmdir**|**_wrmdir**|

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|
|-------------|---------------------|
|**_rmdir**|\<direct.h>|
|**_wrmdir**|\<Direct.h > lub \<wchar.h >|

Aby uzyskać więcej informacji o zgodności, zobacz [zgodności](../../c-runtime-library/compatibility.md).

## <a name="libraries"></a>Biblioteki

Wszystkie wersje [biblioteki wykonawcze języka C](../../c-runtime-library/crt-library-features.md).

## <a name="example"></a>Przykład

Zobacz przykład [_mkdir —](mkdir-wmkdir.md).

## <a name="see-also"></a>Zobacz także

[Kontrola katalogu](../../c-runtime-library/directory-control.md)<br/>
[_chdir, _wchdir](chdir-wchdir.md)<br/>
[_mkdir, _wmkdir](mkdir-wmkdir.md)<br/>
