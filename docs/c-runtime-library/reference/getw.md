---
title: _getw
ms.date: 11/04/2016
api_name:
- _getw
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
- _getw
helpviewer_keywords:
- _getw function
- integers, getting from streams
- getw function
ms.assetid: ef75facc-b84e-470f-9f5f-8746c90822a0
ms.openlocfilehash: ad03c92ce90542ecae13609ee228ad094f64fc07
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/12/2019
ms.locfileid: "70954878"
---
# <a name="_getw"></a>_getw

Pobiera liczbę całkowitą ze strumienia.

## <a name="syntax"></a>Składnia

```C
int _getw(
   FILE *stream
);
```

### <a name="parameters"></a>Parametry

*stream*<br/>
Wskaźnik do struktury **pliku** .

## <a name="return-value"></a>Wartość zwracana

**_getw** zwraca wartość typu Integer Read. Wartość zwracana przez **znacznik EOF** wskazuje na błąd lub koniec pliku. Jednak ze względu na to, że wartość **eof** jest również wiarygodną wartością całkowitą, użyj **feof** lub obiektu **odwołującego** , aby zweryfikować warunek końca pliku lub błędu. Jeśli *strumień* ma **wartość null**, zostanie wywołana procedura obsługi nieprawidłowego parametru, zgodnie z opisem w [walidacji parametru](../../c-runtime-library/parameter-validation.md). Jeśli wykonanie może być kontynuowane, **errno** jest ustawiona na **EINVAL** , a funkcja zwraca **znacznik EOF**.

## <a name="remarks"></a>Uwagi

Funkcja **_getw** odczytuje następną wartość binarną typu **int** z pliku skojarzonego ze *strumieniem* i zwiększa skojarzony wskaźnik pliku (jeśli istnieje), aby wskazywała na Następny nieprzeczytany znak. **_getw** nie zakłada żadnego specjalnego wyrównania elementów w strumieniu. Problemy z portami mogą wystąpić z **_getw** , ponieważ rozmiar typu **int** i kolejność bajtów w typie **int** różnią się w różnych systemach.

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|
|-------------|---------------------|
|**_getw**|\<stdio.h>|

Aby uzyskać więcej informacji o zgodności, zobacz [zgodność](../../c-runtime-library/compatibility.md).

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

### <a name="input-crt_getwtxt"></a>Dane wejściowe: crt_getw. txt

```Input
Line one.
Line two.
```

### <a name="output"></a>Dane wyjściowe

```Output
First data word in file: 0x656e694c
```

## <a name="see-also"></a>Zobacz także

[We/wy strumienia](../../c-runtime-library/stream-i-o.md)<br/>
[_putw](putw.md)<br/>
