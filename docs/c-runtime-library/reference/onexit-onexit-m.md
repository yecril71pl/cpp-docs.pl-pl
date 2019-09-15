---
title: _onexit, _onexit_m
ms.date: 11/04/2016
api_name:
- _onexit
- _onexit_m
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
- _onexit
- onexit_m
- onexit
- _onexit_m
helpviewer_keywords:
- onexit function
- registry, registering exit routines
- _onexit_m function
- onexit_m function
- _onexit function
- registering exit routines
- registering to be called on exit
ms.assetid: 45743298-0e2f-46cf-966d-1ca44babb443
ms.openlocfilehash: 9afcd729f19f11b82e8f24c2b7fcf9ec40990deb
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/12/2019
ms.locfileid: "70951345"
---
# <a name="_onexit-_onexit_m"></a>_onexit, _onexit_m

Rejestruje procedurę, która ma zostać wywołana w czasie zakończenia.

## <a name="syntax"></a>Składnia

```C
_onexit_t _onexit(
   _onexit_t function
);
_onexit_t_m _onexit_m(
   _onexit_t_m function
);
```

### <a name="parameters"></a>Parametry

*funkcyjn*<br/>
Wskaźnik do funkcji, która ma zostać wywołana przy zamykaniu.

## <a name="return-value"></a>Wartość zwracana

**_onexit** zwraca wskaźnik do funkcji, jeśli jest powodzenie lub ma **wartość null** , jeśli nie ma miejsca na przechowywanie wskaźnika funkcji.

## <a name="remarks"></a>Uwagi

Funkcja **_onexit** przekazuje adres funkcji (*funkcji*), która ma być wywoływana, gdy program kończy normalne działanie. Kolejne wywołania do **_onexit** umożliwiają utworzenie rejestru funkcji, które są wykonywane w kolejności LIFO (Last-in-on-First-Out-on-in-in-in-in-in Funkcje przesłane do **_onexit** nie mogą przyjmować parametrów.

W przypadku gdy **_onexit** jest wywoływana z poziomu biblioteki DLL, procedury zarejestrowane przy użyciu **_onexit** są uruchamiane na wyładowaniu biblioteki DLL po wywołaniu **DllMain** z DLL_PROCESS_DETACH.

**_onexit** jest rozszerzeniem firmy Microsoft. W przypadku przenośności ANSI Użyj [atexit —](atexit.md). Wersja **_onexit_m** funkcji jest używana w trybie mieszanym.

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|
|-------------|---------------------|
|**_onexit**|\<stdlib.h>|

Aby uzyskać więcej informacji o zgodności, zobacz [zgodność](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Przykład

```C
// crt_onexit.c

#include <stdlib.h>
#include <stdio.h>

/* Prototypes */
int fn1(void), fn2(void), fn3(void), fn4 (void);

int main( void )
{
   _onexit( fn1 );
   _onexit( fn2 );
   _onexit( fn3 );
   _onexit( fn4 );
   printf( "This is executed first.\n" );
}

int fn1()
{
   printf( "next.\n" );
   return 0;
}

int fn2()
{
   printf( "executed " );
   return 0;
}

int fn3()
{
   printf( "is " );
   return 0;
}

int fn4()
{
   printf( "This " );
   return 0;
}
```

### <a name="output"></a>Dane wyjściowe

```Output
This is executed first.
This is executed next.
```

## <a name="see-also"></a>Zobacz także

[Procedury kontroli środowiska](../../c-runtime-library/process-and-environment-control.md)<br/>
[atexit](atexit.md)<br/>
[exit, _Exit, _exit](exit-exit-exit.md)<br/>
[__dllonexit](../../c-runtime-library/dllonexit.md)<br/>
