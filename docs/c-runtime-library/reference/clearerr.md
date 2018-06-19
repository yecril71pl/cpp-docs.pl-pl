---
title: clearerr — | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
apiname:
- clearerr
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
- clearerr
dev_langs:
- C++
helpviewer_keywords:
- error indicator for streams
- resetting stream error indicator
- clearerr function
ms.assetid: a9711cd4-3335-43d4-a018-87bbac5b3bac
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 9c78355277fbb987d82bed46fb0b5f4ffd848b6a
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
ms.locfileid: "32395305"
---
# <a name="clearerr"></a>clearerr

Resetuje wskaźnik błędów dla strumienia. Bezpieczniejsza wersja ta funkcja jest dostępna; zobacz [clearerr_s —](clearerr-s.md).

## <a name="syntax"></a>Składnia

```C
void clearerr(
   FILE *stream
);
```

### <a name="parameters"></a>Parametry

*strumień* wskaźnik do **pliku** struktury.

## <a name="remarks"></a>Uwagi

**Clearerr —** funkcja resetuje wskaźnik błędów i wskaźnik plik końcowy *strumienia*. Wskaźniki błędów nie są automatycznie usuwane; Po ustawieniu wskaźnik błędów dla określonego strumienia operacji na strumieniu w dalszym ciągu zwracają wartość błąd do **clearerr —**, [fseek](fseek-fseeki64.md), **fsetpos —**, lub [rewind](rewind.md) jest wywoływana.

Jeśli *strumienia* jest **NULL**, program obsługi nieprawidłowych parametrów zostanie wywołany, zgodnie z opisem w [sprawdzanie poprawności parametru](../../c-runtime-library/parameter-validation.md). Jeśli wykonanie może kontynuować, ta funkcja ustawia **errno** do **einval —** i zwraca. Aby uzyskać więcej informacji na temat **errno** i kody błędów, zobacz [errno — stałe](../../c-runtime-library/errno-constants.md).

Bezpieczniejsza wersja ta funkcja jest dostępna; zobacz [clearerr_s —](clearerr-s.md).

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|
|-------------|---------------------|
|**clearerr**|\<stdio.h>|

Aby uzyskać dodatkowe informacje o zgodności, zobacz [zgodności](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Przykład

```C
// crt_clearerr.c
// This program creates an error
// on the standard input stream, then clears
// it so that future reads won't fail.

#include <stdio.h>

int main( void )
{
   int c;
   // Create an error by writing to standard input.
   putc( 'c', stdin );
   if( ferror( stdin ) )
   {
      perror( "Write error" );
      clearerr( stdin );
   }

   // See if read causes an error.
   printf( "Will input cause an error? " );
   c = getc( stdin );
   if( ferror( stdin ) )
   {
      perror( "Read error" );
      clearerr( stdin );
   }
   else
      printf( "No read error\n" );
}
```

```Output

n

```

```Output

      nWrite error: No error
Will input cause an error? n
No read error
```

## <a name="see-also"></a>Zobacz także

[Obsługa błędów](../../c-runtime-library/error-handling-crt.md)<br/>
[We/Wy strumienia](../../c-runtime-library/stream-i-o.md)<br/>
[_eof](eof.md)<br/>
[feof](feof.md)<br/>
[ferror](ferror.md)<br/>
[perror, _wperror](perror-wperror.md)<br/>
