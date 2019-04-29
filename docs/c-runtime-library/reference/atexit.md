---
title: atexit
ms.date: 11/04/2016
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
helpviewer_keywords:
- processing, at exit
- atexit function
ms.assetid: 92c156d2-8052-4e58-96dc-00128baac6f9
ms.openlocfilehash: 48f0fbfa1f3350f73899fcdbb3bf7922f1c6174d
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62341590"
---
# <a name="atexit"></a>atexit

Przetwarza określona funkcja przy wyjściu.

## <a name="syntax"></a>Składnia

```C
int atexit(
   void (__cdecl *func )( void )
);
```

### <a name="parameters"></a>Parametry

*FUNC*<br/>
Funkcja do wywołania.

## <a name="return-value"></a>Wartość zwracana

**atexit** zwraca 0 w przypadku powodzenia lub wartość różną od zera, jeśli wystąpi błąd.

## <a name="remarks"></a>Uwagi

**Atexit** funkcji jest przekazywany adresu funkcji *func* wywoływana, gdy program zakończy się normalnie. Kolejne wywołania **atexit** tworzenia rejestru funkcji, które zostały wykonane w porządku FIFO (LIFO) — ostatni na wejściu,. Funkcje przekazane do **atexit** nie przyjmuje parametrów. **atexit** i **_onexit** umożliwia przechowywania rejestru funkcje sterty. W związku z tym liczbę funkcji, które mogą być rejestrowane jest jedynym ograniczeniem pamięć sterty.

Kod w **atexit** funkcji nie może zawierać żadnych zależności na dowolną biblioteką DLL, która może już zostały usunięte podczas **atexit** funkcja jest wywoływana.

Aby wygenerować aplikację ze standardem ANSI, użyj standardu ANSI **atexit** — funkcja (zamiast podobny **_onexit** funkcji).

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|
|-------------|---------------------|
|**atexit**|\<stdlib.h>|

## <a name="example"></a>Przykład

Ten program wypchnięć czterech funkcji na stosie funkcji do wykonania, gdy **atexit** jest wywoływana. Gdy program jest zamykany, te programy są wykonywane w ostatni na wejściu, pierwszy się.

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
