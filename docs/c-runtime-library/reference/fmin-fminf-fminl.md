---
title: "Fmin fminf —, fminl | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- fmin
- fminf
- fminl
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
- fmin
- fminf
- fminl
- math/fmin
- math/fminf
- math/fminl
helpviewer_keywords:
- fmin function
- fminf function
- fminl function
ms.assetid: 1916dfb5-99c1-4b0d-aefb-513525c3f2ac
caps.latest.revision: "5"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 3428afcdcf403c733e5282b2b3c4347ba94497d7
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="fmin-fminf-fminl"></a>fmin, fminf, fminl
Określa mniejszy z dwiema określonymi wartościami.  
  
## <a name="syntax"></a>Składnia  
  
```  
double fmin(  
   double x,   
   double y  
);  
  
float fmin(  
   float x,   
   float y  
); //C++ only  
  
long double fmin(  
   long double x,   
   long double y  
); //C++ only  
  
float fminf(  
   float x,   
   float y  
);  
  
long double fminl(  
   long double x,   
   long double y  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `x`  
 Pierwsza wartość do porównania.  
  
 `y`  
 Druga wartość do porównania.  
  
## <a name="return-value"></a>Wartość zwracana  
 Jeśli to się powiedzie, zwraca mniejszy z `x` lub `y`.  
  
|Dane wejściowe|Wynik|  
|-----------|------------|  
|`x`jest wartością typu NaN|`y`|  
|`y`jest wartością typu NaN|`x`|  
|`x`i `y` są NaN|NaN|  
  
 Funkcja nie powoduje, że [_matherr —](../../c-runtime-library/reference/matherr.md) do wywołania, powodują wyjątki zmiennoprzecinkowe lub zmień wartość `errno`.  
  
## <a name="remarks"></a>Uwagi  
 Ponieważ C++ pozwala przeładowanie, można wywoływać przeciążenia `fmin` który przyjmować i zwracać zmiennoprzecinkowych i podwójnej długości. W programie C `fmin` zawsze przyjmuje i zwraca wartość o podwójnej precyzji.  
  
## <a name="requirements"></a>Wymagania  
  
|Procedura|Wymagany nagłówek|  
|-------------|---------------------|  
|`fmin`, `fminf`, `fminl`|C: \<math.h ><br />C++: \<math.h > lub \<cmath >|  
  
 Aby uzyskać dodatkowe informacje o zgodności, zobacz [zgodności](../../c-runtime-library/compatibility.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Alfabetyczne zestawienie funkcji](../../c-runtime-library/reference/crt-alphabetical-function-reference.md)  
 [fmax, fmaxf, fmaxl](fmax-fmaxf-fmaxl.md)  