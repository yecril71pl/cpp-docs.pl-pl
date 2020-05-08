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
- api-ms-win-crt-private-l1-1-0.dll
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
ms.openlocfilehash: 1a53eeedd5dfa0f9c01fa5883a9db33e26e3ea17
ms.sourcegitcommit: 5a069c7360f75b7c1cf9d4550446ec2fa2eb2293
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/07/2020
ms.locfileid: "82911621"
---
# <a name="_flushall"></a>_flushall

Opróżnia wszystkie strumienie; Czyści wszystkie bufory.

## <a name="syntax"></a>Składnia

```C
int _flushall( void );
```

## <a name="return-value"></a>Wartość zwracana

**_flushall** zwraca liczbę otwartych strumieni (wejściowych i wyjściowych). Brak powrotu błędu.

## <a name="remarks"></a>Uwagi

Domyślnie funkcja **_flushall** zapisuje do odpowiednich plików zawartość wszystkich buforów skojarzonych z otwartymi strumieniami wyjściowymi. Wszystkie bufory skojarzone z otwartymi strumieniami wejściowymi są usuwane z ich bieżącej zawartości. (Te bufory są zwykle obsługiwane przez system operacyjny, który określa optymalny czas zapisywania danych na dysku: gdy bufor jest pełny, gdy strumień jest zamknięty lub gdy program kończy normalne działanie bez zamykania strumieni).

Jeśli odczyt następuje po wywołaniu **_flushall**, nowe dane są odczytywane z plików wejściowych do buforów. Wszystkie strumienie pozostają otwarte po wywołaniu do **_flushall**.

Funkcja zatwierdzania na dysku w bibliotece wykonawczej pozwala zagwarantować, że krytyczne dane są zapisywane bezpośrednio na dysku, a nie w buforach systemu operacyjnego. Bez ponownego zapisywania istniejącego programu można włączyć tę funkcję, łącząc pliki obiektów programu z towarami. obj. W utworzonym pliku wykonywalnym program wywołuje **_flushall** zapisać zawartość wszystkich buforów na dysku. Tylko **_flushall** i [fflush](fflush.md) mają wpływ na towary. obj.

Aby uzyskać informacje o kontrolowaniu funkcji "Commit-to-Disk", zobacz [przesyłanie strumieniowe we/wy](../../c-runtime-library/stream-i-o.md), [fopen](fopen-wfopen.md)i [_fdopen](fdopen-wfdopen.md).

Domyślnie globalny stan tej funkcji jest objęty zakresem aplikacji. Aby to zmienić, zobacz [stan globalny w CRT](../global-state.md).

## <a name="requirements"></a>Wymagania

|Funkcja|Wymagany nagłówek|
|--------------|---------------------|
|**_flushall**|\<stdio. h>|

Aby uzyskać więcej informacji o zgodności, zobacz [zgodność](../../c-runtime-library/compatibility.md).

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
