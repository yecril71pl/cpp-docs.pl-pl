---
title: fgets, fgetws
ms.date: 07/11/2018
apiname:
- fgets
- fgetws
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
- _fgetts
- fgetws
- fgets
helpviewer_keywords:
- _fgetts function
- streams, getting strings from
- streams, reading from
- fgets function
- fgetws function
- fgetts function
ms.assetid: ad549bb5-df98-4ccd-a53f-95114e60c4fc
ms.openlocfilehash: 16dfb7cb0401083960669a735a976fbcd4ad4081
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50489573"
---
# <a name="fgets-fgetws"></a>fgets, fgetws

Pobierz ciąg ze strumienia.

## <a name="syntax"></a>Składnia

```C
char *fgets(
   char *str,
   int numChars,
   FILE *stream
);
wchar_t *fgetws(
   wchar_t *str,
   int numChars,
   FILE *stream
);
```

### <a name="parameters"></a>Parametry

*str*<br/>
Lokalizacja magazynowa danych.

*numChars*<br/>
Maksymalna liczba znaków do odczytania.

*Stream*<br/>
Wskaźnik do **pliku** struktury.

## <a name="return-value"></a>Wartość zwracana

Każda z tych funkcji zwraca *str*. **Wartość NULL** zwracany jest, aby wskazać błąd lub warunek końca pliku. Użyj **feof** lub **ferror** do określenia, czy wystąpił błąd. Jeśli *str* lub *strumienia* jest wskaźnikiem wartości null lub *numChars* jest mniejszy niż lub równy zero, funkcja wywoła procedurę obsługi nieprawidłowego parametru, zgodnie z opisem w [ Walidacja parametru](../../c-runtime-library/parameter-validation.md). Jeśli wykonanie może być kontynuowane, **errno** ustawiono **EINVAL** a funkcja zwraca **NULL**.

Zobacz [_doserrno, errno, _sys_errlist i _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md) Aby uzyskać więcej informacji na temat tych i innych kodów błędu,.

## <a name="remarks"></a>Uwagi

**Fgets** funkcja odczytuje ciągu wejściowego *strumienia* argumentu i zapisuje go w *str*. **fgets** odczytuje znaki z bieżącym stanie strumienia i pierwszy znak nowego wiersza na koniec strumienia, w tym lub do momentu liczba znaków odczytanych jest równa *numChars* - 1, osiągnięta jako pierwsza. Wynik przechowywany w *str* jest dołączany znakiem null. Znak nowego wiersza, jeśli do odczytu, znajduje się w ciągu.

**fgetws —** to wersja znaku dwubajtowego **fgets**.

**fgetws —** odczytuje argument znaku dwubajtowego *str* jako ciąg znaków wielobajtowych lub ciąg znaków dwubajtowych, zgodnie z czy *strumienia* jest otwarty w trybie tekstu lub w trybie binarnym odpowiednio. Aby uzyskać więcej informacji na temat używania w trybach tekstowym i binarnym w Unicode i wielobajtowych strumienia we/wy, zobacz [tekstowych i binarnych We/Wy trybu](../../c-runtime-library/text-and-binary-mode-file-i-o.md) i [we/wy Stream w Unicode w trybach tekstowym i binarnym](../../c-runtime-library/unicode-stream-i-o-in-text-and-binary-modes.md).

### <a name="generic-text-routine-mappings"></a>Mapowania procedur zwykłego tekstu

|Procedura TCHAR.H|_UNICODE & _MBCS nie zdefiniowano|_MBCS zdefiniowano|_UNICODE zdefiniowano|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_fgetts —**|**fgets**|**fgets**|**fgetws —**|

## <a name="requirements"></a>Wymagania

|Funkcja|Wymagany nagłówek|
|--------------|---------------------|
|**fgets**|\<stdio.h>|
|**fgetws —**|\<stdio.h > lub \<wchar.h >|

Aby uzyskać dodatkowe informacje o zgodności, zobacz [zgodności](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Przykład

```C
// crt_fgets.c
// This program uses fgets to display
// the first line from a file.

#include <stdio.h>

int main( void )
{
   FILE *stream;
   char line[100];

   if( fopen_s( &stream, "crt_fgets.txt", "r" ) == 0 )
   {
      if( fgets( line, 100, stream ) == NULL)
         printf( "fgets error\numChars" );
      else
         printf( "%s", line);
      fclose( stream );
   }
}
```

### <a name="input-crtfgetstxt"></a>Dane wejściowe: crt_fgets.txt

```Input
Line one.
Line two.
```

### <a name="output"></a>Dane wyjściowe

```Output
Line one.
```

## <a name="see-also"></a>Zobacz także

[Stream operacji We/Wy](../../c-runtime-library/stream-i-o.md)<br/>
[fputs, fputws](fputs-fputws.md)<br/>
[gets, _getws](../../c-runtime-library/gets-getws.md)<br/>
[puts, _putws](puts-putws.md)<br/>
