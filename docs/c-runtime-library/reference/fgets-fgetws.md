---
title: fgets, fgetws
ms.date: 07/11/2018
api_name:
- fgets
- fgetws
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
ms.openlocfilehash: 3f68bee181ebb20eb7a0a2eaca02a72c4dc03616
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/12/2019
ms.locfileid: "70957397"
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
Lokalizacja magazynu dla danych.

*numChars*<br/>
Maksymalna liczba znaków do odczytania.

*stream*<br/>
Wskaźnik do struktury **pliku** .

## <a name="return-value"></a>Wartość zwracana

Każda z tych funkcji zwraca *str*. Zwraca **wartość null** , aby wskazać błąd lub warunek końca pliku. Użyj **feof** lub obiektu **odwołującego** , aby określić, czy wystąpił błąd. Jeśli *str* lub *Stream* jest wskaźnikiem o wartości null lub wartość *numChars* jest mniejsza lub równa zero, ta funkcja wywołuje procedurę obsługi nieprawidłowego parametru, zgodnie z opisem w [walidacji parametru](../../c-runtime-library/parameter-validation.md). Jeśli wykonanie może być kontynuowane, **errno** jest ustawiona na **EINVAL** , a funkcja zwraca **wartość null**.

Zobacz [_doserrno, errno, _sys_errlist i _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md) , aby uzyskać więcej informacji na temat tych i innych kodów błędów.

## <a name="remarks"></a>Uwagi

Funkcja **fgets** odczytuje ciąg z argumentu *strumienia* wejściowego i zapisuje go w *str*. **fgets** odczytuje znaki z bieżącego strumienia do i łącznie z pierwszym znakiem nowego wiersza, na końcu strumienia lub dopóki Liczba odczytanych znaków jest równa *numChars* -1, zależnie od tego, co nastąpi wcześniej. Wynik zapisany w *str* jest dołączany do znaku o wartości null. Znak nowego wiersza, jeśli jest odczytywany, jest uwzględniony w ciągu.

**fgetws** to dwubajtowa wersja **fgets**.

**fgetws** odczytuje argument o szerokim znaku *w postaci* ciągu znaków wielobajtowych lub dwubajtowego ciągu w zależności od tego, czy *strumień* jest otwarty odpowiednio w trybie tekstowym czy w trybie binarnym. Aby uzyskać więcej informacji na temat używania trybów tekstowych i binarnych w strumieniach Unicode i wielobajtowych — we/wy, zobacz [plik tekstowy i tryb binarny we/wy](../../c-runtime-library/text-and-binary-mode-file-i-o.md) i [strumienia Unicode/o w trybach tekstowych i binarnych](../../c-runtime-library/unicode-stream-i-o-in-text-and-binary-modes.md).

### <a name="generic-text-routine-mappings"></a>Mapowania procedur zwykłego tekstu

|Procedura TCHAR.H|Nie zdefiniowano _UNICODE & _MBCS|_MBCS zdefiniowano|_UNICODE zdefiniowano|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_fgetts**|**fgets**|**fgets**|**fgetws**|

## <a name="requirements"></a>Wymagania

|Funkcja|Wymagany nagłówek|
|--------------|---------------------|
|**fgets**|\<stdio.h>|
|**fgetws**|\<stdio. h > lub \<WCHAR. h >|

Aby uzyskać dodatkowe informacje o zgodności, zobacz [zgodność](../../c-runtime-library/compatibility.md).

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

### <a name="input-crt_fgetstxt"></a>Dane wejściowe: crt_fgets. txt

```Input
Line one.
Line two.
```

### <a name="output"></a>Dane wyjściowe

```Output
Line one.
```

## <a name="see-also"></a>Zobacz także

[We/wy strumienia](../../c-runtime-library/stream-i-o.md)<br/>
[fputs, fputws](fputs-fputws.md)<br/>
[gets, _getws](../../c-runtime-library/gets-getws.md)<br/>
[puts, _putws](puts-putws.md)<br/>
