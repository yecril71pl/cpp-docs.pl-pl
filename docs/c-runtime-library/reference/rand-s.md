---
title: "rand_s — | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apiname: rand_s
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
f1_keywords: rand_s
dev_langs: C++
helpviewer_keywords:
- generating pseudorandom numbers
- random numbers, cryptographically secure
- random numbers, generating
- rand_s function
- numbers, pseudorandom
- cryptographically secure random numbers
- pseudorandom numbers
- numbers, generating pseudorandom
ms.assetid: d6a0be60-997d-4904-8411-8aea6839cc94
caps.latest.revision: "24"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 4e11cb6db212efd9d7d250057782f8a135859616
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="rands"></a>rand_s
Generuje pseudolosowych numer. Wersja [rand](../../c-runtime-library/reference/rand.md) ulepszeń zabezpieczeń zgodnie z opisem w [funkcje zabezpieczeń w CRT](../../c-runtime-library/security-features-in-the-crt.md).  
  
## <a name="syntax"></a>Składnia  
  
```  
errno_t rand_s(   unsigned int* randomValue);  
```  
  
## <a name="return-value"></a>Wartość zwracana  
 Zero, jeśli to się powiedzie, w przeciwnym razie kod błędu. Jeśli wskaźnika wejścia `randomValue` jest wskaźnika o wartości null, funkcja wywołuje program obsługi nieprawidłowych parametrów, zgodnie z opisem w [sprawdzanie poprawności parametru](../../c-runtime-library/parameter-validation.md). Jeśli jest dozwolone wykonywanie, aby kontynuować, funkcja zwraca `EINVAL` i ustawia `errno` do `EINVAL`. Jeśli funkcja nie powiedzie się z jakiegokolwiek powodu *`randomValue` jest równa 0.  
  
## <a name="remarks"></a>Uwagi  
 `rand_s` Funkcja zapisuje pseudolosowych liczbą całkowitą z zakresu od 0 do `UINT_MAX` do wskaźnika wejścia. `rand_s` Funkcja używa systemu operacyjnego dla generatora liczb losowych kryptograficznie bezpieczne. Nie używa inicjatora generowane przez [srand —](../../c-runtime-library/reference/srand.md) funkcji, ani nie ogranicza losowe sekwencja używane przez `rand`.  
  
 `rand_s` Funkcja wymaga tej stałej `_CRT_RAND_S` można zdefiniować przed instrukcji włączenia funkcji zgłoszone, jak w poniższym przykładzie:  
  
```  
#define _CRT_RAND_S  
#include <stdlib.h>  
```  
  
 `rand_s`zależy od [RtlGenRandom](http://msdn.microsoft.com/library/windows/desktop/aa387694) interfejsu API, który jest tylko dostępne w systemie Windows XP lub nowszy.  
  
## <a name="requirements"></a>Wymagania  
  
|Procedura|Wymagany nagłówek|  
|-------------|---------------------|  
|`rand_s`|\<stdlib.h >|  
  
 Aby uzyskać więcej informacji, zobacz [zgodności](../../c-runtime-library/compatibility.md).  
  
## <a name="example"></a>Przykład  
  
```  
// crt_rand_s.c  
// This program illustrates how to generate random  
// integer or floating point numbers in a specified range.  
  
// Remembering to define _CRT_RAND_S prior  
// to inclusion statement.  
#define _CRT_RAND_S  
  
#include <stdlib.h>  
#include <stdio.h>  
#include <limits.h>  
  
int main( void )  
{  
    int             i;  
    unsigned int    number;  
    double          max = 100.0;  
    errno_t         err;  
  
    // Display 10 random integers in the range [ 1,10 ].  
    for( i = 0; i < 10;i++ )  
    {  
        err = rand_s( &number );  
        if (err != 0)  
        {  
            printf_s("The rand_s function failed!\n");  
        }  
        printf_s( "  %u\n", (unsigned int) ((double)number /  
                       ((double) UINT_MAX + 1 ) * 10.0) + 1);  
    }  
  
    printf_s("\n");  
  
    // Display 10 random doubles in [0, max).  
    for (i = 0; i < 10;i++ )  
    {  
        err = rand_s( &number );  
        if (err != 0)  
        {  
            printf_s("The rand_s function failed!\n");  
        }  
        printf_s( "  %g\n", (double) number /   
                          ((double) UINT_MAX + 1) * max );  
    }  
}  
```  
  
## <a name="sample-output"></a>Przykładowe dane wyjściowe  
  
```  
10  
4  
5  
2  
8  
2  
5  
6  
1  
1  
  
32.6617  
29.4471  
11.5413  
6.41924  
20.711  
60.2878  
61.0094  
20.1222  
80.9192  
65.0712  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Obsługa liczb zmiennoprzecinkowych](../../c-runtime-library/floating-point-support.md)   
 [srand —](../../c-runtime-library/reference/srand.md)