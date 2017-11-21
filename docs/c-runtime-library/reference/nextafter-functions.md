---
title: "nextafter —, nextafterf —, nextafterl, _nextafter —, _nextafterf, nexttoward, nexttowardf, nexttowardl | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- nextafterf
- _nextafterf
- nextafter
- nextafterl
- _nextafter
- nexttoward
- nexttowardf
- nexttowardl
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
- nextafter
- _nextafter
- nextafterf
- nextafterl
- _nextafterf
- math/nextafter
- math/nextafterf
- math/nextafterl
- nexttoward
- nexttowardf
- nexttowardl
- math/nexttoward
- math/nexttowardf
- math/nexttowardl
dev_langs: C++
helpviewer_keywords:
- _nextafter function
- nextafter function
- _nextafterf function
- nextafterf function
- nextafterl function
- nexttoward function
- nexttowardf function
- nexttowardl function
ms.assetid: 9785bfb9-de53-4bd0-9637-f05fa0c1f6ab
caps.latest.revision: "13"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 3dad9078ba4c683b4d29d366943559ad8228cb31
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="nextafter-nextafterf-nextafterl-nextafter-nextafterf-nexttoward-nexttowardf-nexttowardl"></a>nextafter — nextafterf —, nextafterl, _nextafter —, _nextafterf, nexttoward, nexttowardf, nexttowardl
Zwraca następnej można przedstawić wartości zmiennoprzecinkowych.  
  
## <a name="syntax"></a>Składnia  
  
```  
double nextafter(  
   double x,  
   double y   
);  
  
float nextafter(  
   float x,  
   float y   
); /* C++ only, requires <cmath> */  
  
long double nextafter(  
   long double x,  
   long double y   
); /* C++ only, requires <cmath> */  
  
float nextafterf(  
   float x,  
   float y   
);   
  
long double nextafterl(  
   long double x,  
   long double y   
);  
  
double _nextafter(  
   double x,  
   double y   
);  
  
float _nextafterf(  
   float x,  
   float y   
); /* x64 only */  
  
double nexttoward(  
   double x,  
   long double y   
);  
  
float nexttoward(  
   float x,  
   long double y   
); /* C++ only, requires <cmath> */  
  
long double nexttoward(  
   long double x,  
   long double y   
); /* C++ only, requires <cmath> */  
  
float nexttowardf(  
   float x,  
   long double y   
);   
  
long double nexttowardl(  
   long double x,  
   long double y   
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `x`  
 Wartość zmiennoprzecinkowa, aby uruchomić z.  
  
 `y`  
 Wartość zmiennoprzecinkowa, aby przejść do.  
  
## <a name="return-value"></a>Wartość zwracana  
 Zwraca następnej można przedstawić wartości zmiennoprzecinkowych typu zwracanego po `x` w kierunku `y`. Jeśli `x` = `y`, funkcja zwraca `y`konwersji na zwracany typ nie wyjątek wyzwolone. Jeśli `x` nie jest równa `y`, wynik jest nieznormalizowany lub zero, FE_UNDERFLOW i FE_INEXACT stan zmiennoprzecinkowych wyjątków są ustawiane i poprawny wynik zostanie zwrócony. Jeśli dowolny `x` lub `y` jest NAN, a następnie wartość zwracana jest jednym z wejściowej wartości NaN. Jeśli `x` jest jednak ograniczona i wynik jest nieskończone lub nie można przedstawić w typie, zwracany jest poprawnie podpisane infinity lub NAN, FE_OVERFLOW i FE_INEXACT stan zmiennoprzecinkowych wyjątków są skonfigurowane, i `errno` ma ustawioną wartość erange —.  
  
## <a name="remarks"></a>Uwagi  
 `nextafter` i `nexttoward` rodziny funkcji są równoważne, z wyjątkiem typu parametru `y`. Jeśli `x` i `y` są takie same, jest zwracana wartość `y` przekonwertować na typ zwracany.  
  
 Ponieważ C++ pozwala przeciążeniu, Jeśli dołączysz \<cmath > można wywoływać przeciążenia `nextafter` i `nexttoward` zwracające `float` i `long double` typów. W programie C `nextafter` i `nexttoward` zawsze zwraca `double`.  
  
 `_nextafter` i `_nextafterf` funkcje są określone firmy Microsoft. `_nextafterf` Funkcja jest dostępna tylko podczas kompilowania dla x64.  
  
## <a name="requirements"></a>Wymagania  
  
|Procedura|Wymagany nagłówek (C)|Wymaganego nagłówka (C++)|  
|-------------|---------------------------|-------------------------------|  
|`nextafter`, `nextafterf`, `nextafterl`, `_nextafterf`, `nexttoward`, `nexttowardf`, `nexttowardl`|\<Math.h >|\<Math.h > lub \<cmath >|  
|`_nextafter`|\<float.h — >|\<float.h — > lub \<cfloat — >|  
  
 Aby uzyskać więcej informacji o zgodności, zobacz [zgodności](../../c-runtime-library/compatibility.md) we wprowadzeniu.  
  
## <a name="see-also"></a>Zobacz też  
 [Obsługa liczb zmiennoprzecinkowych](../../c-runtime-library/floating-point-support.md)   
 [isNaN _isnan —, _isnanf](../../c-runtime-library/reference/isnan-isnan-isnanf.md)