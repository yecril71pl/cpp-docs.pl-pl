---
title: _getw
ms.date: 4/2/2020
api_name:
- _getw
- _o__getw
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
- _getw
helpviewer_keywords:
- _getw function
- integers, getting from streams
- getw function
ms.assetid: ef75facc-b84e-470f-9f5f-8746c90822a0
ms.openlocfilehash: fc1dfcc54259dfe40d2fc37be1e1c0ab63ab7c4a
ms.sourcegitcommit: 5a069c7360f75b7c1cf9d4550446ec2fa2eb2293
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/07/2020
ms.locfileid: "82916310"
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

*produkcyjne*<br/>
Wskaźnik do struktury **pliku** .

## <a name="return-value"></a>Wartość zwracana

**_getw** zwraca wartość typu Integer Read. Wartość zwracana przez **znacznik EOF** wskazuje na błąd lub koniec pliku. Jednak ze względu na to, że wartość **eof** jest również wiarygodną wartością całkowitą, użyj **feof** lub obiektu **odwołującego** , aby zweryfikować warunek końca pliku lub błędu. Jeśli *strumień* ma **wartość null**, zostanie wywołana procedura obsługi nieprawidłowego parametru, zgodnie z opisem w [walidacji parametru](../../c-runtime-library/parameter-validation.md). Jeśli wykonanie może być kontynuowane, **errno** jest ustawiona na **EINVAL** , a funkcja zwraca **znacznik EOF**.

## <a name="remarks"></a>Uwagi

Funkcja **_getw** odczytuje następną wartość binarną typu **int** z pliku skojarzonego ze *strumieniem* i zwiększa skojarzony wskaźnik pliku (jeśli istnieje), aby wskazywała na Następny nieprzeczytany znak. **_getw** nie zakłada żadnego specjalnego wyrównania elementów w strumieniu. Problemy z portami mogą wystąpić w **_getw** , ponieważ rozmiar typu **int** i kolejność bajtów w typie **int** różnią się w różnych systemach.

Domyślnie globalny stan tej funkcji jest objęty zakresem aplikacji. Aby to zmienić, zobacz [stan globalny w CRT](../global-state.md).

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|
|-------------|---------------------|
|**_getw**|\<stdio. h>|

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

## <a name="see-also"></a>Zobacz też

[We/Wy strumienia](../../c-runtime-library/stream-i-o.md)<br/>
[_putw](putw.md)<br/>
