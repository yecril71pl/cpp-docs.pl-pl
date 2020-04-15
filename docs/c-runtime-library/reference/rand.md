---
title: rand
ms.date: 4/2/2020
api_name:
- rand
- _o_rand
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
- api-ms-win-crt-utility-l1-1-0.dll
- ntoskrnl.exe
- api-ms-win-crt-private-l1-1-0
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- rand
helpviewer_keywords:
- generating pseudorandom numbers
- random numbers, generating
- numbers, pseudorandom
- rand function
- pseudorandom numbers
- numbers, generating pseudorandom
ms.openlocfilehash: 944c512d0102b459afc2924ef7515311e46cd43c
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81338160"
---
# <a name="rand"></a>rand

Generuje numer pseudolosowy przy użyciu dobrze znanego i w pełni powtarzalnego algorytmu. Dostępna jest bardziej programowo bezpieczna wersja tej funkcji; patrz [rand_s](rand-s.md). Liczby generowane przez **rand** nie są zabezpieczone kryptograficznie. Aby uzyskać bardziej kryptograficznie bezpieczne generowanie liczb losowych, użyj [rand_s](rand-s.md) lub funkcji zadeklarowanych w standardowej bibliotece C++ w [ \<losowych>](../../standard-library/random.md).

## <a name="syntax"></a>Składnia

```C
int rand( void );
```

## <a name="return-value"></a>Wartość zwracana

**rand** zwraca numer pseudolosowy, jak opisano powyżej. Nie ma zwracania błędów.

## <a name="remarks"></a>Uwagi

Funkcja **rand** zwraca liczbę całkowitą pseudolosową w zakresie od 0 do **RAND_MAX** (32767). Użyj funkcji [srand](srand.md) do nasion pseudolosdom-generator liczb przed wywołaniem **rand**.

Funkcja **rand** generuje dobrze znaną sekwencję i nie jest odpowiednia do użycia jako funkcja kryptograficzna. Aby uzyskać bardziej kryptograficznie bezpieczne generowanie liczb losowych, użyj [rand_s](rand-s.md) lub funkcji zadeklarowanych w standardowej bibliotece C++ w [ \<losowych>](../../standard-library/random.md). Aby uzyskać informacje o **rand** tym, \<co jest nie tak z rand i jak losowe> rozwiązuje te niedociągnięcia, zobacz ten film zatytułowany [rand Uważane za szkodliwe](https://channel9.msdn.com/Events/GoingNative/2013/rand-Considered-Harmful).

Domyślnie stan globalny tej funkcji jest ograniczony do aplikacji. Aby to zmienić, zobacz [Stan globalny w crt](../global-state.md).

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|
|-------------|---------------------|
|**Rand**|\<>|

Aby uzyskać dodatkowe informacje o zgodności, zobacz [Zgodność](../../c-runtime-library/compatibility.md).

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

## <a name="see-also"></a>Zobacz też

[Obsługa zmiennoprzecinkowej](../../c-runtime-library/floating-point-support.md)<br/>
[srand](srand.md)<br/>
[rand_s](rand-s.md)<br/>
