---
title: "log2 log2f —, log2l | Dokumentacja firmy Microsoft"
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
- log2
- log2l
- log2f
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
dev_langs: C++
ms.assetid: 94d11b38-70b7-4d3a-94ac-523153c92b2e
caps.latest.revision: "14"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: f825304439e3e1c27f5dc1e41a1ae4c311450625
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="log2-log2f-log2l"></a>log2 log2f —, log2l
Określa binarne logarytmu (base-2) w określonej wartości.  
  
## <a name="syntax"></a>Składnia  
  
```  
double log2(  
   double x  
);  
  
float log2(  
   float x  
); //C++ only  
  
long double log2(  
   long double x  
); //C++ only  
  
float log2f(  
   float x  
);  
  
long double log2l(  
   long double x  
);  
  
```  
  
#### <a name="parameters"></a>Parametry  
 [in]`x`  
 Wartość, aby określić logarytmu base-2.  
  
## <a name="return-value"></a>Wartość zwracana  
 W przypadku powodzenia zwraca zwracać log2 `x`.  
  
 W przeciwnym razie może zwracać jedną z następujących wartości:  
  
|Problem|Zwraca|  
|-----------|------------|  
|`x` < 0|NaN|  
|`x` = ±0|— INFINITY|  
|`x` = 1|+0|  
|+ INFINITY|+ INFINITY|  
|NaN|NaN|  
|błąd domeny|NaN|  
|Błąd Bieguna|-Huge_val — i - HUGE_VALF, lub - HUGE_VALL|  
  
 Błędy są zgłaszane jak określono w [_matherr —](../../c-runtime-library/reference/matherr.md).  
  
## <a name="remarks"></a>Uwagi  
 Jeśli x jest liczbą całkowitą, funkcja zwraca zasadniczo liczony od zera indeks najbardziej znaczącego bitu 1 `x`.  
  
## <a name="requirements"></a>Wymagania  
  
|Funkcja|Nagłówek C|Nagłówek C++|  
|--------------|--------------|------------------|  
|`log2`,                `log2f`,  `log2l`|\<Math.h >|\<cmath >|  
  
 Aby uzyskać dodatkowe informacje o zgodności, zobacz [zgodności](../../c-runtime-library/compatibility.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Alfabetyczne odwołanie funkcji](../../c-runtime-library/reference/crt-alphabetical-function-reference.md)   
 [exp2 —, exp2f —, exp2l](../../c-runtime-library/reference/exp2-exp2f-exp2l.md)   
 [logf —, log10, log10f — w Dzienniku](../../c-runtime-library/reference/log-logf-log10-log10f.md)