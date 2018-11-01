---
title: _onexit, _onexit_m
ms.date: 11/04/2016
apiname:
- _onexit
- _onexit_m
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
apitype: DLLExport
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
ms.openlocfilehash: c190f777032904802f771bab9fc323ba305ff32e
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50609611"
---
# <a name="onexit-onexitm"></a>_onexit, _onexit_m

Rejestruje procedury wywoływanej w momencie zakończenia.

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

*— Funkcja*<br/>
Wskaźnik do funkcji ma być wywoływana przy wyjściu.

## <a name="return-value"></a>Wartość zwracana

**_onexit** zwraca wskaźnik do funkcji, jeśli kończy się pomyślnie lub **NULL** Jeśli nie ma już miejsca do przechowywania wskaźnik funkcji.

## <a name="remarks"></a>Uwagi

**_Onexit** funkcji jest przekazywany adresu funkcji (*funkcja*) wywoływana, gdy program zakończy się normalnie. Kolejne wywołania **_onexit** tworzenia rejestru funkcji, które zostały wykonane w porządku LIFO (ostatni wejściu — pierwszy na wyjściu). Funkcje przekazane do **_onexit** nie przyjmuje parametrów.

W przypadku podczas **_onexit** jest wywoływana z w ramach biblioteki DLL, zarejestrowane przy użyciu procedury **_onexit** wykonywania dla biblioteki DLL przez zwalnianie po **DllMain** jest wywoływana z komunikat DLL_PROCESS_DETACH.

**_onexit** jest rozszerzeniem firmy Microsoft. Przenośność kodowania ANSI, można użyć [atexit](atexit.md). **_Onexit_m** wersja tej funkcji jest przeznaczona do użytku w trybie mieszanym.

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|
|-------------|---------------------|
|**_onexit**|\<stdlib.h>|

Aby uzyskać więcej informacji na temat zgodności, zobacz [zgodności](../../c-runtime-library/compatibility.md).

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
