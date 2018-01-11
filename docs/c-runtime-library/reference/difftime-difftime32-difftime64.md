---
title: "difftime —, _difftime32 —, _difftime64 — | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- _difftime32
- difftime
- _difftime64
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
- _difftime64
- difftime
- difftime64
- _difftime32
- difftime32
dev_langs: C++
helpviewer_keywords:
- _difftime32 function
- difftime function
- time, finding the difference
- difftime64 function
- _difftime64 function
- difftime32 function
ms.assetid: 4cc0ac2b-fc7b-42c0-8283-8c9d10c566d0
caps.latest.revision: "21"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 1dd1849b212871db05dcab85111ece7d2a98fc57
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="difftime-difftime32-difftime64"></a>difftime, _difftime32, _difftime64
Znajduje różnicę między dwiema wartościami godziny.  
  
## <a name="syntax"></a>Składnia  
  
```  
double difftime(   
   time_t timer1,  
   time_t timer0   
);  
double _difftime32(   
   __time32_t timer1,  
   __time32_t timer0   
);  
double _difftime64(   
   __time64_t timer1,  
   __time64_t timer0   
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `timer1`  
 Godzina zakończenia.  
  
 `timer0`  
 Godzina rozpoczęcia.  
  
## <a name="return-value"></a>Wartość zwracana  
 `difftime`Zwraca czas w sekundach, z `timer0` do `timer1`. Wartość zwracana jest liczba zmiennoprzecinkowa podwójnej precyzji. Wartość zwracana może być 0, co wskazuje na błąd.  
  
## <a name="remarks"></a>Uwagi  
 `difftime` Funkcja oblicza różnicę między dwiema wartościami godziny podane `timer0` i `timer1`.  
  
 Podana wartość czasu musi mieścić się w zakresie `time_t`. `time_t`jest to wartość 64-bitowych. W związku z tym końca zakresu został rozszerzony z 23:59:59 18 stycznia 2038 r., UTC do 23:59:59 31 grudnia 3000. Dolna granica z `time_t` jest nadal północy, 1 stycznia 1970.  
  
 `difftime`jest obliczane jednej wbudowanej funkcji `_difftime32` lub `_difftime64` w zależności od tego, czy `_USE_32BIT_TIME_T` jest zdefiniowany. _difftime32 — i _difftime64 — można bezpośrednio, aby wymusić użycie określonego rozmiaru typu time.  
  
 Te funkcje walidację ich parametrów. Jeśli wartość parametrów wynosi zero lub ujemne, program obsługi nieprawidłowych parametrów zostanie wywołany, zgodnie z opisem w [sprawdzanie poprawności parametru](../../c-runtime-library/parameter-validation.md). Jeśli wykonanie może kontynuować, funkcje zwracają 0 i ustaw `errno` do `EINVAL`.  
  
## <a name="requirements"></a>Wymagania  
  
|Procedura|Wymagany nagłówek|  
|-------------|---------------------|  
|`difftime`|\<Time.h >|  
|`_difftime32`|\<Time.h >|  
|`_difftime64`|\<Time.h >|  
  
 Aby uzyskać dodatkowe informacje o zgodności, zobacz [zgodności](../../c-runtime-library/compatibility.md) we wprowadzeniu.  
  
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
Using random floating point numbers 1.04749e+038 2.01482e+038 1.72737e+038Multiplying 2 floating point numbers 100 million times...Program takes      3 seconds.Multiplying 2 floating point numbers 500 million times...  
  
Program takes      5 seconds.  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Obsługa liczb zmiennoprzecinkowych](../../c-runtime-library/floating-point-support.md)   
 [Zarządzanie czasem](../../c-runtime-library/time-management.md)   
 [time, _time32, _time64](../../c-runtime-library/reference/time-time32-time64.md)