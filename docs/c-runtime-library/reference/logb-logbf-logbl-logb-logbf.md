---
title: "logb —, logbf —, logbl —, _logb —, _logbf — | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- logb
- _logb
- _logbl
- logbf
- logbl
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
- logb
- logbl
- _logb
- _logbf
- logbf
dev_langs: C++
helpviewer_keywords:
- _logbf function
- mantissas, floating-point variables
- logbf function
- _logb function
- exponent, floating-point numbers
- logbl function
- logb function
- floating-point functions
- floating-point functions, mantissa and exponent
- exponents and mantissas
ms.assetid: 780c4daa-6fe6-4fbc-9412-4c1ba1a1766f
caps.latest.revision: "13"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 81d44f12b363cf74efd334e8ff7daadb4fee5036
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="logb-logbf-logbl-logb-logbf"></a>logb, logbf, logbl, _logb, _logbf
Wyodrębnianie wartości wykładnika liczb zmiennoprzecinkowych argumentu.  
  
## <a name="syntax"></a>Składnia  
  
```  
double logb(  
   double x   
);  
float logb(  
   float x   
); // C++ only  
long double logb(  
   long double x   
); // C++ only   
float logbf(  
   float x   
);  
long double logbl(  
   long double x   
);  
double _logb(  
   double x   
);  
float _logbf(  
   float x   
);  
```  
  
#### <a name="parameters"></a>Parametry  
 x  
 Wartość zmiennoprzecinkowa.  
  
## <a name="return-value"></a>Wartość zwracana  
 `logb`Zwraca wartość nieobciążonej wykładnika `x` jako liczbę całkowitą ze znakiem reprezentowane jako wartości zmiennoprzecinkowej.  
  
## <a name="remarks"></a>Uwagi  
 `logb` Funkcje wyodrębnienie wykładniczej wartości argumentu zmiennoprzecinkowego `x`, tak jakby `x` były reprezentowane z zakresem nieskończoną. Jeśli argument `x` jest nieznormalizowane, jest traktowana tak, jakby był on znormalizowany.  
  
 Ponieważ C++ pozwala przeładowanie, można wywoływać przeciążenia `logb` który przyjmować i zwracać `float` lub `long double` wartości. W programie C `logb` zawsze przyjmuje i zwraca `double`.  
  
|Dane wejściowe|Wyjątek SEH|Matherr — wyjątek|  
|-----------|-------------------|-----------------------|  
|GRANICACH QNAN, IND|Brak|_DOMAIN —|  
|± 0|ZERODIVIDE|—|  
  
## <a name="requirements"></a>Wymagania  
  
|Procedura|Wymagany nagłówek|  
|-------------|---------------------|  
|`_logb`|\<float.h — >|  
|`logb`, `logbf`, `logbl`, `_logbf`|\<Math.h >|  
  
 Aby uzyskać więcej informacji o zgodności, zobacz [zgodności](../../c-runtime-library/compatibility.md).  
  
## <a name="libraries"></a>Biblioteki  
 Wszystkie wersje [biblioteki wykonawcze języka C](../../c-runtime-library/crt-library-features.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Obsługa liczb zmiennoprzecinkowych](../../c-runtime-library/floating-point-support.md)   
 [frexp —](../../c-runtime-library/reference/frexp.md)