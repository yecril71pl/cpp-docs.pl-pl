---
title: fgets, fgetws
ms.date: 4/2/2020
api_name:
- fgets
- fgetws
- _o_fgets
- _o_fgetws
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
ms.openlocfilehash: a1120529157801aac5cf1c4fd61f844fde443bed
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81346867"
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

*Str*<br/>
Lokalizacja przechowywania danych.

*numChars (liczbaChars)*<br/>
Maksymalna liczba znaków do odczytania.

*Strumienia*<br/>
Wskaźnik do struktury **PLIK.**

## <a name="return-value"></a>Wartość zwracana

Każda z tych funkcji zwraca *ul*. **Wartość NULL** jest zwracana w celu wskazania błędu lub stanu końca pliku. Użyj **feof** lub **ferror,** aby ustalić, czy wystąpił błąd. Jeśli *str* lub *stream* jest wskaźnikiem zerowym lub *numChars* jest mniejsza lub równa zero, ta funkcja wywołuje nieprawidłowy program obsługi parametrów, zgodnie z opisem w [weryfikacji parametrów](../../c-runtime-library/parameter-validation.md). Jeśli wykonanie jest dozwolone, **errno** jest ustawiona na **Wartość EINVAL,** a funkcja zwraca **wartość NULL**.

Zobacz [_doserrno, errno, _sys_errlist i _sys_nerr aby](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md) uzyskać więcej informacji na temat tych i innych kodów błędów.

## <a name="remarks"></a>Uwagi

Funkcja **fgets** odczytuje ciąg z argumentu *strumienia* wejściowego i przechowuje go w *str*. **fgets odczytuje** znaki z bieżącej pozycji strumienia do pierwszego znaku nowego linii włącznie, do końca strumienia lub do czasu, gdy liczba odczytanych znaków jest równa *numChars* - 1, w zależności od tego, co nastąpi wcześniej. Wynik przechowywany w *str* jest dołączany ze znakiem zerowym. Znak nowego linii, jeśli odczyt, znajduje się w ciągu.

**fgetws** jest szerokoznakową wersją **fgets**.

**fgetws** odczytuje argument szerokoznakowy *jako* ciąg wieloznakowy lub ciąg znaków szerokoznakowych zgodnie z tym, czy *strumień* jest otwierany odpowiednio w trybie tekstowym, czy w trybie binarnym. Aby uzyskać więcej informacji na temat używania tekstu i trybów binarnych w trybie Unicode i wielobajtowym strumieniu We/Wy, zobacz [We/Wy pliku tekstowego i binarnego oraz](../../c-runtime-library/text-and-binary-mode-file-i-o.md) [we/wy strumienia Unicode w trybach tekstowych i binarnych](../../c-runtime-library/unicode-stream-i-o-in-text-and-binary-modes.md).

Domyślnie stan globalny tej funkcji jest ograniczony do aplikacji. Aby to zmienić, zobacz [Stan globalny w crt](../global-state.md).

### <a name="generic-text-routine-mappings"></a>Mapowania procedur zwykłego tekstu

|Procedura TCHAR.H|_UNICODE nie zdefiniowano & _MBCS|_MBCS zdefiniowano|_UNICODE zdefiniowano|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_fgetts**|**fgets**|**fgets**|**fgetws ( fgetws )**|

## <a name="requirements"></a>Wymagania

|Funkcja|Wymagany nagłówek|
|--------------|---------------------|
|**fgets**|\<stdio.h>|
|**fgetws ( fgetws )**|\<stdio.h> lub \<wchar.h>|

Aby uzyskać dodatkowe informacje o zgodności, zobacz [Zgodność](../../c-runtime-library/compatibility.md).

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

### <a name="input-crt_fgetstxt"></a>Dane wejściowe: crt_fgets.txt

```Input
Line one.
Line two.
```

### <a name="output"></a>Dane wyjściowe

```Output
Line one.
```

## <a name="see-also"></a>Zobacz też

[We/Wy strumienia](../../c-runtime-library/stream-i-o.md)<br/>
[fputs, fputws](fputs-fputws.md)<br/>
[gets, _getws](../../c-runtime-library/gets-getws.md)<br/>
[puts, _putws](puts-putws.md)<br/>
