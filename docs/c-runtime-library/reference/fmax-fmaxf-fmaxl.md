---
title: "Fmax fmaxf —, fmaxl | Dokumentacja firmy Microsoft"
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
- fmax
- fmaxf
- fmaxl
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
- fmax
- fmaxf
- fmaxl
- math/fmax
- math/fmaxf
- math/fmaxl
dev_langs: C++
helpviewer_keywords:
- fmax function
- fmaxf function
- fmaxl function
ms.assetid: a773ccf7-495e-4a9a-8c6d-dfb53e341e35
caps.latest.revision: "11"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 6f580738ba73a7e0a8fac8662be7126edb5a9e95
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="fmax-fmaxf-fmaxl"></a>fmax, fmaxf, fmaxl
Określ większy z dwóch wartości liczbowych określony.  
  
## <a name="syntax"></a>Składnia  
  
```  
double fmax(  
   double x,   
   double y  
);  
  
float fmax(  
   float x,   
   float y  
); //C++ only  
  
long double fmax(  
   long double x,   
   long double y  
); //C++ only  
  
float fmaxf(  
   float x,   
   float y  
);  
  
long double fmaxl(  
   long double x,   
   long double y  
);  
  
```  
  
#### <a name="parameters"></a>Parametry  
 [in]`x`  
 Pierwsza wartość do porównania.  
  
 [in]`y`  
 Druga wartość do porównania.  
  
## <a name="return-value"></a>Wartość zwracana  
 Jeśli to się powiedzie, zwraca większego z `x` lub `y`. Wartość zwracana jest dokładny i nie zależą od dowolnej formy zaokrąglania.  
  
 W przeciwnym razie może zwracać jedną z następujących wartości:  
  
|Problem|Zwraca|  
|-----------|------------|  
|`x`= NaN|`y`|  
|`y`= NaN|`x`|  
|`x`i `y` = NaN|NaN|  
  
 Ta funkcja nie używa błędy określone w [_matherr —](../../c-runtime-library/reference/matherr.md).  
  
## <a name="remarks"></a>Uwagi  
 Ponieważ C++ pozwala przeładowanie, mogą wywoływać przeciążenia fmax, które podejmują i zwracać zmiennoprzecinkowych i podwójnej długości. W programie C fmax zawsze przyjmuje i zwraca wartość o podwójnej precyzji.  
  
## <a name="requirements"></a>Wymagania  
  
|Funkcja|Nagłówek C|Nagłówek C++|  
|--------------|--------------|------------------|  
|`fmax`, `fmaxf`, `fmaxl`|\<Math.h >|\<cmath > lub \<math.h >|  
  
 Aby uzyskać dodatkowe informacje o zgodności, zobacz [zgodności](../../c-runtime-library/compatibility.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Alfabetyczne odwołanie funkcji](../../c-runtime-library/reference/crt-alphabetical-function-reference.md)   
 [fmin, fminf, fminl](fmin-fminf-fminl.md)  