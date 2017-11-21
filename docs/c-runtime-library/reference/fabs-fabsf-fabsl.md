---
title: "fabs — fabsf —, fabsl | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- fabsf
- fabs
- fabsl
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
- fabs
- fabsf
- fabsl
- "math\fabs"
- "math\fabsf"
- "math\fabsl"
dev_langs: C++
helpviewer_keywords:
- absolute values
- fabsf function
- calculating absolute values
- fabs function
- fabsl function
ms.assetid: 23bca210-f408-4f5e-b46b-0ccaaec31e36
caps.latest.revision: "11"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: b448bdc601bbe050d93cc26976fa0925ce9fff14
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="fabs-fabsf-fabsl"></a>fabs —, fabsf —, fabsl
Oblicza wartość bezwzględną liczby zmiennoprzecinkowej argumentu.  
  
## <a name="syntax"></a>Składnia  
  
```  
double fabs(   
   double x   
);  
float fabs(  
   float x   
); // C++ only  
long double fabs(  
   long double x  
); // C++ only  
float fabsf(   
   float x   
);  
long double fabsl(  
   long double x  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `x`  
 Wartość zmiennoprzecinkowa.  
  
## <a name="return-value"></a>Wartość zwracana  
 `fabs` Zwracają wartość bezwzględna argumentu `x`. Nie ma żadnych zwracany błąd.  
  
|Dane wejściowe|Wyjątek SEH|Matherr — wyjątek|  
|-----------|-------------------|-----------------------|  
|GRANICACH QNAN, IND|brak|_DOMAIN —|  
  
## <a name="remarks"></a>Uwagi  
 C++ pozwala przeładowanie, dlatego można wywoływać przeciążenia `fabs` Jeśli dołączysz \<cmath > nagłówka. W programie C `fabs` zawsze przyjmuje i zwraca wartość o podwójnej precyzji.  
  
## <a name="requirements"></a>Wymagania  
  
|Funkcja|Wymagany nagłówek C|Wymagany nagłówek C++|  
|--------------|-----------------------|---------------------------|  
|`fabs`, `fabsf`, `fabsl`|\<Math.h >|\<cmath > lub \<math.h >|  
  
 Aby uzyskać dodatkowe informacje o zgodności, zobacz [zgodności](../../c-runtime-library/compatibility.md) we wprowadzeniu.  
  
## <a name="example"></a>Przykład  
 Zobacz przykład [abs](../../c-runtime-library/reference/abs-labs-llabs-abs64.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Obsługa liczb zmiennoprzecinkowych](../../c-runtime-library/floating-point-support.md)   
 [ABS, laboratoria, llabs — _abs64 —](../../c-runtime-library/reference/abs-labs-llabs-abs64.md)   
 [_cabs —](../../c-runtime-library/reference/cabs.md)   