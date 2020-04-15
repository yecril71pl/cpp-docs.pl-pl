---
title: _setmode
ms.date: 4/2/2020
api_name:
- _setmode
- _o__setmode
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
- api-ms-win-crt-private-l1-1-0
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
ms.openlocfilehash: 36d2130d4039f1f87f7f54fc26ad02cb8d519b4a
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81353833"
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

*Fd*<br/>
Deskryptor pliku.

*Tryb*<br/>
Nowy tryb tłumaczenia.

## <a name="return-value"></a>Wartość zwracana

Jeśli się powiedzie, zwraca poprzedni tryb tłumaczenia.

Jeśli nieprawidłowe parametry są przekazywane do tej funkcji, wywoływany jest program obsługi nieprawidłowego parametru, zgodnie z opisem w [obszarze Sprawdzanie poprawności parametrów.](../../c-runtime-library/parameter-validation.md) Jeśli wykonanie jest dozwolone, ta funkcja zwraca wartość -1 i ustawia **errno** na **EBADF**, który wskazuje nieprawidłowy deskryptor pliku lub **EINVAL**, który wskazuje nieprawidłowy argument *trybu.*

Aby uzyskać więcej informacji na temat tych i innych kodów zwrotnych, zobacz [_doserrno, errno, _sys_errlist i _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

## <a name="remarks"></a>Uwagi

Funkcja **_setmode** ustawia *tryb* tłumaczenia pliku podanego przez *fd*. Przekazywanie **_O_TEXT** jako *tryb* ustawia tekst (czyli przetłumaczony) tryb. Kombinacje kanału informacyjnego wiersza powrotu karetki (CR-LF) są tłumaczone na pojedynczy znak posuwu wiersza na danych wejściowych. Znaki wysuwu wiersza są tłumaczone na kombinacje CR-LF na wyjściu. Przekazywanie **_O_BINARY** ustawia tryb binarny (nieprzetłumaczony), w którym te tłumaczenia są pomijane.

Można również przekazać **_O_U16TEXT** **, _O_U8TEXT**lub **_O_WTEXT,** aby włączyć tryb Unicode, jak pokazano w drugim przykładzie w dalszej części tego dokumentu.

> [!CAUTION]
> Tryb Unicode jest przeznaczony dla funkcji `wprintf`szerokiego drukowania (na przykład) i nie jest obsługiwany w przypadku funkcji drukowania wąskego. Użycie funkcji drukowania wąskego w strumieniu trybu Unicode wyzwala potwierdzenia.

**_setmode** jest zwykle używany do modyfikowania domyślnego trybu tłumaczenia **stdin** i **stdout**, ale można go używać w dowolnym pliku. Jeśli **zastosujesz _setmode** do deskryptora pliku dla strumienia, wywołaj **_setmode** przed wykonaniem jakichkolwiek operacji wejściowych lub wyjściowych w strumieniu.

> [!CAUTION]
> Jeśli piszesz dane do strumienia plików, jawnie opróżnić kod za pomocą [fflush](fflush.md) przed użyciem **_setmode,** aby zmienić tryb. Jeśli nie opróżnić kod, może pojawić się nieoczekiwane zachowanie. Jeśli nie zostały zapisane dane do strumienia, nie trzeba opróżniać kod.

Domyślnie stan globalny tej funkcji jest ograniczony do aplikacji. Aby to zmienić, zobacz [Stan globalny w crt](../global-state.md).

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|Opcjonalne nagłówki|
|-------------|---------------------|----------------------|
|**_setmode**|\<> io.h|\<fcntl.h>|

Aby uzyskać więcej informacji o zgodności, zobacz [Zgodność](../../c-runtime-library/compatibility.md).

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

## <a name="see-also"></a>Zobacz też

[Obsługa plików](../../c-runtime-library/file-handling.md)<br/>
[_creat, _wcreat](creat-wcreat.md)<br/>
[fopen, _wfopen](fopen-wfopen.md)<br/>
[_open, _wopen](open-wopen.md)<br/>
[_set_fmode](set-fmode.md)<br/>
