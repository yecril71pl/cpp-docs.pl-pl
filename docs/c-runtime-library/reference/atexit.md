---
title: atexit
ms.date: 11/04/2016
api_name:
- atexit
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
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- atexit
helpviewer_keywords:
- processing, at exit
- atexit function
ms.assetid: 92c156d2-8052-4e58-96dc-00128baac6f9
ms.openlocfilehash: b91e6dad81f006b0b94ac17a940e840386f6d2b1
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/12/2019
ms.locfileid: "70939659"
---
# <a name="atexit"></a>atexit

Przetwarza określoną funkcję przy zamykaniu.

## <a name="syntax"></a>Składnia

```C
int atexit(
   void (__cdecl *func )( void )
);
```

### <a name="parameters"></a>Parametry

*func*<br/>
Funkcja, która ma zostać wywołana.

## <a name="return-value"></a>Wartość zwracana

**atexit —** zwraca wartość 0, jeśli zakończyło się pomyślnie, lub o wartości niezerowej, jeśli wystąpi błąd.

## <a name="remarks"></a>Uwagi

Funkcja **atexit —** przekazuje adres funkcji *Func* do wywołania, gdy program kończy normalne działanie. Kolejne wywołania do **atexit —** umożliwiają utworzenie rejestru funkcji, które są wykonywane w kolejności od ostatniej do końca (LIFO). Funkcje przesłane do **atexit —** nie mogą przyjmować parametrów. **atexit —** i **_onexit** używają sterty do przechowywania rejestru funkcji. W ten sposób liczba funkcji, które mogą być rejestrowane, jest ograniczona tylko przez pamięć sterty.

Kod w funkcji **atexit —** nie powinien zawierać żadnej zależności od żadnej biblioteki DLL, która mogła zostać już zwolniona, gdy wywoływana jest funkcja **atexit —** .

Aby wygenerować aplikację zgodną ze standardem ANSI, należy użyć funkcji **atexit —** standard ANSI (zamiast podobnej funkcji **_onexit** ).

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|
|-------------|---------------------|
|**atexit**|\<stdlib.h>|

## <a name="example"></a>Przykład

Ten program umieszcza cztery funkcje na stosie funkcji, które mają zostać wykonane po wywołaniu **atexit —** . Po zakończeniu działania programu te programy są wykonywane na ostatnim, a pierwszy z nich.

```C
// crt_atexit.c
#include <stdlib.h>
#include <stdio.h>

void fn1( void ), fn2( void ), fn3( void ), fn4( void );

int main( void )
{
   atexit( fn1 );
   atexit( fn2 );
   atexit( fn3 );
   atexit( fn4 );
   printf( "This is executed first.\n" );
}

void fn1()
{
   printf( "next.\n" );
}

void fn2()
{
   printf( "executed " );
}

void fn3()
{
   printf( "is " );
}

void fn4()
{
   printf( "This " );
}
```

```Output
This is executed first.
This is executed next.
```

## <a name="see-also"></a>Zobacz także

[Procedury kontroli środowiska](../../c-runtime-library/process-and-environment-control.md)<br/>
[abort](abort.md)<br/>
[exit, _Exit, _exit](exit-exit-exit.md)<br/>
[_onexit, _onexit_m](onexit-onexit-m.md)<br/>
