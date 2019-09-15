---
title: _getcwd, _wgetcwd
ms.date: 11/04/2016
api_name:
- _wgetcwd
- _getcwd
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
- api-ms-win-crt-environment-l1-1-0.dll
- api-ms-win-crt-stdio-l1-1-0.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- _getcwd
- wgetcwd
- _wgetcwd
- tgetcwd
- _tgetcwd
helpviewer_keywords:
- getcwd function
- working directory
- _wgetcwd function
- _getcwd function
- current working directory
- wgetcwd function
- directories [C++], current working
ms.assetid: 888dc8c6-5595-4071-be55-816b38e3e739
ms.openlocfilehash: 78b02871aafca85db50df2eea74a2210c578c204
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/12/2019
ms.locfileid: "70955247"
---
# <a name="_getcwd-_wgetcwd"></a>_getcwd, _wgetcwd

Pobiera bieżący katalog roboczy.

## <a name="syntax"></a>Składnia

```C
char *_getcwd(
   char *buffer,
   int maxlen
);
wchar_t *_wgetcwd(
   wchar_t *buffer,
   int maxlen
);
```

### <a name="parameters"></a>Parametry

*buffer*<br/>
Lokalizacja przechowywania dla ścieżki.

*maxlen*<br/>
Maksymalna długość ścieżki w znakach: **char** dla **_getcwd** i **wchar_t** dla **_wgetcwd**.

## <a name="return-value"></a>Wartość zwracana

Zwraca wskaźnik do *buforu*. Wartość zwracana **null** wskazuje na błąd, a **errno** jest ustawiona na **ENOMEM**, co oznacza, że za mało pamięci do przydzielenia bajtów *MaxLen* (gdy argument o **wartości null** jest podawany jako *bufor*) lub do **ERANGE** , co oznacza, że ścieżka jest dłuższa niż *MaxLen* znaków. Jeśli *MaxLen* jest mniejsza lub równa zero, ta funkcja wywołuje procedurę obsługi nieprawidłowego parametru, zgodnie z opisem w [walidacji parametru](../../c-runtime-library/parameter-validation.md).

Aby uzyskać więcej informacji na temat tych i innych kodów powrotnych, zobacz [_doserrno, errno, _sys_errlist i _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

## <a name="remarks"></a>Uwagi

Funkcja **_getcwd** pobiera pełną ścieżkę bieżącego katalogu roboczego dla dysku domyślnego i zapisuje ją w *buforze*. Argument Integer *MaxLen* określa maksymalną długość ścieżki. Błąd występuje, jeśli długość ścieżki (w tym kończący znak null) przekracza *MaxLen*. Argument *buforu* może mieć **wartość null**; bufor o rozmiarze co najmniej *MaxLen* (tylko w razie potrzeby) jest automatycznie przypisywany przy użyciu opcji **malloc**do przechowywania ścieżki. Bufor ten może zostać później zwolniony przez wywołanie funkcji **Free** i przekazanie jej do **_getcwd** wartości zwracanej (wskaźnik do przydzielonego buforu).

**_getcwd** zwraca ciąg, który reprezentuje ścieżkę bieżącego katalogu roboczego. Jeśli bieżący katalog roboczy jest katalogiem głównym, ciąg kończący się ukośnikiem odwrotnym **\\** (). Jeśli bieżący katalog roboczy jest katalogiem innym niż katalog główny, ciąg kończący się nazwą katalogu, a nie ukośnikiem odwrotnym.

**_wgetcwd** to dwubajtowa wersja **_getcwd**; argument *buforu* i wartość zwracana przez **_wgetcwd** są ciągami znaków dwubajtowych. **_wgetcwd** i **_getcwd** zachowują się identycznie w inny sposób.

Jeśli **_DEBUG** i **_CRTDBG_MAP_ALLOC** są zdefiniowane, wywołania do **_getcwd** i **_wgetcwd** są zastępowane przez wywołania **_getcwd_dbg** i **_wgetcwd_dbg** , aby umożliwić debugowanie alokacji pamięci. Aby uzyskać więcej informacji, zobacz [_getcwd_dbg, _wgetcwd_dbg](getcwd-dbg-wgetcwd-dbg.md).

### <a name="generic-text-routine-mappings"></a>Mapowania procedur zwykłego tekstu

|Procedura tchar.h|_UNICODE i _MBCS niezdefiniowane|_MBCS zdefiniowano|_UNICODE zdefiniowano|
|---------------------|--------------------------------------|--------------------|-----------------------|
|**_tgetcwd**|**_getcwd**|**_getcwd**|**_wgetcwd**|

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|
|-------------|---------------------|
|**_getcwd**|\<direct.h>|
|**_wgetcwd**|\<Direct. h > lub \<WCHAR. h >|

Aby uzyskać więcej informacji o zgodności, zobacz [zgodność](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Przykład

```C
// crt_getcwd.c
// This program places the name of the current directory in the
// buffer array, then displays the name of the current directory
// on the screen. Passing NULL as the buffer forces getcwd to allocate
// memory for the path, which allows the code to support file paths
// longer than _MAX_PATH, which are supported by NTFS.

#include <direct.h>
#include <stdlib.h>
#include <stdio.h>

int main( void )
{
   char* buffer;

   // Get the current working directory:
   if( (buffer = _getcwd( NULL, 0 )) == NULL )
      perror( "_getcwd error" );
   else
   {
      printf( "%s \nLength: %d\n", buffer, strnlen(buffer) );
      free(buffer);
   }
}
```

```Output
C:\Code
```

## <a name="see-also"></a>Zobacz także

[Kontrola katalogu](../../c-runtime-library/directory-control.md)<br/>
[_chdir, _wchdir](chdir-wchdir.md)<br/>
[_mkdir, _wmkdir](mkdir-wmkdir.md)<br/>
[_rmdir, _wrmdir](rmdir-wrmdir.md)<br/>
