---
title: "hypot —, hypotf —, hypotl —, _hypot —, _hypotf, _hypotl | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- _hypotf
- hypot
- hypotf
- _hypot
- _hypotl
- hypotl
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
- hypotf
- hypotl
- _hypotl
- hypot
- _hypot
- _hypotf
dev_langs: C++
helpviewer_keywords:
- hypotenuse calculation
- hypot function
- hypotf function
- triangles, calculating hypotenuse
- hypotl function
- calculating hypotenuses
- _hypot function
ms.assetid: 6a13887f-bd53-43fc-9d77-5b42d6e49925
caps.latest.revision: "17"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 36a9fee91a98b224d31df6b9af58ce4caf27030a
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="hypot-hypotf-hypotl-hypot-hypotf-hypotl"></a>hypot, hypotf, hypotl, _hypot, _hypotf, _hypotl
Obliczanie przeciwprostokątnej.  
  
## <a name="syntax"></a>Składnia  
  
```  
double hypot(   
   double x,  
   double y   
);  
float hypotf(   
   float x,  
   float y   
);  
long double hypotl(  
   long double x,  
   long double y  
);  
double _hypot(   
   double x,  
   double y   
);  
float _hypotf(   
   float x,  
   float y   
);  
long double _hypotl(  
   long double x,  
   long double y  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `x`, `y`  
 Wartości zmiennoprzecinkowych.  
  
## <a name="return-value"></a>Wartość zwracana  
 W przypadku powodzenia `hypot` zwraca długość przeciwprostokątnej; na przepełnienia, `hypot` zwraca INF (nieskończoności) i `errno` zmienna jest ustawiona na `ERANGE`. Można użyć `_matherr` do zmodyfikowania obsługi błędów.  
  
 Aby uzyskać więcej informacji na temat kody powrotu, zobacz [errno _doserrno —, _sys_errlist — i _sys_nerr —](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).  
  
## <a name="remarks"></a>Uwagi  
 `hypot` Funkcje obliczyć długość przeciwprostokątnej trójkąt, podana długość obu stron `x` i `y` (innymi słowy, pierwiastek kwadratowy liczby `x` <sup>2</sup>  +  `y` <sup>2</sup>).  
  
 Wersje funkcje, które mają wiodące znaki podkreślenia są dostępne dla zgodności ze standardami wcześniej. Ich zachowanie jest takie same jak wersje, które nie mają wiodące znaki podkreślenia. Firma Microsoft zaleca dla nowego kodu przy użyciu wersji bez wiodące znaki podkreślenia.  
  
## <a name="requirements"></a>Wymagania  
  
|Procedura|Wymagany nagłówek|  
|-------------|---------------------|  
|`hypot`, `hypotf`, `hypotl`, `_hypot`, `_hypotf`, `_hypotl`|\<Math.h >|  
  
 Aby uzyskać więcej informacji o zgodności, zobacz [zgodności](../../c-runtime-library/compatibility.md).  
  
## <a name="example"></a>Przykład  
  
```  
// crt_hypot.c  
// This program prints the hypotenuse of a right triangle.  
  
#include <math.h>  
#include <stdio.h>  
  
int main( void )  
{  
   double x = 3.0, y = 4.0;  
  
   printf( "If a right triangle has sides %2.1f and %2.1f, "  
           "its hypotenuse is %2.1f\n", x, y, _hypot( x, y ) );  
}  
```  
  
```Output  
If a right triangle has sides 3.0 and 4.0, its hypotenuse is 5.0  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Obsługa liczb zmiennoprzecinkowych](../../c-runtime-library/floating-point-support.md)   
 [_cabs —](../../c-runtime-library/reference/cabs.md)   
 [_matherr —](../../c-runtime-library/reference/matherr.md)