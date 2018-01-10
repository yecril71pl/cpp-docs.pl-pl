---
title: Drukowanie, rintf, rintl | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- rintf
- rintl
- rint
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
- api-ms-win-crt-math-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- rintf
- rintl
- rint
dev_langs: C++
helpviewer_keywords:
- rintf function
- rint function
- rintl function
ms.assetid: 312ae3e6-278c-459a-9393-11b8f87d9184
caps.latest.revision: "8"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: f9d993879a37a7fc4d940d06920b5c5de1758433
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="rint-rintf-rintl"></a>rint, rintf, rintl
Zaokrągla wartość zmiennoprzecinkowa do najbliższej liczby całkowitej w formacie liczb zmiennoprzecinkowych.  
  
## <a name="syntax"></a>Składnia  
  
```  
double rint( double x );  
float rint( float x );  // C++ only  
long double rint( long double x );  // C++ only  
float rintf( float x );   
long double rintl( long double x );  
  
```  
  
#### <a name="parameters"></a>Parametry  
 `x`  
 Wartość zmiennoprzecinkowa zostać zaokrąglona.  
  
## <a name="return-value"></a>Wartość zwracana  
 `rint` Zwracają wartość zmiennoprzecinkowa, która reprezentuje najbliższej liczby całkowitej w celu `x`. W połowie wartości są zaokrąglane zgodnie z ustawieniem bieżącego trybu zaokrąglania liczb zmiennoprzecinkowych, taka sama jak `nearbyint` funkcji. W odróżnieniu od `nearbyint` funkcje, `rint` funkcje mogą zgłaszać `FE_INEXACT` zmiennoprzecinkowych wyjątków, jeśli wynik różni się w wartości w argumencie. Nie ma żadnych zwracany błąd.  
  
|Dane wejściowe|Wyjątek SEH|`_matherr`Wyjątek|  
|-----------|-------------------|--------------------------|  
|∞; GRANICACH, QNAN, IND|brak|brak|  
|Denormals|EXCEPTION_FLT_UNDERFLOW|brak|  
  
## <a name="remarks"></a>Uwagi  
 Ponieważ C++ pozwala przeładowanie, można wywoływać przeciążenia `rint` który przyjmować i zwracać `float` i `long double` wartości. W programie C `rint` zawsze przyjmuje i zwraca `double`.  
  
## <a name="requirements"></a>Wymagania  
  
|Funkcja|Nagłówek C|Nagłówek C++|  
|--------------|--------------|------------------|  
|`rint`, `rintf`, `rintl`|\<Math.h >|\<cmath >|  
  
 Aby uzyskać dodatkowe informacje o zgodności, zobacz [zgodności](../../c-runtime-library/compatibility.md).  
  
## <a name="example"></a>Przykład  
  
```  
// crt_rint.c  
// Build with: cl /W3 /Tc crt_rint.c  
// This example displays the rounded results of  
// the floating-point values 2.499999, -2.499999,   
// 2.8, -2.8, 2.5 and -2.5.  
  
#include <math.h>  
#include <stdio.h>  
  
int main( void )  
{  
   double x = 2.499999;  
   float y = 2.8f;  
   long double z = 2.5;  
  
   printf("rint(%f) is %.0f\n", x, rint (x));  
   printf("rint(%f) is %.0f\n", -x, rint (-x));  
   printf("rintf(%f) is %.0f\n", y, rintf(y));  
   printf("rintf(%f) is %.0f\n", -y, rintf(-y));  
   printf("rintl(%Lf) is %.0Lf\n", z, rintl(z));  
   printf("rintl(%Lf) is %.0Lf\n", -z, rintl(-z));  
}  
```  
  
```Output  
rint(2.499999) is 2  
rint(-2.499999) is -2  
rintf(2.800000) is 3  
rintf(-2.800000) is -3  
rintl(2.500000) is 3  
rintl(-2.500000) is -3  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Obsługa liczb zmiennoprzecinkowych](../../c-runtime-library/floating-point-support.md)   
 [ceil ceilf —, ceill —](../../c-runtime-library/reference/ceil-ceilf-ceill.md)   
 [FLOOR floorf —, floorl —](../../c-runtime-library/reference/floor-floorf-floorl.md)   
 [fmod —, fmodf —](../../c-runtime-library/reference/fmod-fmodf.md)   
 [lrint, lrintf, lrintl, llrint, llrintf, llrintl](http://msdn.microsoft.com/en-us/312fd869-a9c0-4107-bb23-ab8299d04385)   
 [lround —, lroundf —, lroundl —, llround — llroundf —, llroundl —](../../c-runtime-library/reference/lround-lroundf-lroundl-llround-llroundf-llroundl.md)   
 [nearbyint —, nearbyintf —, nearbyintl](http://msdn.microsoft.com/en-us/15111e73-331d-41d1-81b7-3e10df894848)   
 [Drukowanie](../../c-runtime-library/reference/rint-rintf-rintl.md)