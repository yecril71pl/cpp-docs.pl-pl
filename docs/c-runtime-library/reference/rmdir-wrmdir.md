---
title: _rmdir, _wrmdir
ms.date: 11/04/2016
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
ms.openlocfilehash: 1169405ae2f03a1e6affe2fcc00d594912e08ae1
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50511127"
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

*nazwa_kat*<br/>
Ścieżka katalogu, który ma zostać usunięty.

## <a name="return-value"></a>Wartość zwracana

Każda z tych funkcji zwraca wartość 0, jeśli katalog został pomyślnie usunięty. Zwracana wartość-1 wskazuje błąd i **errno** jest ustawiony na jedną z następujących wartości:

|errno wartość|Warunek|
|-|-|
**ENOTEMPTY**|Podana ścieżka nie jest katalogiem, katalog nie jest pusty lub katalog jest bieżącym katalogu roboczym lub katalogu głównego.
**ENOENT**|Ścieżka jest nieprawidłowa.
**EACCES**|Program ma otwarte dojście do katalogu.

Aby uzyskać więcej informacji na temat tych i innych kodach powrotnych, zobacz [_doserrno, errno, _sys_errlist i _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

## <a name="remarks"></a>Uwagi

**_Rmdir —** funkcja usuwa katalogu określonego przez *nazwa_kat*. Katalog może być pusta i nie może być bieżącym katalogu roboczym lub katalogu głównego.

**_wrmdir —** to wersja znaku dwubajtowego **_rmdir —**; *nazwa_kat* argument **_wrmdir —** jest ciągiem znaku dwubajtowego. **_wrmdir —** i **_rmdir —** zachowują się identycznie.

### <a name="generic-text-routine-mappings"></a>Mapowania procedur zwykłego tekstu

|Procedura tchar.h|_UNICODE i _MBCS niezdefiniowane|_MBCS zdefiniowano|_UNICODE zdefiniowano|
|---------------------|--------------------------------------|--------------------|-----------------------|
|**_trmdir —**|**_rmdir**|**_rmdir**|**_wrmdir**|

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|
|-------------|---------------------|
|**_rmdir**|\<direct.h>|
|**_wrmdir**|\<Direct.h > lub \<wchar.h >|

Aby uzyskać więcej informacji na temat zgodności, zobacz [zgodności](../../c-runtime-library/compatibility.md).

## <a name="libraries"></a>Biblioteki

Wszystkie wersje [biblioteki wykonawczej C](../../c-runtime-library/crt-library-features.md).

## <a name="example"></a>Przykład

Zobacz przykład [_mkdir —](mkdir-wmkdir.md).

## <a name="see-also"></a>Zobacz także

[Kontrola katalogu](../../c-runtime-library/directory-control.md)<br/>
[_chdir, _wchdir](chdir-wchdir.md)<br/>
[_mkdir, _wmkdir](mkdir-wmkdir.md)<br/>
