---
title: zegar | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apiname: clock
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
f1_keywords: clock
dev_langs: C++
helpviewer_keywords:
- processor time used, calculating
- time, calculating processor
- clock function
- processor time used
- calculating processor time used
ms.assetid: 3e1853dd-498f-49ba-b06a-f2315f20904e
caps.latest.revision: "15"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 7e48d06b3170da0ded81473affec957f3eae0e3c
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="clock"></a>zegar
Oblicza czasu zegara wall używany przez proces wywoływania.  
  
## <a name="syntax"></a>Składnia  
  
```  
clock_t clock( void );  
```  
  
## <a name="return-value"></a>Wartość zwracana  
Czas, który upłynął od Inicjalizacja CRT na początku procesu, mierzony w `CLOCKS_PER_SEC` jednostkach na sekundę. Jeśli czas, który jest niedostępny lub przekroczyła maksymalny czas dodatnią, które mogą być rejestrowane jako `clock_t` typu, funkcja zwraca wartość `(clock_t)(-1)`.   
  
## <a name="remarks"></a>Uwagi  
`clock` Funkcja informuje zegara wall czas, jaki upłynął od Inicjalizacja CRT podczas uruchamiania procesu. Należy pamiętać, że ta funkcja jest ściśle niezgodny ze ISO C, który określa czas procesora CPU netto jako wartości zwracane. Aby uzyskać czas procesora CPU, użyj środowiska Win32 [GetProcessTimes](https://msdn.microsoft.com/library/windows/desktop/ms683223) funkcji. Aby określić czas w sekundach, Podziel wartość zwrócona przez `clock` funkcja przez makro `CLOCKS_PER_SEC`.  
  
Mając wystarczająco dużo czasu, wartość zwracana przez `clock` może być dłuższa niż maksymalna wartość dodatnią `clock_t`. Podczas procesu dysponuje już, wartość zwracana przez `clock` jest zawsze `(clock_t)(-1)`, zgodnie z określonym standardu ISO C99 (7.23.2.1) i standard ISO C11 (7.27.2.1). Implementuje Microsoft `clock_t` jako `long`, całkowita 32-bitowa i `CLOCKS_PER_SEC` makro jest zdefiniowany jako 1000. Dzięki temu maksymalnie `clock` funkcji zwracana wartość 2147483.647 sekund lub około 24.8 dni. Nie należy polegać na wartość zwrócona przez `clock` w procesach, które zostało uruchomione przez dłużej niż ta ilość czasu. Można użyć 64-bitowych `time` funkcji lub systemu Windows [QueryPerformanceCounter](https://msdn.microsoft.com/library/windows/desktop/ms644904) funkcji czas przetwarzania rekordów wiele lat.  

## <a name="requirements"></a>Wymagania  
  
|Procedura|Wymagany nagłówek|  
|-------------|---------------------|  
|`clock`|\<Time.h >|  
  
 Aby uzyskać dodatkowe informacje o zgodności, zobacz [zgodności](../../c-runtime-library/compatibility.md) we wprowadzeniu.  
  
## <a name="example"></a>Przykład  
  
```  
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
  
## <a name="see-also"></a>Zobacz też  
 [Zarządzanie czasem](../../c-runtime-library/time-management.md)   
 [difftime —, _difftime32 —, _difftime64 —](../../c-runtime-library/reference/difftime-difftime32-difftime64.md)   
 [time, _time32, _time64](../../c-runtime-library/reference/time-time32-time64.md)