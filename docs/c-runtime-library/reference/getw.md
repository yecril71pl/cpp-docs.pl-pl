---
title: _getw
ms.date: 11/04/2016
apiname:
- _getw
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
- _getw
helpviewer_keywords:
- _getw function
- integers, getting from streams
- getw function
ms.assetid: ef75facc-b84e-470f-9f5f-8746c90822a0
ms.openlocfilehash: 615d3ac9bdc73ad200368eaeabf7c84951bc91ae
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50487610"
---
# <a name="getw"></a>_getw

Pobiera liczbę całkowitą ze strumienia.

## <a name="syntax"></a>Składnia

```C
int _getw(
   FILE *stream
);
```

### <a name="parameters"></a>Parametry

*Stream*<br/>
Wskaźnik do **pliku** struktury.

## <a name="return-value"></a>Wartość zwracana

**_getw —** zwraca wartość całkowitą odczytu. Zwracana wartość wynosząca **EOF** wskazuje błąd lub koniec pliku. Jednak ponieważ **EOF** wartość jest również wartością całkowitą autoryzowanych, należy użyć **feof** lub **ferror** Aby zweryfikować warunek końca pliku lub błąd. Jeśli *strumienia* jest **NULL**, procedura obsługi nieprawidłowego parametru zostanie wywołana, zgodnie z opisem w [Parameter Validation](../../c-runtime-library/parameter-validation.md). Jeśli wykonanie może być kontynuowane, **errno** ustawiono **EINVAL** a funkcja zwraca **EOF**.

## <a name="remarks"></a>Uwagi

**_Getw —** funkcja odczytuje następny wartość binarna typu **int** z pliku skojarzone z *strumienia* i zwiększa skojarzony wskaźnik pliku (jeśli istnieje) w celu wskazania Następny znak jako nieprzeczytane. **_getw —** nie przyjmuje żadnych specjalnych wyrównania elementów w strumieniu. Mogą wystąpić problemy z przenoszenie ze **_getw —** ponieważ rozmiar **int** typu i kolejność bajtów w ramach **int** typu różne w różnych systemach.

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|
|-------------|---------------------|
|**_getw**|\<stdio.h>|

Aby uzyskać więcej informacji na temat zgodności, zobacz [zgodności](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Przykład

```C
// crt_getw.c
// This program uses _getw to read a word
// from a stream, then performs an error check.

#include <stdio.h>
#include <stdlib.h>

int main( void )
{
   FILE *stream;
   int i;

   if( fopen_s( &stream, "crt_getw.txt", "rb" ) )
      printf( "Couldn't open file\n" );
   else
   {
      // Read a word from the stream:
      i = _getw( stream );

      // If there is an error...
      if( ferror( stream ) )
      {
         printf( "_getw failed\n" );
         clearerr_s( stream );
      }
      else
         printf( "First data word in file: 0x%.4x\n", i );
      fclose( stream );
   }
}
```

### <a name="input-crtgetwtxt"></a>Dane wejściowe: crt_getw.txt

```Input
Line one.
Line two.
```

### <a name="output"></a>Dane wyjściowe

```Output
First data word in file: 0x656e694c
```

## <a name="see-also"></a>Zobacz także

[Stream operacji We/Wy](../../c-runtime-library/stream-i-o.md)<br/>
[_putw](putw.md)<br/>
