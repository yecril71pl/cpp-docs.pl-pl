---
title: _setmode
ms.date: 11/04/2016
apiname:
- _setmode
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
- api-ms-win-crt-stdio-l1-1-0.dll
apitype: DLLExport
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
ms.openlocfilehash: 887936299dce0a13738f9dd891a168785d17c979
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50617441"
---
# <a name="setmode"></a>_setmode

Ustawia tryb tłumaczenia pliku.

## <a name="syntax"></a>Składnia

```C
int _setmode (
   int fd,
   int mode
);
```

### <a name="parameters"></a>Parametry

*FD*<br/>
Deskryptor pliku.

*Tryb*<br/>
Nowy tryb translacji.

## <a name="return-value"></a>Wartość zwracana

Jeśli to się powiedzie, zwraca poprzedniego tryb translacji.

Jeśli nieprawidłowe parametry są przekazywane do tej funkcji, parametr nieprawidłowy program obsługi zostanie wywołana, zgodnie z opisem w [Parameter Validation](../../c-runtime-library/parameter-validation.md). Jeśli wykonanie może być kontynuowane, ta funkcja zwraca wartość -1 i ustawia **errno** do jednej **EBADF**, co oznacza nieprawidłowego deskryptora pliku, lub **EINVAL**, który wskazuje nieprawidłową *tryb* argumentu.

Aby uzyskać więcej informacji na temat tych i innych kodach powrotnych, zobacz [_doserrno, errno, _sys_errlist i _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

## <a name="remarks"></a>Uwagi

**_Setmode —** funkcja ustawia *tryb* tryb translacji pliku przez *fd*. Przekazywanie **_O_TEXT** jako *tryb* ustawia tekst (tłumaczonym) trybu. Kombinacji (CR-LF) kanału informacyjnego wiersza powrotu karetki są tłumaczone na jednym wierszu znaku wysuwu na dane wejściowe. Znaki kanału informacyjnego wiersza są tłumaczone na kombinacje CR-LF w danych wyjściowych. Przekazywanie **_O_BINARY** ustawia binarnym (nieprzetłumaczonym) tryb, w którym te tłumaczenia są pomijane.

Można również przekazać **_O_U16TEXT**, **_O_U8TEXT**, lub **_O_WTEXT** Aby włączyć tryb Unicode, jak pokazano w drugim przykładzie w dalszej części tego dokumentu. **_setmode —** jest zwykle używane do modyfikowania domyślny tryb translacji **stdin** i **stdout**, ale służy dowolny plik. Jeśli zastosujesz **_setmode —** deskryptor pliku dla strumienia, wywołać **_setmode —** przed wykonaniem jakiejkolwiek operacji na strumieniu danych wejściowych lub wyjściowych.

> [!CAUTION]
> Jeśli piszesz danych w strumieniu plików jawnie opróżnić kodu za pomocą [fflush —](fflush.md) przed użyciem **_setmode —** Aby zmienić tryb. Jeśli kod nie jest opróżnienia, możesz otrzymać nieoczekiwane zachowanie. W przypadku niezapisania danych w strumieniu ma opróżniania kodu.

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|Opcjonalne nagłówki|
|-------------|---------------------|----------------------|
|**_setmode**|\<io.h>|\<fcntl.h>|

Aby uzyskać więcej informacji na temat zgodności, zobacz [zgodności](../../c-runtime-library/compatibility.md).

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
