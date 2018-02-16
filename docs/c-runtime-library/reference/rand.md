---
title: RAND | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 1/02/2018
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
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
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 5fecd9079de1ae846d83847eb299890d62c29d17
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/14/2018
---
# <a name="rand"></a>rand

Generuje liczby pseudolosowe za pomocą algorytmu dobrze znanych i pełni odtworzenia. Więcej programowo bezpiecznego wersja ta funkcja jest dostępna; zobacz [rand_s —](../../c-runtime-library/reference/rand-s.md). Kody generowane przez `rand` nie są zabezpieczone kryptograficznie. Generowanie liczby losowej więcej zabezpieczone kryptograficznie, użyj `rand_s` lub zadeklarowany funkcje standardowej biblioteki C++ w [ \<losowe >](../../standard-library/random.md).

## <a name="syntax"></a>Składnia

```C
int rand( void );
```

## <a name="return-value"></a>Wartość zwracana

`rand` Zwraca liczbę pseudolosowych, jak opisano powyżej. Nie ma żadnych zwracany błąd.

## <a name="remarks"></a>Uwagi

`rand` Funkcja zwraca pseudolosowych liczbą całkowitą z zakresu od 0 do `RAND_MAX` (32767). Użyj [srand —](../../c-runtime-library/reference/srand.md) funkcji jako zalążek generatora liczby pseudolosowe przed wywołaniem `rand`.

`rand` Funkcji generuje dobrze znanego sekwencji i nie jest odpowiedni dla funkcji kryptograficznych. Generowanie liczby losowej więcej zabezpieczone kryptograficznie, użyj `rand_s` lub zadeklarowany funkcje standardowej biblioteki C++ w [ \<losowe >](../../standard-library/random.md). Aby uzyskać informacje o problem z `rand()` i w jaki sposób `<random>` dotyczy tych nieprawidłowości, zobacz [ten film](http://go.microsoft.com/fwlink/?LinkId=397615).

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|
|-------------|---------------------|
|`rand`|\<stdlib.h>|

Aby uzyskać dodatkowe informacje o zgodności, zobacz [zgodności](../../c-runtime-library/compatibility.md) we wprowadzeniu.

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

[Obsługa liczb zmiennoprzecinkowych](../../c-runtime-library/floating-point-support.md)  
[srand](../../c-runtime-library/reference/srand.md)  
[rand_s](../../c-runtime-library/reference/rand-s.md)  