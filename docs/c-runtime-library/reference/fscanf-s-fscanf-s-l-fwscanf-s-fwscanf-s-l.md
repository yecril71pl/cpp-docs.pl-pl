---
title: fscanf_s, _fscanf_s_l, fwscanf_s, _fwscanf_s_l
ms.date: 11/04/2016
apiname:
- fwscanf_s
- _fscanf_s_l
- _fwscanf_s_l
- fscanf_s
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
- _fwscanf_s_l
- _fscanf_s_l
- fscanf_s
- _ftscanf_s_l
- _ftscanf_s
- fwscanf_s
helpviewer_keywords:
- formatted data [C++], reading from streams
- _ftscanf_s_l function
- _fscanf_s_l function
- ftscanf_s function
- fwscanf_s function
- _ftscanf_s function
- data [CRT], reading from streams
- _fwscanf_s_l function
- fscanf_s function
- fwscanf_s_l function
- ftscanf_s_l function
- streams [C++], reading formatted data from
- fscanf_s_l function
ms.assetid: b6e88194-714b-4322-be82-1cc0b343fe01
ms.openlocfilehash: f9c1686d7e42e0e885a65e153ee4e1ff2be01f27
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50454720"
---
# <a name="fscanfs-fscanfsl-fwscanfs-fwscanfsl"></a>fscanf_s, _fscanf_s_l, fwscanf_s, _fwscanf_s_l

Odczyty sformatowanych danych ze strumienia. Te wersje [fscanf —, _fscanf_l —, fwscanf —, _fwscanf_l —](fscanf-fscanf-l-fwscanf-fwscanf-l.md) mają wzmocnienia zabezpieczeń, zgodnie z opisem w [funkcje zabezpieczeń w CRT](../../c-runtime-library/security-features-in-the-crt.md).

## <a name="syntax"></a>Składnia

```C
int fscanf_s(
   FILE *stream,
   const char *format [,
   argument ]...
);
int _fscanf_s_l(
   FILE *stream,
   const char *format,
   locale_t locale [,
   argument ]...
);
int fwscanf_s(
   FILE *stream,
   const wchar_t *format [,
   argument ]...
);
int _fwscanf_s_l(
   FILE *stream,
   const wchar_t *format,
   locale_t locale [,
   argument ]...
);
```

### <a name="parameters"></a>Parametry

*Stream*<br/>
Wskaźnik do **pliku** struktury.

*Format*<br/>
Ciąg kontroli formatu.

*Argument*<br/>
Argumenty opcjonalne.

*Ustawienia regionalne*<br/>
Ustawienia regionalne do użycia.

## <a name="return-value"></a>Wartość zwracana

Każda z tych funkcji zwraca liczbę pól pomyślnie przekonwertowanych i przypisanych; zwracana wartość nie uwzględnia pól, które zostały odczytane, ale nie przypisane. Zwracana wartość wynosząca 0 wskazuje, że nie przydzielono żadnych pól. Jeśli wystąpi błąd lub jeśli osiągnięto koniec strumienia pliku przed dokonaniem pierwszej konwersji, zwracana jest wartość **EOF** dla **fscanf_s —** i **fwscanf_s —**.

Te funkcje sprawdzają poprawność swoich parametrów. Jeśli *strumienia* jest nieprawidłowym wskaźnikiem pliku, lub *format* jest pustym wskaźnikiem, funkcje te wywołują procedurę obsługi nieprawidłowego parametru, zgodnie z opisem w [Parameter Validation](../../c-runtime-library/parameter-validation.md). Jeśli wykonanie może być kontynuowane, te funkcje zwracają **EOF** i ustaw **errno** do **EINVAL**.

## <a name="remarks"></a>Uwagi

**Fscanf_s —** funkcja odczytuje dane z bieżącego położenia obiektu *strumienia* do lokalizacji, które są określone przez *argument* (jeśli istnieje). Każdy *argument* musi być wskaźnikiem do zmiennej typu odpowiadającego specyfikatorowi typu w parametrze *format*. *Format* kontroluje interpretację danych wejściowych pola, a ma taką samą formę i funkcjonuje jako *format* argument **scanf_s**; zobacz [pola specyfikacji formatu: Funkcji wscanf](../../c-runtime-library/format-specification-fields-scanf-and-wscanf-functions.md) opis *format*.  **fwscanf_s —** to wersja znaku dwubajtowego **fscanf_s —**; format argumentu **fwscanf_s —** jest ciągiem znaku dwubajtowego. Funkcje te zachowują się identycznie, jeżeli strumień jest otwarty w trybie ANSI. **fscanf_s —** aktualnie nie obsługuje danych wejściowych ze strumienia UNICODE.

