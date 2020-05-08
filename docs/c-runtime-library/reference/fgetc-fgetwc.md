---
title: fgetc, fgetwc
ms.date: 4/2/2020
api_name:
- fgetwc
- fgetc
- _o_fgetc
- _o_fgetwc
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
- api-ms-win-crt-private-l1-1-0.dll
api_type:
- DLLExport
topic_type:
- apiref
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
ms.openlocfilehash: a9c064582e22e267b0c597ecd89df8a43ef0bbc4
ms.sourcegitcommit: 5a069c7360f75b7c1cf9d4550446ec2fa2eb2293
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/07/2020
ms.locfileid: "82912868"
---
# <a name="fgetc-fgetwc"></a>fgetc, fgetwc

Odczytaj znak ze strumienia.

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

*produkcyjne*<br/>
Wskaźnik do struktury **pliku** .

## <a name="return-value"></a>Wartość zwracana

**fgetc** zwraca znak odczytywany jako **int** lub zwraca **znacznik EOF** , aby wskazać błąd lub koniec pliku. **fgetwc** zwraca, jako [wint_t](../../c-runtime-library/standard-types.md), znak dwubajtowy, który odpowiada znakowi odczytu lub zwraca **WEOF** , aby wskazać błąd lub koniec pliku. Dla obu funkcji Użyj **feof** lub obiektu **odwołującego** do rozróżnienia między błędem a warunkiem końca pliku. Jeśli wystąpi błąd odczytu, zostanie ustawiony wskaźnik błędu dla strumienia. Jeśli *strumień* ma **wartość null**, **fgetc** i **fgetwc** Wywołaj procedurę obsługi nieprawidłowego parametru, zgodnie z opisem w [walidacji parametru](../../c-runtime-library/parameter-validation.md). Jeśli wykonanie może być kontynuowane, te funkcje ustawiają **errno** na **EINVAL** i zwracają **znacznik EOF**.

## <a name="remarks"></a>Uwagi

Każda z tych funkcji odczytuje pojedynczy znak z bieżącego położenia pliku skojarzonego ze *strumieniem*. Funkcja następnie zwiększa skojarzony wskaźnik pliku (jeśli jest zdefiniowany), aby wskazywał na następny znak. Jeśli strumień znajduje się na końcu pliku, wskaźnik końca pliku dla strumienia jest ustawiony.

**fgetc** jest odpowiednikiem **getc —**, ale jest zaimplementowana tylko jako funkcja, a nie jako funkcja i makro.

**fgetwc** to dwubajtowa wersja **fgetc**; Odczytuje **c** jako znak wielobajtowy lub szeroki znak w zależności od tego, czy *strumień* jest otwarty w trybie tekstowym czy w trybie binarnym.

Wersje z sufiksem **_nolock** są identyczne, z tą różnicą, że nie są chronione przed ingerencją przez inne wątki.

Aby uzyskać więcej informacji o przetwarzaniu szerokich znaków i znaków wielobajtowych w trybach tekstowych i binarnych, zobacz [we/wy strumienia Unicode w trybach tekstowych i binarnych](../../c-runtime-library/unicode-stream-i-o-in-text-and-binary-modes.md).

Domyślnie globalny stan tej funkcji jest objęty zakresem aplikacji. Aby to zmienić, zobacz [stan globalny w CRT](../global-state.md).

### <a name="generic-text-routine-mappings"></a>Mapowania procedur zwykłego tekstu

|Procedura TCHAR.H|Nie zdefiniowano _MBCS _UNICODE &|_MBCS zdefiniowano|_UNICODE zdefiniowano|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_fgettc**|**fgetc**|**fgetc**|**fgetwc**|

## <a name="requirements"></a>Wymagania

|Funkcja|Wymagany nagłówek|
|--------------|---------------------|
|**fgetc**|\<stdio. h>|
|**fgetwc**|\<stdio. h> lub \<WCHAR. h>|

Aby uzyskać dodatkowe informacje o zgodności, zobacz [zgodność](../../c-runtime-library/compatibility.md).

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

## <a name="input-crt_fgetctxt"></a>Dane wejściowe: crt_fgetc. txt

```Input
Line one.
Line two.
```

### <a name="output"></a>Dane wyjściowe

```Output
Line one.
Line two.
```

## <a name="see-also"></a>Zobacz też

[We/Wy strumienia](../../c-runtime-library/stream-i-o.md)<br/>
[fputc, fputwc](fputc-fputwc.md)<br/>
[getc, getwc](getc-getwc.md)<br/>
