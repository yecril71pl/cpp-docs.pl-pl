---
title: _flushall
ms.date: 11/04/2016
apiname:
- _flushall
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
- _flushall
helpviewer_keywords:
- flushall function
- flushing streams
- streams, flushing
- _flushall function
ms.assetid: 2cd73562-6d00-4ca2-b13c-80d0ae7870b5
ms.openlocfilehash: de8caf30568816f41441f5d9487293c346d2bff1
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50466247"
---
# <a name="flushall"></a>_flushall

Czyści wszystkie strumienie; Czyści wszystkie bufory.

## <a name="syntax"></a>Składnia

```C
int _flushall( void );
```

## <a name="return-value"></a>Wartość zwracana

**_flushall —** zwraca liczbę otwartych strumieni (dane wejściowe i wyjściowe). Nie będzie zwrotu błędu.

## <a name="remarks"></a>Uwagi

Domyślnie **_flushall —** funkcja zapisuje do odpowiednich plików zawartości wszystkich buforów skojarzone z strumienie wyjściowe Otwórz. Wszystkie bufory skojarzone z otwartych strumienie wejściowe są usuwane z ich bieżącą zawartość. (Bufory są zazwyczaj obsługiwane przez system operacyjny, który określa optymalny czas automatycznie zapisywać dane na dysku: gdy bufor jest pełny, jeśli strumień jest zamknięty lub gdy program kończy się normalnie bez zamykania strumieni.)

Jeśli odczyt następuje po wywołaniu **_flushall —**, nowe dane są odczytywane z plików wejściowych do buforów. Wszystkie strumienie pozostają otwarte po wywołaniu **_flushall —**.

Funkcja commit-to-disk biblioteki wykonawczej pozwala upewnić się, że krytyczne dane są zapisywane bezpośrednio na dysku, a nie do buforów systemu operacyjnego. Bez konieczności ponownego zapisu istniejący program, można włączyć tę funkcję, konsolidacji plików obiektu programu z plikiem Commode.obj. Wynikowy plik wykonywalny wywołuje w celu **_flushall —** zapisywanie zawartości wszystkich buforów na dysku. Tylko **_flushall —** i [fflush —](fflush.md) dotyczy plikiem Commode.obj.

Aby uzyskać informacje o sposobie sterowania funkcją commit-to-disk, zobacz [Stream operacji We/Wy](../../c-runtime-library/stream-i-o.md), [fopen —](fopen-wfopen.md), i [_fdopen —](fdopen-wfdopen.md).

## <a name="requirements"></a>Wymagania

|Funkcja|Wymagany nagłówek|
|--------------|---------------------|
|**_flushall**|\<stdio.h>|

Aby uzyskać więcej informacji na temat zgodności, zobacz [zgodności](../../c-runtime-library/compatibility.md).

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

## <a name="see-also"></a>Zobacz także

[Stream operacji We/Wy](../../c-runtime-library/stream-i-o.md)<br/>
[_commit](commit.md)<br/>
[fclose, _fcloseall](fclose-fcloseall.md)<br/>
[fflush](fflush.md)<br/>
[setvbuf](setvbuf.md)<br/>
