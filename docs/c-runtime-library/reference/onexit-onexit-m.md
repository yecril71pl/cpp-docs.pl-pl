---
title: _onexit —, _onexit_m — | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
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
dev_langs:
- C++
helpviewer_keywords:
- onexit function
- registry, registering exit routines
- _onexit_m function
- onexit_m function
- _onexit function
- registering exit routines
- registering to be called on exit
ms.assetid: 45743298-0e2f-46cf-966d-1ca44babb443
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 8c190ce2c78135625a502d7509e56771fd670aa3
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
ms.locfileid: "32401711"
---
# <a name="onexit-onexitm"></a>_onexit, _onexit_m

Rejestruje procedura ma być wywoływana w momencie zakończenia.

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

*Funkcja*<br/>
Wskaźnik do funkcję, która ma zostać wywołana w chwili zakończenia.

## <a name="return-value"></a>Wartość zwracana

**_onexit —** zwraca wskaźnik do funkcji w przypadku powodzenia lub **NULL** Jeśli brakuje miejsca do przechowywania wskaźnik funkcji.

## <a name="remarks"></a>Uwagi

**_Onexit —** funkcji została przekazana adresu funkcji (*funkcja*) wywoływana, gdy program zakończy się normalnie. Kolejne wywołania **_onexit —** tworzenia rejestru funkcje, które są wykonywane w kolejności LIFO (ostatnie — w pierwszej — ruch wychodzący). Funkcje przekazany do **_onexit —** nie może mieć parametrów.

W przypadku gdy **_onexit —** jest wywołana z poziomu biblioteki DLL, procedury zarejestrowana w usłudze **_onexit —** Uruchom na bibliotekę DLL na zwalnianie po **DllMain** jest wywoływana z komunikat DLL_PROCESS_DETACH.

**_onexit —** to rozszerzenie firmy Microsoft. Przenośności ANSI, użyj [atexit —](atexit.md). **_Onexit_m —** wersji funkcji jest przeznaczona do użytku w trybie mieszanym.

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|
|-------------|---------------------|
|**_onexit —**|\<stdlib.h>|

Aby uzyskać więcej informacji o zgodności, zobacz [zgodności](../../c-runtime-library/compatibility.md).

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
