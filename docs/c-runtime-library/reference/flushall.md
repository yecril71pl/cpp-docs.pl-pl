---
title: _flushall
ms.date: 4/2/2020
api_name:
- _flushall
- _o__flushall
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
- _flushall
helpviewer_keywords:
- flushall function
- flushing streams
- streams, flushing
- _flushall function
ms.assetid: 2cd73562-6d00-4ca2-b13c-80d0ae7870b5
ms.openlocfilehash: 93181c0fe941a1c5e259e706771495666329bcb3
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81346619"
---
# <a name="_flushall"></a>_flushall

Opróżnia wszystkie strumienie; usuwa wszystkie bufory.

## <a name="syntax"></a>Składnia

```C
int _flushall( void );
```

## <a name="return-value"></a>Wartość zwracana

**_flushall** zwraca liczbę otwartych strumieni (wejście i wyjście). Nie ma zwracania błędów.

## <a name="remarks"></a>Uwagi

Domyślnie funkcja **_flushall** zapisuje do odpowiednich plików zawartość wszystkich buforów skojarzonych z otwartymi strumieniami wyjściowymi. Wszystkie bufory skojarzone z otwartymi strumieniami wejściowymi są czyszczone z ich bieżącej zawartości. (Bufory te są zwykle obsługiwane przez system operacyjny, który określa optymalny czas automatycznego zapisywania danych na dysku: gdy bufor jest pełny, gdy strumień jest zamknięty lub gdy program kończy się normalnie bez zamykania strumieni.)

Jeśli odczyt następuje wywołanie **_flushall**, nowe dane są odczytywane z plików wejściowych do buforów. Wszystkie strumienie pozostają otwarte po wywołaniu **_flushall**.

Funkcja zatwierdzania na dysku biblioteki w czasie wykonywania pozwala upewnić się, że dane krytyczne są zapisywane bezpośrednio na dysku, a nie do buforów systemu operacyjnego. Bez przepisywania istniejącego programu można włączyć tę funkcję, łącząc pliki obiektów programu z plikiem Commode.obj. W wynikowym pliku wykonywalnym wywołania **_flushall** zapisu zawartości wszystkich buforów na dysku. Commode.obj dotyczy tylko **_flushall** i [fflush.](fflush.md)

Aby uzyskać informacje dotyczące sterowania funkcją zatwierdzania na dysku, zobacz [Stream we/wy](../../c-runtime-library/stream-i-o.md), [fopen](fopen-wfopen.md)i [_fdopen](fdopen-wfdopen.md).

Domyślnie stan globalny tej funkcji jest ograniczony do aplikacji. Aby to zmienić, zobacz [Stan globalny w crt](../global-state.md).

## <a name="requirements"></a>Wymagania

|Funkcja|Wymagany nagłówek|
|--------------|---------------------|
|**_flushall**|\<stdio.h>|

Aby uzyskać więcej informacji o zgodności, zobacz [Zgodność](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Przykład

```C
// crt_flushall.c
// This program uses _flushall
// to flush all open buffers.

#include <stdio.h>

int main( void )
{
   int numflushed;

   numflushed = _flushall();
   printf( "There were %d streams flushed\n", numflushed );
}
```

```Output
There were 3 streams flushed
```

## <a name="see-also"></a>Zobacz też

[We/Wy strumienia](../../c-runtime-library/stream-i-o.md)<br/>
[_commit](commit.md)<br/>
[fclose, _fcloseall](fclose-fcloseall.md)<br/>
[fflush](fflush.md)<br/>
[setvbuf](setvbuf.md)<br/>
