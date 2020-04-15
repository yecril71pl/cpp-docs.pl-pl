---
title: _getcwd, _wgetcwd
description: C Funkcje biblioteki wykonawczej _getcwd, _wgetcwd uzyskać bieżący katalog roboczy.
ms.date: 4/2/2020
api_name:
- _wgetcwd
- _getcwd
- _o__getcwd
- _o__wgetcwd
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
- api-ms-win-crt-private-l1-1-0
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
ms.openlocfilehash: bc19a416ebebeb901e8dbb435971e6d5f33e4067
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81344434"
---
# <a name="_getcwd-_wgetcwd"></a>_getcwd, _wgetcwd

Pobiera bieżącego katalogu roboczego.

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

*Buforu*\
Lokalizacja przechowywania ścieżki.

*maxlen ( maxlen )*\
Maksymalna długość ścieżki w znakach: **char** dla **_getcwd** i **wchar_t** dla **_wgetcwd**.

## <a name="return-value"></a>Wartość zwracana

Zwraca wskaźnik do *buforu*. Wartość **zwracana NULL** wskazuje błąd, a **errno** jest ustawiane na **ENOMEM,** co oznacza, że nie ma wystarczającej ilości pamięci do przydzielenia bajtów *maxlen* (gdy argument **NULL** jest podany jako *bufor)* lub **ERANGE**, co wskazuje, że ścieżka jest dłuższa niż znaki *maxlen.* Jeśli *maxlen* jest mniejszy lub równy zero, ta funkcja wywołuje nieprawidłowy program obsługi parametrów, zgodnie z opisem w [weryfikacji parametrów](../../c-runtime-library/parameter-validation.md).

Aby uzyskać więcej informacji na temat tych i innych kodów zwrotnych, zobacz [_doserrno, errno, _sys_errlist i _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

## <a name="remarks"></a>Uwagi

Funkcja **_getcwd** pobiera pełną ścieżkę bieżącego katalogu roboczego dla dysku domyślnego i przechowuje go w *buforze*. Argument liczby całkowitej *maxlen* określa maksymalną długość ścieżki. Błąd występuje, jeśli długość ścieżki (w tym kończący się znak null) przekracza *maxlen*. Argument *buforu* może mieć **wartość NULL**; bufor o co najmniej *rozmiarze maxlen* (więcej tylko w razie potrzeby) jest automatycznie przydzielany, używając **malloc**, do przechowywania ścieżki. Ten bufor można później zwolnić, wywołując **free** i przekazując go **_getcwd** zwracaną wartość (wskaźnik do przydzielonego buforu).

**_getcwd** zwraca ciąg reprezentujący ścieżkę bieżącego katalogu roboczego. Jeśli bieżący katalog roboczy jest katalogiem głównym, ciąg`\`kończy się ukośnikiem odwrotnym ( ). Jeśli bieżący katalog roboczy jest katalogiem innym niż katalog główny, ciąg kończy się nazwą katalogu, a nie ukośnikiem odwrotnym.

**_wgetcwd** jest szerokoznakową wersją **_getcwd**; argument *buforu* i zwracana wartość **_wgetcwd** są ciągami znaków o szerokich znakach. **_wgetcwd** i **_getcwd** zachowują się identycznie w przeciwnym razie.

Po **zdefiniowaniu _DEBUG** i **_CRTDBG_MAP_ALLOC** wywołania **_getcwd** i **_wgetcwd** są zastępowane wywołaniami **_getcwd_dbg** i **_wgetcwd_dbg,** aby umożliwić debugowanie alokacji pamięci. Aby uzyskać więcej informacji, zobacz [_getcwd_dbg _wgetcwd_dbg](getcwd-dbg-wgetcwd-dbg.md).

Domyślnie stan globalny tej funkcji jest ograniczony do aplikacji. Aby to zmienić, zobacz [Stan globalny w crt](../global-state.md).

### <a name="generic-text-routine-mappings"></a>Mapowania procedur zwykłego tekstu

|Procedura tchar.h|_UNICODE i _MBCS niezdefiniowane|_MBCS zdefiniowano|_UNICODE zdefiniowano|
|---------------------|--------------------------------------|--------------------|-----------------------|
|**_tgetcwd**|**_getcwd**|**_getcwd**|**_wgetcwd**|

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|
|-------------|---------------------|
|**_getcwd**|\<direct.h>|
|**_wgetcwd**|\<direct.h> lub \<wchar.h>|

Aby uzyskać więcej informacji o zgodności, zobacz [Zgodność](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Przykład

```C
// crt_getcwd.c
// Compile with: cl /W4 crt_getcwd.c
// This program places the name of the current directory in the
// buffer array, then displays the name of the current directory
// on the screen. Passing NULL as the buffer forces getcwd to allocate
// memory for the path, which allows the code to support file paths
// longer than _MAX_PATH, which are supported by NTFS.

#include <direct.h> // _getcwd
#include <stdlib.h> // free, perror
#include <stdio.h>  // printf
#include <string.h> // strlen

int main( void )
{
   char* buffer;

   // Get the current working directory:
   if ( (buffer = _getcwd( NULL, 0 )) == NULL )
      perror( "_getcwd error" );
   else
   {
      printf( "%s \nLength: %zu\n", buffer, strlen(buffer) );
      free(buffer);
   }
}
```

```Output
C:\Code
```

## <a name="see-also"></a>Zobacz też

[Kontrola katalogu](../../c-runtime-library/directory-control.md)\
[_chdir, _wchdir](chdir-wchdir.md)\
[_mkdir, _wmkdir](mkdir-wmkdir.md)\
[_rmdir, _wrmdir](rmdir-wrmdir.md)
