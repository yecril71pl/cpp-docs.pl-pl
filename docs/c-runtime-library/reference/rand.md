---
title: rand
ms.date: 01/02/2018
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
- ntoskrnl.exe
apitype: DLLExport
f1_keywords:
- rand
helpviewer_keywords:
- generating pseudorandom numbers
- random numbers, generating
- numbers, pseudorandom
- rand function
- pseudorandom numbers
- numbers, generating pseudorandom
ms.openlocfilehash: 407640c5f00ae54c43450abcbbe8c2e3ba0fcf95
ms.sourcegitcommit: effb516760c0f956c6308eeded48851accc96b92
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/12/2019
ms.locfileid: "70927526"
---
# <a name="rand"></a>rand

Generuje numer pseudolosowych przy użyciu dobrze znanego i w pełni odtwarzalnego algorytmu. Dostępna jest bardziej programowo bezpieczna wersja tej funkcji; Zobacz [rand_s](rand-s.md). Liczby wygenerowane przez **Rand** nie są kryptograficznie zabezpieczone. Aby uzyskać bardziej kryptograficzną kryptograficznie funkcję generowania liczb losowych, użyj [rand_s](rand-s.md) lub funkcji zadeklarowanych w bibliotece C++ standardowej w [ \<losowo >](../../standard-library/random.md).

## <a name="syntax"></a>Składnia

```C
int rand( void );
```

## <a name="return-value"></a>Wartość zwracana

Funkcja **Rand** zwraca numer pseudolosowych, zgodnie z powyższym opisem. Brak powrotu błędu.

## <a name="remarks"></a>Uwagi

Funkcja **Rand** zwraca liczbę całkowitą pseudolosowych z zakresu od 0 do **RAND_MAX** (32767). Użyj funkcji [srand](srand.md) , aby wypełniać generatora numerów pseudolosowych przed wywołaniem funkcji **Rand**.

Funkcja **Rand** generuje dobrze znaną sekwencję i nie jest odpowiednia do użycia jako funkcja kryptograficzna. Aby uzyskać bardziej kryptograficzną kryptograficznie funkcję generowania liczb losowych, użyj [rand_s](rand-s.md) lub funkcji zadeklarowanych w bibliotece C++ standardowej w [ \<losowo >](../../standard-library/random.md). Aby uzyskać informacje o tym, co się stało z \<Los i jak losowo > eliminuje te nieprawidłowości, zobacz ten film wideo zatytułowany [Los uważany za szkodliwy](https://channel9.msdn.com/Events/GoingNative/2013/rand-Considered-Harmful).

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|
|-------------|---------------------|
|**rand**|\<stdlib.h>|

Aby uzyskać dodatkowe informacje o zgodności, zobacz [zgodność](../../c-runtime-library/compatibility.md).

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
