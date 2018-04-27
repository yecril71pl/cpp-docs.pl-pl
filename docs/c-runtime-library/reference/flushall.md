---
title: _flushall — | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: ''
ms.topic: reference
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
dev_langs:
- C++
helpviewer_keywords:
- flushall function
- flushing streams
- streams, flushing
- _flushall function
ms.assetid: 2cd73562-6d00-4ca2-b13c-80d0ae7870b5
caps.latest.revision: 16
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 936a0c4c18b36c490f0edfeefa651e21c017e1fc
ms.sourcegitcommit: ef859ddf5afea903711e36bfd89a72389a12a8d6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/20/2018
---
# <a name="flushall"></a>_flushall

Czyści wszystkie strumienie; Czyści wszystkie bufory.

## <a name="syntax"></a>Składnia

```C
int _flushall( void );
```

## <a name="return-value"></a>Wartość zwracana

**_flushall —** zwraca liczbę otwartych strumieni (dane wejściowe i wyjściowe). Nie ma żadnych zwracany błąd.

## <a name="remarks"></a>Uwagi

Domyślnie **_flushall —** funkcja zapisuje odpowiednią zawartość buforów wszystkie skojarzone z strumienie wyjściowe otwarte pliki. Wszystkie bufory skojarzone z otwartych strumienie wejściowe są usuwane z ich bieżącej zawartości. (Bufory są zazwyczaj obsługiwane przez system operacyjny, który określa czas optymalnego automatycznie zapisać danych na dysku: gdy bufor jest pełny, gdy strumień jest zamknięty lub gdy program kończy się zwykle bez zamykania strumieni.)

Jeśli odczytu następuje po wywołaniu **_flushall —**, nowe dane są odczytywane z plików wejściowych do buforów. Wszystkie strumienie pozostają otwarte po wywołaniu **_flushall —**.

Funkcja commit-to-disk biblioteki wykonawczej umożliwia upewnij się, że krytyczne dane są zapisywane bezpośrednio na dysku, a nie do buforów systemu operacyjnego. Bez ponowne zapisywanie istniejący program, łącząc plików obiektów programu z Commode.obj można włączyć tę funkcję. W wynikowym pliku wykonywalnego, wywołań **_flushall —** zapisać zawartość buforów wszystkich na dysku. Tylko **_flushall —** i [fflush —](fflush.md) dotyczy Commode.obj.

Aby uzyskać informacje na temat funkcji commit-to-disk, zobacz [strumień we/wy](../../c-runtime-library/stream-i-o.md), [fopen —](fopen-wfopen.md), i [_fdopen —](fdopen-wfdopen.md).

## <a name="requirements"></a>Wymagania

|Funkcja|Wymagany nagłówek|
|--------------|---------------------|
|**_flushall**|\<stdio.h>|

Aby uzyskać więcej informacji o zgodności, zobacz [zgodności](../../c-runtime-library/compatibility.md).

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

[We/Wy strumienia](../../c-runtime-library/stream-i-o.md)<br/>
[_commit](commit.md)<br/>
[fclose, _fcloseall](fclose-fcloseall.md)<br/>
[fflush](fflush.md)<br/>
[setvbuf](setvbuf.md)<br/>
