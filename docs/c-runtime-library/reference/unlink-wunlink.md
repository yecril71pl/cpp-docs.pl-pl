---
title: _unlink, _wunlink
ms.date: 4/2/2020
api_name:
- _unlink
- _wunlink
- _o__unlink
- _o__wunlink
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
ms.openlocfilehash: ffc1a64c60d41246773d5e262523000355b0de3b
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81361263"
---
# <a name="_unlink-_wunlink"></a>_unlink, _wunlink

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

*Pod nazwą*<br/>
Nazwa pliku do usunięcia.

## <a name="return-value"></a>Wartość zwracana

Każda z tych funkcji zwraca wartość 0, jeśli zakończy się pomyślnie. W przeciwnym razie funkcja zwraca wartość -1 i ustawia **errno** na **EACCES**, co oznacza, że ścieżka określa plik tylko do odczytu lub katalog lub **enoent**, co oznacza, że plik lub ścieżka nie zostanie znaleziona.

Zobacz [_doserrno, errno, _sys_errlist i _sys_nerr,](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md) aby uzyskać więcej informacji na temat tych i innych kodów zwrotnych.

## <a name="remarks"></a>Uwagi

Funkcja **_unlink** usuwa plik określony przez *nazwę pliku*. **_wunlink** jest szerokoznakową wersją **_unlink**; *argumentnazyt,* który **ma _wunlink** jest ciągiem znaków o szerokim charakterze. Te funkcje zachowują się identycznie w przeciwnym razie.

Domyślnie stan globalny tej funkcji jest ograniczony do aplikacji. Aby to zmienić, zobacz [Stan globalny w crt](../global-state.md).

### <a name="generic-text-routine-mappings"></a>Mapowania procedur zwykłego tekstu

|Procedura TCHAR.H|_UNICODE nie zdefiniowano & _MBCS|_MBCS zdefiniowano|_UNICODE zdefiniowano|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_tunlink**|**_unlink**|**_unlink**|**_wunlink**|

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|
|-------------|---------------------|
|**_unlink**|\<io.h> i \<stdio.h>|
|**_wunlink**|\<io.h> lub \<wchar.h>|

Aby uzyskać dodatkowe informacje o zgodności, zobacz [Zgodność](../../c-runtime-library/compatibility.md).

## <a name="code-example"></a>Przykład kodu

Ten program używa _unlink do usuwania CRT_UNLINK. Txt.

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

### <a name="input-crt_unlinktxt"></a>Dane wejściowe: crt_unlink.txt

```Input
This file will be deleted.
```

### <a name="sample-output"></a>Przykładowe dane wyjściowe

```Output
Deleted 'CRT_UNLINK.TXT'
```

## <a name="see-also"></a>Zobacz też

[Obsługa plików](../../c-runtime-library/file-handling.md)<br/>
[_close](close.md)<br/>
[remove, _wremove](remove-wremove.md)<br/>
