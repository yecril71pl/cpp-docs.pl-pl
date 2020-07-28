---
title: zegar
ms.date: 11/04/2016
api_name:
- clock
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
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- clock
helpviewer_keywords:
- processor time used, calculating
- time, calculating processor
- clock function
- processor time used
- calculating processor time used
ms.assetid: 3e1853dd-498f-49ba-b06a-f2315f20904e
ms.openlocfilehash: 03d1a9ece92dbedfdceb89488e5d0440dc64f7ae
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/27/2020
ms.locfileid: "87220733"
---
# <a name="clock"></a>zegar

Oblicza Czas zegarowy używany przez proces wywołujący.

## <a name="syntax"></a>Składnia

```C
clock_t clock( void );
```

## <a name="return-value"></a>Wartość zwracana

Czas, który upłynął od momentu inicjalizacji CRT na początku procesu, mierzony w **CLOCKS_PER_SEC** jednostkach na sekundę. Jeśli czas, który upłynął, jest niedostępny lub przekroczy maksymalny czas pozytywny, który można zarejestrować jako typ **clock_t** , funkcja zwraca wartość `(clock_t)(-1)` .

## <a name="remarks"></a>Uwagi

Funkcja **Clock** informuje, ile czasu zegar ściany został zakończony od momentu inicjalizacji CRT podczas uruchamiania procesu. Należy zauważyć, że ta funkcja nie jest ściśle zgodna z normą ISO C, która określa czas procesora CPU jako wartość zwracaną. Aby uzyskać czasy procesora, użyj funkcji Win32 [GetProcessTimes](/windows/win32/api/processthreadsapi/nf-processthreadsapi-getprocesstimes) . Aby określić czas (w sekundach), należy podzielić wartość zwróconą przez funkcję **zegara** przez makro **CLOCKS_PER_SEC**.

Mając wystarczająco dużo czasu, wartość zwracana przez **zegar** może przekroczyć maksymalną wartość dodatnią **clock_t**. Gdy proces ma więcej czasu, wartość zwracana przez **zegar** jest zawsze `(clock_t)(-1)` określona przez standard ISO C99 Standard (7.23.2.1) i ISO C11 (7.27.2.1). Firma Microsoft implementuje **clock_t** w postaci **`long`** podpisanej 32-bitowej liczby całkowitej, a makro **CLOCKS_PER_SEC** jest zdefiniowane jako 1000. Dzięki temu maksymalna wartość **zegara** jest zwracana przez 2147483,647 sekund lub około 24,8 dni. Nie należy polegać na wartości zwracanej przez **zegar** w procesach, które są wykonywane dłużej niż ten czas. Można użyć funkcji [czasu](time-time32-time64.md) 64-bitowego lub funkcji [QueryPerformanceCounter](/windows/win32/api/profileapi/nf-profileapi-queryperformancecounter) systemu Windows, aby nagrać czas, który upłynął przez wiele lat.

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|
|-------------|---------------------|
|**zegar**|\<time.h>|

Aby uzyskać dodatkowe informacje o zgodności, zobacz [zgodność](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Przykład

```C
// crt_clock.c
// This sample uses clock() to 'sleep' for three
// seconds, then determines how long it takes
// to execute an empty loop 600000000 times.

#include <stdio.h>
#include <stdlib.h>
#include <time.h>

// Pauses for a specified number of clock cycles.
void do_sleep( clock_t wait )
{
   clock_t goal;
   goal = wait + clock();
   while( goal > clock() )
      ;
}

const long num_loops = 600000000L;

int main( void )
{
   long    i = num_loops;
   clock_t start, finish;
   double  duration;

   // Delay for a specified time.
   printf( "Delay for three seconds\n" );
   do_sleep( (clock_t)3 * CLOCKS_PER_SEC );
   printf( "Done!\n" );

   // Measure the duration of an event.
   start = clock();
   while( i-- )
      ;
   finish = clock();
   duration = (double)(finish - start) / CLOCKS_PER_SEC;
   printf( "Time to do %ld empty loops is ", num_loops );
   printf( "%2.3f seconds\n", duration );
}
```

```Output
Delay for three seconds
Done!
Time to do 600000000 empty loops is 1.354 seconds
```

## <a name="see-also"></a>Zobacz także

[Zarządzanie czasem](../../c-runtime-library/time-management.md)<br/>
[difftime, _difftime32, _difftime64](difftime-difftime32-difftime64.md)<br/>
[time, _time32, _time64](time-time32-time64.md)<br/>
