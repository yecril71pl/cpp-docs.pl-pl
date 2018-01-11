---
title: "exp2 —, exp2f —, exp2l | Dokumentacja firmy Microsoft"
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
- exp2
- exp2f
- exp2l
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
- exp2
- math/exp2
- exp2f
- math/exp2f
- exp2l
- math/exp2l
dev_langs: C++
helpviewer_keywords:
- exp2 function
- exp2f function
- exp2l function
ms.assetid: 526e3e10-201a-4610-a886-533f44ece344
caps.latest.revision: "13"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 2ceff966e289fd3118cdd515fb4fbc288080b0f3
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="exp2-exp2f-exp2l"></a>exp2, exp2f, exp2l
Oblicza 2 podniesione do określonej wartości.  
  
## <a name="syntax"></a>Składnia  
  
```  
double exp2(  
   double x  
);  
  
float exp2(  
   float x  
);  // C++ only  
  
long double exp2(  
   long double x  
); // C++ only  
  
float exp2f(  
   float x  
);  
  
long double exp2l(  
   long double x  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 [in]`x`  
 Wartość wykładnik.  
  
## <a name="return-value"></a>Wartość zwracana  
 Jeśli to się powiedzie, zwraca wykładnik base-2 `x`, czyli 2<sup>x</sup>. W przeciwnym razie zwraca jedną z następujących wartości:  
  
|Problem|Zwraca|  
|-----------|------------|  
|`x` = ±0|1|  
|`x`= — WARTOŚCI INFINITY|+0|  
|`x`= + INFINITY|+ INFINITY|  
|`x`= NaN|NaN|  
|Błąd przepełnienia zakresu|+ Huge_val — + HUGE_VALF, lub + HUGE_VALL|  
|Błąd zakresu niedopełnienie|Prawidłowego wyniku zaokrągloną|  
  
 Błędy są zgłaszane jak określono w [_matherr —](../../c-runtime-library/reference/matherr.md).  
  
## <a name="remarks"></a>Uwagi  
 Ponieważ C++ pozwala przeładowanie, można wywoływać przeciążenia `exp2` który przyjmować i zwracać **float** i **podwójnej długości** typów. W programie C `exp2` zawsze przyjmuje i zwraca **podwójne**.  
  
## <a name="requirements"></a>Wymagania  
  
|Procedura|Nagłówek C|Nagłówek C++|  
|-------------|--------------|------------------|  
|`exp`, `expf`, `expl`|\<Math.h >|\<cmath >|  
  
 Aby uzyskać dodatkowe informacje o zgodności, zobacz [zgodności](../../c-runtime-library/compatibility.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Alfabetyczne odwołanie funkcji](../../c-runtime-library/reference/crt-alphabetical-function-reference.md)   
 [EXP, expf —, expl](../../c-runtime-library/reference/exp-expf.md)   
 [log2, log2f, log2l](../../c-runtime-library/reference/log2-log2f-log2l.md)