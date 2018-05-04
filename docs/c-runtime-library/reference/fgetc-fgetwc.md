---
title: fgetc —, fgetwc — | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
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
dev_langs:
- C++
helpviewer_keywords:
- fgettc function
- characters, reading
- _fgettc function
- fgetc function
- streams, reading characters from
- reading characters from streams
- fgetwc function
ms.assetid: 13348b7b-dc86-421c-9d6c-611ca79c8338
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: f06c5c2f092932d97755a8f0cff63cde3a9682c6
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
---
# <a name="fgetc-fgetwc"></a>fgetc, fgetwc

Znak odczytu ze strumienia.

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

*Strumień*<br/>
Wskaźnik do **pliku** struktury.

## <a name="return-value"></a>Wartość zwracana

**fgetc —** zwraca znak odczytany jako **int** lub zwraca **EOF** wskazująca błąd lub koniec pliku. **fgetwc —** zwraca, jako [wint_t —](../../c-runtime-library/standard-types.md), znaków dwubajtowych, który odpowiada znaków do odczytu lub zwraca **weof —** wskazująca błąd lub koniec pliku. Dla obu tych funkcji, należy użyć **feof —** lub **ferror —** odróżnić błąd warunku końcowego pliku. Jeśli wystąpi błąd odczytu, ustawiono Wskaźnik błędów dla tego strumienia. Jeśli *strumienia* jest **NULL**, **fgetc —** i **fgetwc —** Wywołaj program obsługi nieprawidłowych parametrów, zgodnie z opisem w [parametru Sprawdzanie poprawności](../../c-runtime-library/parameter-validation.md). Jeśli dozwolone jest wykonywanie aby kontynuować, ustawianie tych funkcji **errno** do **einval —** i zwracać **EOF**.

## <a name="remarks"></a>Uwagi

Każda z tych funkcji odczytuje od bieżącego położenia pliku skojarzone z pojedynczym znakiem *strumienia*. Funkcja zwiększa następnie kursor skojarzony plik (jeśli jest zdefiniowana), aby wskazywały na następny znak. Jeśli strumień jest na końcu pliku, jest ustawiony dla tego strumienia wskaźnika końca pliku.

**fgetc —** jest odpowiednikiem **getc —**, ale jest zaimplementowana tylko jako funkcję, a nie jako funkcję i makr.

**fgetwc —** jest wersja znaków dwubajtowych **fgetc —**; odczytuje **c** jako znaków wielobajtowych lub znaków dwubajtowych zgodnie z czy *strumienia* jest otwarty w trybu tekst lub binarny.

Wersje z **_nolock —** sufiks są identyczne z tą różnicą, że nie są chronione przez inne wątki od zakłóceń.

Aby uzyskać więcej informacji na temat przetwarzania znaki dwubajtowe i znaków wielobajtowych w trybach tekstowym i binarnym, zobacz [we/wy strumienia w Unicode w trybach tekstowym i binarnym](../../c-runtime-library/unicode-stream-i-o-in-text-and-binary-modes.md).

### <a name="generic-text-routine-mappings"></a>Mapowania procedur zwykłego tekstu

|Procedura TCHAR.H|_Unicode — & _MBCS nie zdefiniowany|_MBCS zdefiniowano|_UNICODE zdefiniowano|
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

[We/Wy strumienia](../../c-runtime-library/stream-i-o.md)<br/>
[fputc, fputwc](fputc-fputwc.md)<br/>
[getc, getwc](getc-getwc.md)<br/>
