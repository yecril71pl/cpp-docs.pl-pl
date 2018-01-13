---
title: "fdim —, fdimf —, fdiml | Dokumentacja firmy Microsoft"
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
- fdim
- fdimf
- fdiml
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
- fdim
- fdimf
- fdiml
- math/fdim
- math/fdimf
- math/fdiml
dev_langs: C++
helpviewer_keywords:
- fdim function
- fdimf function
- fdiml function
ms.assetid: 2d4ac639-51e9-462d-84ab-fb03b06971a0
caps.latest.revision: "11"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: ecf0b0590942aad133cb7b8f478200525e4f4519
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="fdim-fdimf-fdiml"></a>fdim, fdimf, fdiml
Określa dodatnią różnica między wartościami pierwszego i drugiego.  
  
## <a name="syntax"></a>Składnia  
  
```  
double fdim(  
   double x,   
   double y  
);  
  
float fdim(  
   float x,   
   float y  
); //C++ only  
  
long double fdim(  
   long double x,   
   long double y  
); //C++ only  
  
float fdimf(  
   float x,   
   float y  
);  
  
long double fdiml(  
   long double x,   
   long double y  
);  
  
```  
  
#### <a name="parameters"></a>Parametry  
 [in]`x`  
 Pierwsza wartość.  
  
 [in]`y`  
 Druga wartość.  
  
## <a name="return-value"></a>Wartość zwracana  
 Zwraca dodatnią różnicę między `x` i `y`:  
  
|Wartość zwracana|Scenariusz|  
|------------------|--------------|  
|x i y|Jeśli x > y|  
|0|Jeśli x < = y|  
  
 W przeciwnym razie może zwracać jedną z następujących błędów:  
  
|Problem|Zwraca|  
|-----------|------------|  
|Błąd przepełnienia zakresu|+ Huge_val — + HUGE_VALF, lub + HUGE_VALL|  
|Błąd zakresu niedopełnienie|poprawne wartości (zaokrągloną)|  
|`x`lub `y` jest wartością typu NaN|NaN|  
  
 Błędy są zgłaszane jak określono w [_matherr —](../../c-runtime-library/reference/matherr.md).  
  
## <a name="remarks"></a>Uwagi  
 Ponieważ C++ pozwala przeładowanie, można wywoływać przeciążenia `fdim` który przyjmować i zwracać zmiennoprzecinkowych i podwójnej długości. W programie C `fdim` zawsze przyjmuje i zwraca wartość o podwójnej precyzji.  
  
 Z wyjątkiem obsługi NaN funkcja ta jest odpowiednikiem `fmax(x - y, 0)`.  
  
## <a name="requirements"></a>Wymagania  
  
|Funkcja|Nagłówek C|Nagłówek C++|  
|--------------|--------------|------------------|  
|`fdim`, `fdimf`, `fdiml`|\<Math.h >|\<cmath >|  
  
 Aby uzyskać dodatkowe informacje o zgodności, zobacz [zgodności](../../c-runtime-library/compatibility.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Alfabetyczne odwołanie funkcji](../../c-runtime-library/reference/crt-alphabetical-function-reference.md)   
 [Fmax fmaxf —, fmaxl](../../c-runtime-library/reference/fmax-fmaxf-fmaxl.md)   
 [abs, labs, llabs, _abs64](../../c-runtime-library/reference/abs-labs-llabs-abs64.md)