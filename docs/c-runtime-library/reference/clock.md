---
title: zegar
ms.date: 11/04/2016
apiname:
- clock
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
- api-ms-win-crt-time-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- clock
helpviewer_keywords:
- processor time used, calculating
- time, calculating processor
- clock function
- processor time used
- calculating processor time used
ms.assetid: 3e1853dd-498f-49ba-b06a-f2315f20904e
ms.openlocfilehash: 4b58b33b533250447cf964134de9869bddee4498
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62347473"
---
# <a name="clock"></a>zegar

Oblicza czas zegarowy używany przez proces wywołujący.

## <a name="syntax"></a>Składnia

```C
clock_t clock( void );
```

## <a name="return-value"></a>Wartość zwracana

Czas, jaki upłynął od Inicjalizacja CRT na początku procesu, mierzone w **CLOCKS_PER_SEC** jednostkach na sekundę. Jeśli czas jest niedostępny lub został przekroczony maksymalny czas dodatnią, która może zostać zarejestrowana jako **clock_t** typu, funkcja zwraca wartość `(clock_t)(-1)`.

## <a name="remarks"></a>Uwagi

**Zegara** funkcja informuje, ile czasu zegarowego minęło od Inicjalizacja CRT podczas uruchamiania procesu. Należy pamiętać, że ta funkcja nie jest ściśle zgodny z C ISO, który określa czas procesora CPU netto jako wartość zwracaną. Aby uzyskać czas procesora CPU, użyj Win32 [GetProcessTimes](/windows/desktop/api/processthreadsapi/nf-processthreadsapi-getprocesstimes) funkcji. Aby określić czas w sekundach, Podziel wartość zwrócona przez obiekt **zegara** funkcji przez makro **CLOCKS_PER_SEC**.

Mając wystarczająco dużo czasu, wartość zwracana przez **zegara** może przekroczyć maksymalnej wartości dodatniej **clock_t**. Proces ma uruchamiania, wartość zwracana przez **zegara** jest zawsze `(clock_t)(-1)`, jak określono w normie ISO C99 (7.23.2.1) i standard ISO C11 (7.27.2.1). Firma Microsoft implementuje **clock_t** jako **długie**, całkowita 32-bitowa i **CLOCKS_PER_SEC** — makro jest zdefiniowany jako 1000. Dzięki temu maksymalnie **zegara** funkcji zwracana wartość 2147483.647 sekund lub około 24.8 dni. Nie należy polegać na wartość zwrócona przez obiekt **zegara** w procesach, które zostały uruchomione przez dłużej niż to ilość czasu. Można użyć 64-bitowego [czasu](time-time32-time64.md) funkcji lub Windows [QueryPerformanceCounter](https://msdn.microsoft.com/library/windows/desktop/ms644904) funkcję, aby czas przetwarzania rekordów wielu lat.

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|
|-------------|---------------------|
|**clock**|\<time.h>|

Aby uzyskać dodatkowe informacje o zgodności, zobacz [zgodności](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Przykład

```C
// crt_clock.c
// This sample uses clock() to 'sleep' for three
// seconds, then determines how long it takes
// to execute an empty loop 600000000 times.

#include <stdio.h>
#include <stdlib.h>
#include <time.h>

// Pauses for a specified number of milliseconds.
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
