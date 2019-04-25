---
title: _getcwd, _wgetcwd
ms.date: 11/04/2016
apiname:
- _wgetcwd
- _getcwd
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
- api-ms-win-crt-environment-l1-1-0.dll
- api-ms-win-crt-stdio-l1-1-0.dll
apitype: DLLExport
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
ms.openlocfilehash: 4c533f0e716cb9a13c152b9be3c46f60291118d9
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62331795"
---
# <a name="getcwd-wgetcwd"></a>_getcwd, _wgetcwd

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
Maksymalna długość ścieżki w znakach: **char** dla **_getcwd —** i **wchar_t** dla **_wgetcwd —**.

## <a name="return-value"></a>Wartość zwracana

Zwraca wskaźnik do *buforu*. A **NULL** zwracana wartość wskazuje błąd, i **errno** ustawiono opcję **ENOMEM**, wskazujący, że jest za mało pamięci do przydzielenia *maxlen* bajtów (gdy **o wartości NULL** argument jest podawana jako *buforu*), lub **ERANGE**, wskazującą, czy ścieżka jest dłuższa niż *maxlen*  znaków. Jeśli *maxlen* jest mniejszy niż lub równy zero, funkcja wywoła nieprawidłowego parametru, zgodnie z opisem w [Parameter Validation](../../c-runtime-library/parameter-validation.md).

Aby uzyskać więcej informacji na temat tych i innych kodach powrotnych, zobacz [_doserrno, errno, _sys_errlist i _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

## <a name="remarks"></a>Uwagi

**_Getcwd —** funkcja pobiera pełną ścieżkę bieżącego katalogu roboczego na domyślnym dysku i zapisuje go w *buforu*. Argument liczby całkowitej *maxlen* określa maksymalną długość ścieżki. Błąd występuje, jeśli długość ścieżki (w tym kończącego znaku null) przekracza *maxlen*. *Buforu* argument może być **NULL**; bufor o rozmiarze co najmniej *maxlen* (więcej tylko wtedy, gdy jest to konieczne) jest przydzielany automatycznie, przy użyciu **— funkcja malloc**w celu przechowywania ścieżki. Ten bufor później może zostać uwolniony przez wywołanie metody **bezpłatne** i przekazanie do niej **_getcwd —** zwracają wartość (wskaźnik do przydzielonego buforu).

**_getcwd —** zwraca ciąg, który reprezentuje ścieżkę bieżącego katalogu roboczego. Jeśli bieżący katalog roboczy jest katalog główny, ciąg kończy się znakiem kreski ułamkowej odwróconej ( **\\** ). Jeśli bieżący katalog roboczy na katalog inny niż katalog główny, ciąg kończy się nazwą katalogu, a nie znakiem kreski ułamkowej odwróconej.

**_wgetcwd —** to wersja znaku dwubajtowego **_getcwd —**; *buforu* argument i wartość zwracana przez **_wgetcwd —** są ciągami znaków dwubajtowych. **_wgetcwd —** i **_getcwd —** zachowują się identycznie.

Gdy **_DEBUG** i **_CRTDBG_MAP_ALLOC** są zdefiniowane, wzywa do **_getcwd —** i **_wgetcwd —** są zastępowane przez wywołania **_ getcwd_dbg —** i **_wgetcwd_dbg —** aby umożliwić debugowanie alokacji pamięci. Aby uzyskać więcej informacji, zobacz [_getcwd_dbg —, _wgetcwd_dbg —](getcwd-dbg-wgetcwd-dbg.md).

### <a name="generic-text-routine-mappings"></a>Mapowania procedur zwykłego tekstu

|Procedura tchar.h|_UNICODE i _MBCS niezdefiniowane|_MBCS zdefiniowano|_UNICODE zdefiniowano|
|---------------------|--------------------------------------|--------------------|-----------------------|
|**_tgetcwd**|**_getcwd**|**_getcwd**|**_wgetcwd**|

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|
|-------------|---------------------|
|**_getcwd**|\<direct.h>|
|**_wgetcwd**|\<Direct.h > lub \<wchar.h >|

Aby uzyskać więcej informacji na temat zgodności, zobacz [zgodności](../../c-runtime-library/compatibility.md).

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
