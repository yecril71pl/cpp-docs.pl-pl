---
title: "log1p —, log1pf —, log1pl2 | Dokumentacja firmy Microsoft"
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
- log1p
- log1pf
- log1pl
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
- log1p
- log1pf
- log1pl
- math/log1p
- math/log1pf
- math/log1pl
helpviewer_keywords:
- log1p function
- log1pf function
- log1pl function
ms.assetid: a40d965d-b4f6-42f4-ba27-2395546f7c12
caps.latest.revision: "7"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: f32799e2eabc54dacdc5144c59483b7a6a641110
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="log1p-log1pf-log1pl"></a>log1p —, log1pf —, log1pl
Oblicza logarytm naturalny 1 oraz określonej wartości.  
  
## <a name="syntax"></a>Składnia  
  
```  
double log1p(  
   double x  
);  
  
float log1p(  
   float x  
); //C++ only  
  
long double log1p(  
   long double x  
); //C++ only  
  
float log1pf(  
   float x  
);  
  
long double log1pl(  
   long double x  
);  
  
```  
  
#### <a name="parameters"></a>Parametry  
 `x`  
 Argument zmiennoprzecinkowy.  
  
## <a name="return-value"></a>Wartość zwracana  
 Jeśli to się powiedzie, zwraca logarytm naturalny (base-e) z (`x`+ 1).  
  
 W przeciwnym razie może zwracać jedną z następujących wartości:  
  
|Dane wejściowe|Wynik|Wyjątek SEH|errno|  
|-----------|------------|-------------------|-----------|  
|+ inf|+ inf|||  
|Denormals|Taki sam jak wejście|NIEDOPEŁNIENIE||  
|±0|Taki sam jak wejście|||  
|-1|-inf|DIVBYZERO|ERANGE —|  
|< -1|NaN|NIEPRAWIDŁOWY|EDOM —|  
|-inf|NaN|NIEPRAWIDŁOWY|EDOM —|  
|±SNaN|Taki sam jak wejście|NIEPRAWIDŁOWY||  
|±QNaN nieograniczonego|Taki sam jak wejście|||  
  
 `errno` Wartość jest równa erange — Jeśli `x` = -1. `errno` Wartość jest równa edom — Jeśli `x` < -1.  
  
## <a name="remarks"></a>Uwagi  
 `log1p` Funkcje mogą być bardziej dokładne niż przy użyciu dziennika (`x`+ 1) Jeśli x jest bliski 0.  
  
 Ponieważ C++ pozwala przeładowanie, można wywoływać przeciążenia `log1p` który przyjmować i zwracać zmiennoprzecinkowych i podwójnej długości. W programie C `log1p` zawsze przyjmuje i zwraca wartość o podwójnej precyzji.  
  
 Jeśli `x` jest liczbą naturalnego, funkcja zwraca logarytm silni (`x`-1).  
  
## <a name="requirements"></a>Wymagania  
  
|Funkcja|Nagłówek C|Nagłówek C++|  
|--------------|--------------|------------------|  
|`log1p`,                `log1pf`,  `log1pl`|\<Math.h >|\<cmath >|  
  
 Aby uzyskać dodatkowe informacje o zgodności, zobacz [zgodności](../../c-runtime-library/compatibility.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Alfabetyczne odwołanie funkcji](../../c-runtime-library/reference/crt-alphabetical-function-reference.md)   
 [log2 log2f —, log2l](../../c-runtime-library/reference/log2-log2f-log2l.md)   
 [log, logf, log10, log10f](../../c-runtime-library/reference/log-logf-log10-log10f.md)