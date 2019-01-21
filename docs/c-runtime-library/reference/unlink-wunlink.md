---
title: _unlink, _wunlink
ms.date: 11/04/2016
apiname:
- _unlink
- _wunlink
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
- _tunlink
- _unlink
- wunlink
- _wunlink
helpviewer_keywords:
- files [C++], deleting
- _wunlink function
- wunlink function
- unlink function
- _unlink function
- tunlink function
- files [C++], removing
- _tunlink function
ms.assetid: 5e4f5f1b-1e99-4391-9b18-9ac63c32fae8
ms.openlocfilehash: ec59a02f1302fe4a2149889cf1b48090d061d6b2
ms.sourcegitcommit: 22f7c4a9b4fc2158fb5283810f15275803cafe10
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/21/2019
ms.locfileid: "54417619"
---
# <a name="unlink-wunlink"></a>_unlink, _wunlink

Usuwanie pliku.

## <a name="syntax"></a>Składnia

```C
int _unlink(
   const char *filename
);
int _wunlink(
   const wchar_t *filename
);
```

### <a name="parameters"></a>Parametry

*Nazwa pliku*<br/>
Nazwa pliku do usunięcia.

## <a name="return-value"></a>Wartość zwracana

Każda z tych funkcji zwraca wartość 0, jeśli kończy się pomyślnie. W przeciwnym razie funkcja zwraca wartość -1 i ustawia **errno** do **EACCES**, co oznacza, że ścieżka określa tylko do odczytu pliku lub katalogu, lub **ENOENT**, co oznacza plik lub ścieżka Nie można odnaleźć.

Zobacz [_doserrno, errno, _sys_errlist i _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md) kody powrotne — Aby uzyskać więcej informacji na temat tych i innych.

## <a name="remarks"></a>Uwagi

**_Unlink —** funkcja usuwa plik określony przez *filename*. **_wunlink —** to wersja znaku dwubajtowego **_unlink —**; *filename* argument **_wunlink —** jest ciągiem znaku dwubajtowego. Funkcje te zachowują się identycznie.

### <a name="generic-text-routine-mappings"></a>Mapowania procedur zwykłego tekstu

|Procedura TCHAR.H|_UNICODE & _MBCS nie zdefiniowano|_MBCS zdefiniowano|_UNICODE zdefiniowano|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_tunlink**|**_unlink**|**_unlink**|**_wunlink**|

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|
|-------------|---------------------|
|**_unlink**|\<IO.h > i \<stdio.h >|
|**_wunlink**|\<IO.h > lub \<wchar.h >|

Aby uzyskać dodatkowe informacje o zgodności, zobacz [zgodności](../../c-runtime-library/compatibility.md).

## <a name="code-example"></a>Przykład kodu

_Unlink — jest używane do usuwania CRT_UNLINK. TXT.

```C
// crt_unlink.c

#include <stdio.h>

int main( void )
{
   if( _unlink( "crt_unlink.txt" ) == -1 )
      perror( "Could not delete 'CRT_UNLINK.TXT'" );
   else
      printf( "Deleted 'CRT_UNLINK.TXT'\n" );
}
```

### <a name="input-crtunlinktxt"></a>Input: crt_unlink.txt

```Input
This file will be deleted.
```

### <a name="sample-output"></a>Przykładowe dane wyjściowe

```Output
Deleted 'CRT_UNLINK.TXT'
```

## <a name="see-also"></a>Zobacz także

[Obsługa plików](../../c-runtime-library/file-handling.md)<br/>
[_close](close.md)<br/>
[remove, _wremove](remove-wremove.md)<br/>
