---
title: "scalbn —, scalbnf —, scalbnl, scalbln, scalblnf, scalblnl | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- scalblnl
- scalbnl
- scalbnf
- scalblnf
- scalbn
- scalbln
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
- scalblnf
- scalbnl
- scalblnl
- scalbln
- scalbn
- scalbnf
dev_langs: C++
helpviewer_keywords:
- scalbn function
- scalbln function
- scalblnl function
- scalbnl function
- scalbnf function
- scalblnf function
ms.assetid: df2f1543-8e39-4af4-a5cf-29307e64807d
caps.latest.revision: "5"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 6ef24a46d7152934351fddf4be6b58392ce0a0ef
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="scalbn-scalbnf-scalbnl-scalbln-scalblnf-scalblnl"></a>scalbn, scalbnf, scalbnl, scalbln, scalblnf, scalblnl
Mnoży liczba zmiennoprzecinkowa przez całkowitą potęgą liczby flt_radix —.  
  
## <a name="syntax"></a>Składnia  
  
```  
double scalbn(  
   double x,  
   int exp   
);  
float scalbn(  
   float x,  
   int exp  
);  // C++ only  
long double scalbn(  
   long double x,  
   int exp  
);  // C++ only   
float scalbnf(  
   float x,  
   int exp  
);   
long double scalbnl(  
   long double x,  
   int exp  
);  
double scalbln(  
   double x,  
   long exp   
);  
float scalbln(  
   float x,  
   long exp  
);  // C++ only  
long double scalbln(  
   long double x,  
   long exp  
);  // C++ only   
float scalblnf(  
   float x,  
   long exp  
);   
long double scalblnl(  
   long double x,  
   long exp  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `x`  
 Wartość zmiennoprzecinkowa.  
  
 `exp`  
 Wykładnik liczby całkowitej.  
  
## <a name="return-value"></a>Wartość zwracana  
 `scalbn` Zwracają wartość `x`  *  `FLT_RADIX` <sup>exp</sup> zakończone powodzeniem. Na przepełnienia (w zależności od jej znaku `x`), `scalbn` zwraca `HUGE_VAL`; `errno` ma wartość `ERANGE`.  
  
 Aby uzyskać więcej informacji na temat `errno` i może zawierać błąd zwracają wartości, zobacz [errno _doserrno —, _sys_errlist — i _sys_nerr —](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).  
  
## <a name="remarks"></a>Uwagi  
 `FLT_RADIX`jest zdefiniowany w \<float.h — > jako podstawa natywnych liczb zmiennoprzecinkowych; w systemach pliku binarnego, jest równa 2, a `scalbn` jest odpowiednikiem [ldexp —](../../c-runtime-library/reference/ldexp.md).  
  
 Ponieważ C++ pozwala przeładowanie, można wywoływać przeciążenia `scalbn` i `scalbln` który przyjmować i zwracać `float` lub `long double` typów. W programie C `scalbn` zawsze ma `double` i `int` i zwraca `double`, i `scalbln` zawsze ma `double` i `long` i zwraca `double`.  
  
## <a name="requirements"></a>Wymagania  
  
|Funkcja|Nagłówek C|Nagłówek C++|  
|--------------|--------------|------------------|  
|`scalbn`, `scalbnf`, `scalbnl`, `scalbln`, `scalblnf`, `scalblnl`|\<Math.h >|\<cmath >|  
  
 Aby uzyskać dodatkowe informacje o zgodności, zobacz [zgodności](../../c-runtime-library/compatibility.md).  
  
## <a name="example"></a>Przykład  
  
```  
// crt_scalbn.c  
// Compile using: cl /W4 crt_scalbn.c  
#include <math.h>  
#include <stdio.h>  
  
int main( void )  
{  
   double x = 6.4, y;  
   int p = 3;  
  
   y = scalbn( x, p );  
   printf( "%2.1f times FLT_RADIX to the power of %d is %2.1f\n", x, p, y );  
}  
```  
  
## <a name="output"></a>Dane wyjściowe  
  
```  
6.4 times FLT_RADIX to the power of 3 is 51.2  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Obsługa liczb zmiennoprzecinkowych](../../c-runtime-library/floating-point-support.md)   
 [frexp —](../../c-runtime-library/reference/frexp.md)   
 [ldexp —](../../c-runtime-library/reference/ldexp.md)   
 [modf, modff, modfl](../../c-runtime-library/reference/modf-modff-modfl.md)