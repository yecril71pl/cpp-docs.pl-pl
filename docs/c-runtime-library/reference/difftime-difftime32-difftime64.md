---
title: difftime, _difftime32, _difftime64
ms.date: 4/2/2020
api_name:
- _difftime32
- difftime
- _difftime64
- _o__difftime32
- _o__difftime64
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
- api-ms-win-crt-time-l1-1-0.dll
- api-ms-win-crt-private-l1-1-0
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- _difftime64
- difftime
- difftime64
- _difftime32
- difftime32
helpviewer_keywords:
- _difftime32 function
- difftime function
- time, finding the difference
- difftime64 function
- _difftime64 function
- difftime32 function
ms.assetid: 4cc0ac2b-fc7b-42c0-8283-8c9d10c566d0
ms.openlocfilehash: e2573f0bd5120796c0185c4dafe2699f8ceaae29
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81348130"
---
# <a name="difftime-_difftime32-_difftime64"></a>difftime, _difftime32, _difftime64

Znajduje różnicę między dwa razy.

## <a name="syntax"></a>Składnia

```C
double difftime( time_t timeEnd, time_t timeStart );
double _difftime32( __time32_t timeEnd, __time32_t timeStart );
double _difftime64( __time64_t timeEnd, __time64_t timeStart );
```

### <a name="parameters"></a>Parametry

*timeEnd (limit czasu)*<br/>
Czas zakończenia.

*timeStart*<br/>
Czas rozpoczęcia.

## <a name="return-value"></a>Wartość zwracana

**difftime** zwraca czas, jaki upłynął w sekundach, od *timeStart* do *timeEnd*. Zwracana wartość jest podwójną precyzją liczby zmiennoprzecinkowej. Zwracana wartość może wynosić 0, co oznacza błąd.

## <a name="remarks"></a>Uwagi

Funkcja **difftime** oblicza różnicę między dwiema podanymi wartościami czasu *timeStart* i *timeEnd*.

Podana wartość czasu musi mieścić się w zakresie **time_t**. **time_t** jest wartością 64-bitową. W ten sposób, koniec zakresu został przedłużony z 23:59:59 18 stycznia 2038, UTC do 23:59:59, 31 grudnia 3000. Dolny zakres **time_t** jest jeszcze północ, 1 stycznia 1970.

**difftime** jest funkcją wbudowaną, która ocenia **_difftime32** lub **_difftime64** w zależności od tego, czy **_USE_32BIT_TIME_T** jest zdefiniowany. _difftime32 i _difftime64 mogą być używane bezpośrednio do wymuszania użycia określonego rozmiaru typu czasu.

Te funkcje sprawdzają ich parametry. Jeśli którykolwiek z parametrów jest zerowy lub ujemny, wywoływany jest nieprawidłowy program obsługi parametrów, zgodnie z opisem w obszarze [Sprawdzanie poprawności parametrów.](../../c-runtime-library/parameter-validation.md) Jeśli wykonanie jest dozwolone, te funkcje zwracają 0 i ustawić **errno** do **EINVAL**.

Domyślnie stan globalny tej funkcji jest ograniczony do aplikacji. Aby to zmienić, zobacz [Stan globalny w crt](../global-state.md).

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|
|-------------|---------------------|
|**difftime**|\<> time.h|
|**_difftime32**|\<> time.h|
|**_difftime64**|\<> time.h|

Aby uzyskać dodatkowe informacje o zgodności, zobacz [Zgodność](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Przykład

```cpp
// crt_difftime.c
// This program calculates the amount of time
// needed to do a floating-point multiply 100 million times.
//

#include <stdio.h>
#include <stdlib.h>
#include <time.h>
#include <float.h>

double RangedRand( float range_min, float range_max)
{
   // Generate random numbers in the half-closed interval
   // [range_min, range_max). In other words,
   // range_min <= random number < range_max
   return ((double)rand() / (RAND_MAX + 1) * (range_max - range_min)
            + range_min);
}

int main( void )
{
   time_t   start, finish;
   long     loop;
   double   result, elapsed_time;
   double   arNums[3];

   // Seed the random-number generator with the current time so that
   // the numbers will be different every time we run.
   srand( (unsigned)time( NULL ) );

   arNums[0] = RangedRand(1, FLT_MAX);
   arNums[1] = RangedRand(1, FLT_MAX);
   arNums[2] = RangedRand(1, FLT_MAX);
   printf( "Using floating point numbers %.5e %.5e %.5e\n", arNums[0], arNums[1], arNums[2] );

   printf( "Multiplying 2 numbers 100 million times...\n" );

   time( &start );
   for( loop = 0; loop < 100000000; loop++ )
      result = arNums[loop%3] * arNums[(loop+1)%3];
   time( &finish );

   elapsed_time = difftime( finish, start );
   printf( "\nProgram takes %6.0f seconds.\n", elapsed_time );
}
```

```Output
Using random floating point numbers 1.04749e+038 2.01482e+038 1.72737e+038
Multiplying 2 floating point numbers 100 million times...
Program takes      3 seconds.
```

## <a name="see-also"></a>Zobacz też

[Obsługa zmiennoprzecinkowej](../../c-runtime-library/floating-point-support.md)<br/>
[Zarządzanie czasem](../../c-runtime-library/time-management.md)<br/>
[time, _time32, _time64](time-time32-time64.md)<br/>
