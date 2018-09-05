---
title: RAND | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 1/02/2018
ms.technology:
- cpp-standard-libraries
ms.topic: reference
apiname:
- rand
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
- api-ms-win-crt-utility-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- rand
dev_langs:
- C++
helpviewer_keywords:
- generating pseudorandom numbers
- random numbers, generating
- numbers, pseudorandom
- rand function
- pseudorandom numbers
- numbers, generating pseudorandom
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 081e380dc639ed6a814913dd42c6fc1b55041b01
ms.sourcegitcommit: a7046aac86f1c83faba1088c80698474e25fe7c3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/04/2018
ms.locfileid: "43681138"
---
# <a name="rand"></a>rand

Generuje numer pseudolosowych przy użyciu algorytmu dobrze znanych i w pełni odtworzenia. Więcej programowo bezpiecznego wersja tej funkcji jest dostępna; zobacz [rand_s —](rand-s.md). Kody generowane przez **rand** nie są kryptograficznie bezpieczne. Generowanie liczby losowej więcej zabezpieczone kryptograficznie, użyj [rand_s —](rand-s.md) lub funkcji zadeklarowanych w standardowej bibliotece języka C++ w [ \<losowy >](../../standard-library/random.md).

## <a name="syntax"></a>Składnia

```C
int rand( void );
```

## <a name="return-value"></a>Wartość zwracana

**RAND** zwraca liczbę pseudolosowych, zgodnie z opisem powyżej. Nie będzie zwrotu błędu.

## <a name="remarks"></a>Uwagi

**Rand** funkcja zwraca pseudolosowych liczbę całkowitą z zakresu od 0 do **RAND_MAX** (32767). Użyj [srand —](srand.md) funkcji, aby zainicjować generatora liczb pseudolosowych przed wywołaniem **rand**.

**Rand** funkcja generuje sekwencję dobrze znanych i nie jest przeznaczone do użycia w funkcji kryptograficznych. Generowanie liczby losowej więcej zabezpieczone kryptograficznie, użyj [rand_s —](rand-s.md) lub funkcji zadeklarowanych w standardowej bibliotece języka C++ w [ \<losowy >](../../standard-library/random.md). Aby uzyskać informacje o problem z **rand** i w jaki sposób \<losowy > adresy te wad, zobacz ten film wideo, mają prawo [rand uznawane za szkodliwe](https://channel9.msdn.com/Events/GoingNative/2013/rand-Considered-Harmful).

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|
|-------------|---------------------|
|**rand**|\<stdlib.h>|

Aby uzyskać dodatkowe informacje o zgodności, zobacz [zgodności](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Przykład

```C
// crt_rand.c
// This program seeds the random-number generator
// with the time, then exercises the rand function.
//

#include <stdlib.h>
#include <stdio.h>
#include <time.h>

void SimpleRandDemo( int n )
{
   // Print n random numbers.
   int i;
   for( i = 0; i < n; i++ )
      printf( "  %6d\n", rand() );
}

void RangedRandDemo( int range_min, int range_max, int n )
{
   // Generate random numbers in the half-closed interval
   // [range_min, range_max). In other words,
   // range_min <= random number < range_max
   int i;
   for ( i = 0; i < n; i++ )
   {
      int u = (double)rand() / (RAND_MAX + 1) * (range_max - range_min)
            + range_min;
      printf( "  %6d\n", u);
   }
}

int main( void )
{
   // Seed the random-number generator with the current time so that
   // the numbers will be different every time we run.
   srand( (unsigned)time( NULL ) );

   SimpleRandDemo( 10 );
   printf("\n");
   RangedRandDemo( -100, 100, 10 );
}
```

```Output
22036
18330
11651
27464
18093
3284
11785
14686
11447
11285

   74
   48
   27
   65
   96
   64
   -5
  -42
  -55
   66
```

## <a name="see-also"></a>Zobacz także

[Obsługa liczb zmiennoprzecinkowych](../../c-runtime-library/floating-point-support.md)<br/>
[srand](srand.md)<br/>
[rand_s](rand-s.md)<br/>
