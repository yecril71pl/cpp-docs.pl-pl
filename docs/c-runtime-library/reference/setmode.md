---
title: _setmode
ms.date: 11/04/2016
api_name:
- _setmode
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
- api-ms-win-crt-stdio-l1-1-0.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- _setmode
helpviewer_keywords:
- Unicode [C++], console output
- files [C++], modes
- _setmode function
- file translation [C++], setting mode
- files [C++], translation
- setmode function
ms.assetid: 996ff7cb-11d1-43f4-9810-f6097182642a
ms.openlocfilehash: 7f14cc9451b93a9077916b8c650645990ba654a3
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/12/2019
ms.locfileid: "70948594"
---
# <a name="_setmode"></a>_setmode

Ustawia tryb tłumaczenia plików.

## <a name="syntax"></a>Składnia

```C
int _setmode (
   int fd,
   int mode
);
```

### <a name="parameters"></a>Parametry

*proces*<br/>
Deskryptor pliku.

*wyst*<br/>
Nowy tryb tłumaczenia.

## <a name="return-value"></a>Wartość zwracana

Jeśli to się powiedzie, zwraca poprzedni tryb tłumaczenia.

Jeśli do tej funkcji są przesyłane nieprawidłowe parametry, procedura obsługi nieprawidłowego parametru jest wywoływana, zgodnie z opisem w [walidacji parametru](../../c-runtime-library/parameter-validation.md). Jeśli wykonanie może być kontynuowane, funkcja zwraca wartość-1 i ustawia **errno** na **EBADF**, która wskazuje nieprawidłowy deskryptor pliku lub **EINVAL**, który wskazuje nieprawidłowy argument *trybu* .

Aby uzyskać więcej informacji na temat tych i innych kodów powrotnych, zobacz [_doserrno, errno, _sys_errlist i _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

## <a name="remarks"></a>Uwagi

Funkcja **_setmode** ustawia tryb translacji pliku *, który jest* określony przez *FD*. Przekazanie trybu **_O_TEXT** jako *tryb* tekstu (który jest tłumaczony). Kombinacje powrotu karetki liniowej (CR-LF) są tłumaczone na pojedynczy znak wysuwu wiersza na wejściu. Znaki wysuwu wiersza są tłumaczone na kombinacje CR-LF w danych wyjściowych. Przekazywanie zestawów **_O_BINARY** ustawia binarny (nieprzetłumaczony) tryb, w którym te tłumaczenia są pomijane.

Możesz również przekazać **_O_U16TEXT**, **_O_U8TEXT**lub **_O_WTEXT** , aby włączyć tryb Unicode, jak pokazano w drugim przykładzie w dalszej części tego dokumentu.

> [!CAUTION]
> Tryb Unicode jest przeznaczony dla szerokiej funkcji drukowania (na `wprintf`przykład) i nie jest obsługiwany w przypadku wąskich funkcji drukowania. Użycie wąskiej funkcji drukowania w strumieniu trybu Unicode wyzwala potwierdzenie.

**_setmode** jest zwykle używany do modyfikacji domyślnego trybu translacji **stdin** i **stdout**, ale można go użyć w dowolnym pliku. Jeśli zastosujesz **_setmode** do deskryptora pliku dla strumienia, wywołaj **_setmode** przed wykonaniem jakichkolwiek operacji wejścia lub wyjścia strumienia.

> [!CAUTION]
> Jeśli zapisujesz dane do strumienia plików, jawnie Opróżniaj kod przy użyciu [fflush](fflush.md) przed użyciem **_setmode** do zmiany trybu. Jeśli kod nie zostanie opróżniony, może wystąpić nieoczekiwane zachowanie. Jeśli nie zapisano danych do strumienia, nie ma potrzeby opróżniania kodu.

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|Opcjonalne nagłówki|
|-------------|---------------------|----------------------|
|**_setmode**|\<io.h>|\<fcntl.h>|

Aby uzyskać więcej informacji o zgodności, zobacz [zgodność](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Przykład

```C
// crt_setmode.c
// This program uses _setmode to change
// stdin from text mode to binary mode.

#include <stdio.h>
#include <fcntl.h>
#include <io.h>

int main( void )
{
   int result;

   // Set "stdin" to have binary mode:
   result = _setmode( _fileno( stdin ), _O_BINARY );
   if( result == -1 )
      perror( "Cannot set mode" );
   else
      printf( "'stdin' successfully changed to binary mode\n" );
}
```

```Output
'stdin' successfully changed to binary mode
```

## <a name="example"></a>Przykład

```C
// crt_setmodeunicode.c
// This program uses _setmode to change
// stdout to Unicode. Cyrillic and Ideographic
// characters will appear on the console (if
// your console font supports those character sets).

#include <fcntl.h>
#include <io.h>
#include <stdio.h>

int main(void) {
    _setmode(_fileno(stdout), _O_U16TEXT);
    wprintf(L"\x043a\x043e\x0448\x043a\x0430 \x65e5\x672c\x56fd\n");
    return 0;
}
```

## <a name="see-also"></a>Zobacz także

[Obsługa plików](../../c-runtime-library/file-handling.md)<br/>
[_creat, _wcreat](creat-wcreat.md)<br/>
[fopen, _wfopen](fopen-wfopen.md)<br/>
[_open, _wopen](open-wopen.md)<br/>
[_set_fmode](set-fmode.md)<br/>
