---
title: fgetc, fgetwc
ms.date: 11/04/2016
apiname:
- fgetwc
- fgetc
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
- _fgettc
- fgetwc
- fgetc
helpviewer_keywords:
- fgettc function
- characters, reading
- _fgettc function
- fgetc function
- streams, reading characters from
- reading characters from streams
- fgetwc function
ms.assetid: 13348b7b-dc86-421c-9d6c-611ca79c8338
ms.openlocfilehash: a853a46fc43106c9ea57be84b37fb46a18041ba8
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50639926"
---
# <a name="fgetc-fgetwc"></a>fgetc, fgetwc

Przeczytaj znak ze strumienia.

## <a name="syntax"></a>Składnia

```C
int fgetc(
   FILE *stream
);
wint_t fgetwc(
   FILE *stream
);
```

### <a name="parameters"></a>Parametry

*Stream*<br/>
Wskaźnik do **pliku** struktury.

## <a name="return-value"></a>Wartość zwracana

**fgetc —** zwraca znak odczytywany jako **int** lub zwraca **EOF** aby wskazać błąd lub koniec pliku. **fgetwc —** zwraca, jako [wint_t](../../c-runtime-library/standard-types.md), znak dwubajtowy, który odpowiada znakowi odczytu lub zwraca **WEOF** aby wskazać błąd lub koniec pliku. W przypadku obu tych funkcji, użyj **feof** lub **ferror** Aby rozróżnić między błędem a warunkiem końca pliku. Jeśli wystąpi błąd odczytu, zostanie ustawiony wskaźnik błędu dla strumienia. Jeśli *strumienia* jest **NULL**, **fgetc —** i **fgetwc —** wywołują nieprawidłowy parametr uchwytu, zgodnie z opisem w [parametru Sprawdzanie poprawności](../../c-runtime-library/parameter-validation.md). Jeśli wykonanie może być kontynuowane, te funkcje ustawiają **errno** do **EINVAL** i zwracają **EOF**.

## <a name="remarks"></a>Uwagi

Każda z tych funkcji odczytuje pojedynczy znak z bieżącego położenia pliku skojarzone z *strumienia*. Funkcja następnie zwiększa skojarzony wskaźnik pliku (Jeżeli zdefiniowane) aby wskazywała na następny znak. Jeśli strumień jest na końcu pliku, wskaźnik końca pliku dla strumienia jest ustawiony.

**fgetc —** jest odpowiednikiem **getc —**, ale jest realizowane tylko jako funkcja, a nie jako funkcja i makra.

**fgetwc —** jest wersją znaków dwubajtowych **fgetc —**; odczytuje **c** jako znak wielobajtowy lub znak dwubajtowy ze czy *strumienia* jest otwarty w Tryb tekstu lub w trybie binarnym.

Wersje **_nolock** sufiksem są identyczne, z tą różnicą, że nie są chronione przed ingerencją przez inne wątki.

Aby uzyskać więcej informacji na temat przetwarzania znaków dwubajtowych i znaków wielobajtowych w trybach tekstowym i binarnym, zobacz [we/wy Stream w Unicode w trybach tekstowym i binarnym](../../c-runtime-library/unicode-stream-i-o-in-text-and-binary-modes.md).

### <a name="generic-text-routine-mappings"></a>Mapowania procedur zwykłego tekstu

|Procedura TCHAR.H|_UNICODE & _MBCS nie zdefiniowano|_MBCS zdefiniowano|_UNICODE zdefiniowano|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_fgettc —**|**fgetc**|**fgetc**|**fgetwc**|

## <a name="requirements"></a>Wymagania

|Funkcja|Wymagany nagłówek|
|--------------|---------------------|
|**fgetc**|\<stdio.h>|
|**fgetwc**|\<stdio.h > lub \<wchar.h >|

Aby uzyskać dodatkowe informacje o zgodności, zobacz [zgodności](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Przykład

```C
// crt_fgetc.c
// This program uses getc to read the first
// 80 input characters (or until the end of input)
// and place them into a string named buffer.

#include <stdio.h>
#include <stdlib.h>

int main( void )
{
   FILE *stream;
   char buffer[81];
   int  i, ch;

   // Open file to read line from:
   fopen_s( &stream, "crt_fgetc.txt", "r" );
   if( stream == NULL )
      exit( 0 );

   // Read in first 80 characters and place them in "buffer":
   ch = fgetc( stream );
   for( i=0; (i < 80 ) && ( feof( stream ) == 0 ); i++ )
   {
      buffer[i] = (char)ch;
      ch = fgetc( stream );
   }

   // Add null to end string
   buffer[i] = '\0';
   printf( "%s\n", buffer );
   fclose( stream );
}
```

## <a name="input-crtfgetctxt"></a>Dane wejściowe: crt_fgetc.txt

```Input
Line one.
Line two.
```

### <a name="output"></a>Dane wyjściowe

```Output
Line one.
Line two.
```

## <a name="see-also"></a>Zobacz także

[Stream operacji We/Wy](../../c-runtime-library/stream-i-o.md)<br/>
[fputc, fputwc](fputc-fputwc.md)<br/>
[getc, getwc](getc-getwc.md)<br/>
