---
title: atexit — | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
apiname:
- atexit
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
- atexit
dev_langs:
- C++
helpviewer_keywords:
- processing, at exit
- atexit function
ms.assetid: 92c156d2-8052-4e58-96dc-00128baac6f9
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: d66954348d5d812fac7eca0b231304267cc26157
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
---
# <a name="atexit"></a>atexit

Przetwarza określona funkcja na wyjściu.

## <a name="syntax"></a>Składnia

```C
int atexit(
   void (__cdecl *func )( void )
);
```

### <a name="parameters"></a>Parametry

*FUNC*<br/>
Funkcja wywoływana.

## <a name="return-value"></a>Wartość zwracana

**atexit —** zwraca 0 w przypadku powodzenia lub wartość różną od zera, jeśli wystąpi błąd.

## <a name="remarks"></a>Uwagi

**Atexit —** funkcji została przekazana adresu funkcji *func* wywoływana, gdy program zakończy się normalnie. Kolejne wywołania **atexit —** tworzenia rejestru funkcje, które są wykonywane w ostatniej, w kolejności wytworzenia. Funkcje przekazany do **atexit —** nie może mieć parametrów. **atexit —** i **_onexit —** użyć sterty do przechowywania rejestru funkcji. W związku z tym liczbę funkcji, które można zarejestrować jest ograniczona tylko przez pamięci sterty.

Kod w **atexit —** funkcja nie może zawierać żadnych zależności od każdej biblioteki DLL, która może już zostać usunięty z pamięci podczas **atexit —** funkcja jest wywoływana.

Aby wygenerować standardem ANSI aplikacji, należy użyć standardu ANSI **atexit —** — funkcja (zamiast podobne **_onexit —** funkcji).

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|
|-------------|---------------------|
|**atexit**|\<stdlib.h>|

## <a name="example"></a>Przykład

Ten program wypchnięć czterech funkcji na stosie funkcji ma być wykonywana po **atexit —** jest wywoływana. Gdy program jest kończona, te programy są wykonywane na ostatnich, najpierw się.

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
