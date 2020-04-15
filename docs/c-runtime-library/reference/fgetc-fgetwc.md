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
- api-ms-win-crt-private-l1-1-0
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
ms.openlocfilehash: c1589c64127b47f4dd2a1147f2b4d549601db4fc
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81347011"
---
# <a name="fgetc-fgetwc"></a>fgetc, fgetwc

Odczyt znaku ze strumienia.

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

*Strumienia*<br/>
Wskaźnik do struktury **PLIK.**

## <a name="return-value"></a>Wartość zwracana

**fgetc** zwraca znak odczytany jako **int** lub zwraca **EOF,** aby wskazać błąd lub koniec pliku. **fgetwc** zwraca, jako [wint_t,](../../c-runtime-library/standard-types.md)szeroki znak odpowiadający odczytowi lub zwraca **WEOF,** aby wskazać błąd lub koniec pliku. W przypadku obu funkcji należy użyć **feof** lub **ferror,** aby odróżnić błąd od stanu końca pliku. Jeśli wystąpi błąd odczytu, zostanie ustawiony wskaźnik błędu dla strumienia. Jeśli *strumień* ma **wartość NULL**, **fgetc** i **fgetwc** wywołać nieprawidłowy program obsługi parametrów, zgodnie z opisem w [weryfikacji parametrów](../../c-runtime-library/parameter-validation.md). Jeśli wykonanie jest dozwolone, te funkcje ustawić **errno** na **EINVAL** i zwrócić **EOF**.

## <a name="remarks"></a>Uwagi

Każda z tych funkcji odczytuje pojedynczy znak z bieżącej pozycji pliku skojarzonego ze *strumieniem*. Następnie funkcja zwiększa wskaźnik skojarzonego pliku (jeśli jest zdefiniowany), aby wskazywał następny znak. Jeśli strumień znajduje się na końcu pliku, ustawiony jest wskaźnik końca pliku dla strumienia.

**fgetc** jest odpowiednikiem **getc**, ale jest realizowany tylko jako funkcja, a nie jako funkcja i makro.

**fgetwc** jest szerokoznakową wersją **fgetc**; odczytuje **c** jako znak wielobajtowy lub szeroki znak w zależności od tego, czy *strumień* jest otwarty w trybie tekstowym, czy w trybie binarnym.

Wersje z sufiksem **_nolock** są identyczne, z tą różnicą, że nie są chronione przed zakłóceniami przez inne wątki.

Aby uzyskać więcej informacji na temat przetwarzania znaków szerokich i znaków wielobajtowych w trybach tekstowych i binarnych, zobacz [Unicode Stream We/Wy w trybach tekstowych i binarnych](../../c-runtime-library/unicode-stream-i-o-in-text-and-binary-modes.md).

Domyślnie stan globalny tej funkcji jest ograniczony do aplikacji. Aby to zmienić, zobacz [Stan globalny w crt](../global-state.md).

### <a name="generic-text-routine-mappings"></a>Mapowania procedur zwykłego tekstu

|Procedura TCHAR.H|_UNICODE nie zdefiniowano & _MBCS|_MBCS zdefiniowano|_UNICODE zdefiniowano|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_fgettc**|**fgetc ( fgetc )**|**fgetc ( fgetc )**|**fgetwc ( fgetwc )**|

## <a name="requirements"></a>Wymagania

|Funkcja|Wymagany nagłówek|
|--------------|---------------------|
|**fgetc ( fgetc )**|\<stdio.h>|
|**fgetwc ( fgetwc )**|\<stdio.h> lub \<wchar.h>|

Aby uzyskać dodatkowe informacje o zgodności, zobacz [Zgodność](../../c-runtime-library/compatibility.md).

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

## <a name="input-crt_fgetctxt"></a>Dane wejściowe: crt_fgetc.txt

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
