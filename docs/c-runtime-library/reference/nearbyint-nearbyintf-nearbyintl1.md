---
title: "nearbyint —, nearbyintf —, nearbyintl | Dokumentacja firmy Microsoft"
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
- nearbyint
- nearbyintf
- nerabyintl
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
- nearbyint
- nearbyintf
- nearbyintl
- math/nearbyint
- math/narbyintf
- math/narbyintl
dev_langs:
- C++
helpviewer_keywords:
- nearbyint function
- nearbyintf function
- nearbyintl function
ms.assetid: dd39cb68-96b0-434b-820f-6ff2ea65584f
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 0d981df622450ef0b52a9b0d81427497a3e180bc
ms.sourcegitcommit: 185e11ab93af56ffc650fe42fb5ccdf1683e3847
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/29/2018
---
# <a name="nearbyint-nearbyintf-nearbyintl"></a>nearbyint, nearbyintf, nearbyintl
Zaokrągla określona wartość zmiennoprzecinkowa na liczbę całkowitą i zwraca tę wartość w formacie liczb zmiennoprzecinkowych.  
  
## <a name="syntax"></a>Składnia  
  
```  
double nearbyint(  
   double x  
);  
  
float nearbyint(  
   float x  
); //C++ only  
  
long double nearbyint(  
   long double x  
); //C++ only  
  
float nearbyintf(  
   float x  
);  
  
long double nearbyintl(  
   long double x  
);  
  
```  
  
#### <a name="parameters"></a>Parametry  
 [in]`x`  
 wartość do zaokrąglenia.  
  
## <a name="return-value"></a>Wartość zwracana  
 Jeśli to się powiedzie, zwraca `x`, zaokrąglona do najbliższej liczby całkowitej, zdefiniowane przez fegetround przy użyciu bieżącego formatu zaokrąglania. W przeciwnym razie funkcja może zwracać jedną z następujących wartości:  
  
|Problem|Zwraca|  
|-----------|------------|  
|`x`= ±INFINITY|±INFINITY nie mają być modyfikowane|  
|`x` = ±0|±0, nie mają być modyfikowane|  
|`x` = NaN|NaN|  
  
 Błędy nie są zgłaszane przez [_matherr —](../../c-runtime-library/reference/matherr.md); ściślej mówiąc, ta funkcja nie raportuje wszystkie wyjątki FE_INEXACT.  
  
## <a name="remarks"></a>Uwagi  
 Główną różnicą między tej funkcji i `rint` jest ta funkcja nie zgłaszał niedokładnymi zmiennoprzecinkowych wyjątków punktu.  
  
 Ponieważ maksymalne wartości zmiennoprzecinkowe są dokładne liczb całkowitych, ta funkcja nigdy nie będzie przepełnienie siebie. dane wyjściowe mogą zamiast przepełnienie zwracanej wartości, w zależności od instalowanej wersji funkcji używasz.  
  
## <a name="requirements"></a>Wymagania  
  
|Funkcja|Nagłówek C|Nagłówek C++|  
|--------------|--------------|------------------|  
|`nearbyint`,                `nearbyintf`,  `nearbyintl`|\<math.h>|\<cmath>|  
  
 Aby uzyskać dodatkowe informacje o zgodności, zobacz [zgodności](../../c-runtime-library/compatibility.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Alfabetyczne zestawienie funkcji](../../c-runtime-library/reference/crt-alphabetical-function-reference.md)