Główna różnica między funkcjami bardziej bezpiecznymi (mają **_s** sufiks) i innymi wersjami polega na to, że funkcje bardziej bezpieczne wymagają rozmiaru w znakach każdego **c**, **C**, **s**, **S**, i **[** pole Typ został przekazany jako argument zaraz po zmiennej. Aby uzyskać więcej informacji, zobacz [scanf_s, _scanf_s_l —, wscanf_s —, _wscanf_s_l —](scanf-s-scanf-s-l-wscanf-s-wscanf-s-l.md) i [scanf — specyfikacje szerokości](../../c-runtime-library/scanf-width-specification.md).

> [!NOTE]
> Parametr rozmiaru ma typ **niepodpisane**, a nie **size_t**.

Wersje tych funkcji, które mają **_l** sufiksem są identyczne, z tą różnicą, że używają parametru ustawień regionalnych, który jest przekazywany zamiast bieżących ustawień regionalnych wątku.

### <a name="generic-text-routine-mappings"></a>Mapowania procedur zwykłego tekstu

|Procedura TCHAR.H|_UNICODE & _MBCS nie zdefiniowano|_MBCS zdefiniowano|_UNICODE zdefiniowano|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_ftscanf_s —**|**fscanf_s**|**fscanf_s**|**fwscanf_s**|
|**_ftscanf_s_l —**|**_fscanf_s_l**|**_fscanf_s_l**|**_fwscanf_s_l**|

## <a name="requirements"></a>Wymagania

|Funkcja|Wymagany nagłówek|
|--------------|---------------------|
|**fscanf_s —**, **_fscanf_s_l —**|\<stdio.h>|
|**fwscanf_s —**, **_fwscanf_s_l —**|\<stdio.h > lub \<wchar.h >|

Aby uzyskać dodatkowe informacje o zgodności, zobacz [zgodności](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Przykład

```C
// crt_fscanf_s.c
// This program writes formatted
// data to a file. It then uses fscanf to
// read the various data back from the file.

#include <stdio.h>
#include <stdlib.h>

FILE *stream;

int main( void )
{
   long l;
   float fp;
   char s[81];
   char c;

   errno_t err = fopen_s( &stream, "fscanf.out", "w+" );
   if( err )
      printf_s( "The file fscanf.out was not opened\n" );
   else
   {
      fprintf_s( stream, "%s %ld %f%c", "a-string",
               65000, 3.14159, 'x' );
      // Set pointer to beginning of file:
      fseek( stream, 0L, SEEK_SET );

      // Read data back from file:
      fscanf_s( stream, "%s", s, _countof(s) );
      fscanf_s( stream, "%ld", &l );

      fscanf_s( stream, "%f", &fp );
      fscanf_s( stream, "%c", &c, 1 );

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

[Stream operacji We/Wy](../../c-runtime-library/stream-i-o.md)<br/>
[_cscanf_s, _cscanf_s_l, _cwscanf_s, _cwscanf_s_l](cscanf-s-cscanf-s-l-cwscanf-s-cwscanf-s-l.md)<br/>
[fprintf_s, _fprintf_s_l, fwprintf_s, _fwprintf_s_l](fprintf-s-fprintf-s-l-fwprintf-s-fwprintf-s-l.md)<br/>
[scanf_s, _scanf_s_l, wscanf_s, _wscanf_s_l](scanf-s-scanf-s-l-wscanf-s-wscanf-s-l.md)<br/>
[sscanf_s, _sscanf_s_l, swscanf_s, _swscanf_s_l](sscanf-s-sscanf-s-l-swscanf-s-swscanf-s-l.md)<br/>
[fscanf, _fscanf_l, fwscanf, _fwscanf_l](fscanf-fscanf-l-fwscanf-fwscanf-l.md)<br/>
