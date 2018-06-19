---
title: fscanf —, _fscanf_l —, fwscanf —, _fwscanf_l — | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
apiname:
- fscanf
- _fwscanf_l
- _fscanf_l
- fwscanf
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
apitype: DLLExport
f1_keywords:
- fscanf
- fwscanf
- _ftscanf_l
- _fwscanf_l
- _ftscanf
- _fscanf_l
dev_langs:
- C++
helpviewer_keywords:
- fscanf function
- fwscanf function
- formatted data [C++], reading from streams
- ftscanf_l function
- _ftscanf_l function
- _fwscanf_l function
- data [CRT], reading from streams
- _fscanf_l function
- ftscanf function
- fscanf_l function
- streams [C++], reading formatted data from
- _ftscanf function
- fwscanf_l function
ms.assetid: 9004e978-6c5f-4bb2-98fd-51e5948933f2
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 72ed322c78723826615e1264642eb53f6f9eb14d
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
ms.locfileid: "32404077"
---
# <a name="fscanf-fscanfl-fwscanf-fwscanfl"></a>fscanf, _fscanf_l, fwscanf, _fwscanf_l

Odczyt sformatowanych danych ze strumienia. Bezpieczniejsza wersje te funkcje są dostępne; zobacz [fscanf_s —, _fscanf_s_l —, fwscanf_s —, _fwscanf_s_l —](fscanf-s-fscanf-s-l-fwscanf-s-fwscanf-s-l.md).

## <a name="syntax"></a>Składnia

```C
int fscanf(
   FILE *stream,
   const char *format [,
   argument ]...
);
int _fscanf_l(
   FILE *stream,
   const char *format,
   locale_t locale [,
   argument ]...
);
int fwscanf(
   FILE *stream,
   const wchar_t *format [,
   argument ]...
);
int _fwscanf_l(
   FILE *stream,
   const wchar_t *format,
   locale_t locale [,
   argument ]...
);
```

### <a name="parameters"></a>Parametry

*Strumień*<br/>
Wskaźnik do **pliku** struktury.

*Format*<br/>
Ciąg kontroli formatu.

*Argument*<br/>
Argumenty opcjonalne.

*Ustawienia regionalne*<br/>
Ustawienia regionalne do użycia.

## <a name="return-value"></a>Wartość zwracana

Każda z tych funkcji zwraca liczbę pól pomyślnie przekonwertowany i przypisane; wartość zwrotna nie zawiera pola, które zostały do odczytu, ale nie są przypisane. Wartość zwracana 0 wskazuje, że nie ma pól zostały przypisane. Jeśli wystąpi błąd, lub czy osiągnięto koniec strumienia pliku przed pierwszym konwersji, jest zwracana wartość **EOF** dla **fscanf —** i **fwscanf —**.

Te funkcje walidację ich parametrów. Jeśli *strumienia* lub *format* wskaźnika o wartości null, jest program obsługi nieprawidłowych parametrów zostanie wywołany, zgodnie z opisem w [sprawdzanie poprawności parametru](../../c-runtime-library/parameter-validation.md). Jeśli jest dozwolone wykonywanie, aby kontynuować, te funkcje zwracają **EOF** i ustaw **errno** do **einval —**.

## <a name="remarks"></a>Uwagi

**Fscanf —** funkcja odczytuje dane z bieżącej pozycji *strumienia* do lokalizacji podanej przez *argument* (jeśli istnieje). Każdy *argument* musi być wskaźnikiem do zmiennej typu, który odpowiada specyfikatorowi typu w *format*. *Format* formanty interpretacji dane wejściowe pola i ma tę samą tworzą i funkcję, która *format* argument **scanf**; zobacz [scanf](scanf-scanf-l-wscanf-wscanf-l.md) dla Opis *format*.

**fwscanf —** jest wersja znaków dwubajtowych **fscanf —**; argument formatu **fwscanf —** jest ciągiem znaków dwubajtowych. Te funkcje zachowują się tak samo tak samo, jakby strumień jest otwarty w trybie ANSI. **fscanf —** nie obsługuje obecnie danych wejściowych z strumienia UNICODE.

Wersje tych funkcji z **_l** sufiks są identyczne, z wyjątkiem tego, aby używały parametr ustawień regionalnych przekazano zamiast bieżącego ustawienia regionalne wątku.

### <a name="generic-text-routine-mappings"></a>Mapowania procedur zwykłego tekstu

|Procedura TCHAR.H|_Unicode — & _MBCS nie zdefiniowany|_MBCS zdefiniowano|_UNICODE zdefiniowano|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_ftscanf —**|**fscanf —**|**fscanf —**|**fwscanf**|
|**_ftscanf_l —**|**_fscanf_l**|**_fscanf_l**|**_fwscanf_l**|

Aby uzyskać więcej informacji, zobacz [pola specyfikacji formatu - scanf funkcji i funkcji wscanf —](../../c-runtime-library/format-specification-fields-scanf-and-wscanf-functions.md).

## <a name="requirements"></a>Wymagania

|Funkcja|Wymagany nagłówek|
|--------------|---------------------|
|**fscanf —**, **_fscanf_l —**|\<stdio.h>|
|**fwscanf —**, **_fwscanf_l —**|\<stdio.h > lub \<wchar.h >|

Aby uzyskać dodatkowe informacje o zgodności, zobacz [zgodności](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Przykład

```C
// crt_fscanf.c
// compile with: /W3
// This program writes formatted
// data to a file. It then uses fscanf to
// read the various data back from the file.

#include <stdio.h>

FILE *stream;

int main( void )
{
   long l;
   float fp;
   char s[81];
   char c;

   if( fopen_s( &stream, "fscanf.out", "w+" ) != 0 )
      printf( "The file fscanf.out was not opened\n" );
   else
   {
      fprintf( stream, "%s %ld %f%c", "a-string",
               65000, 3.14159, 'x' );
      // Security caution!
      // Beware loading data from a file without confirming its size,
      // as it may lead to a buffer overrun situation.

      // Set pointer to beginning of file:
      fseek( stream, 0L, SEEK_SET );

      // Read data back from file:
      fscanf( stream, "%s", s );   // C4996
      fscanf( stream, "%ld", &l ); // C4996

      fscanf( stream, "%f", &fp ); // C4996
      fscanf( stream, "%c", &c );  // C4996
      // Note: fscanf is deprecated; consider using fscanf_s instead

      // Output data read:
      printf( "%s\n", s );
      printf( "%ld\n", l );
      printf( "%f\n", fp );
      printf( "%c\n", c );

      fclose( stream );
   }
}
```

```Output
a-string
65000
3.141590
x
```

## <a name="see-also"></a>Zobacz także

[We/Wy strumienia](../../c-runtime-library/stream-i-o.md)<br/>
[_cscanf, _cscanf_l, _cwscanf, _cwscanf_l](cscanf-cscanf-l-cwscanf-cwscanf-l.md)<br/>
[fprintf, _fprintf_l, fwprintf, _fwprintf_l](fprintf-fprintf-l-fwprintf-fwprintf-l.md)<br/>
[scanf, _scanf_l, wscanf, _wscanf_l](scanf-scanf-l-wscanf-wscanf-l.md)<br/>
[sscanf, _sscanf_l, swscanf, _swscanf_l](sscanf-sscanf-l-swscanf-swscanf-l.md)<br/>
[fscanf_s, _fscanf_s_l, fwscanf_s, _fwscanf_s_l](fscanf-s-fscanf-s-l-fwscanf-s-fwscanf-s-l.md)<br/>
