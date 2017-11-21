---
title: "nearbyint —, nearbyintf —, nearbyintl1 | Dokumentacja firmy Microsoft"
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
dev_langs: C++
helpviewer_keywords:
- nearbyint function
- nearbyintf function
- nearbyintl function
ms.assetid: dd39cb68-96b0-434b-820f-6ff2ea65584f
caps.latest.revision: "12"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 205381e315cf703a9fded4b24812a32c4aef4a9a
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
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
|`x`= NaN|NaN|  
  
 Błędy nie są zgłaszane przez [_matherr —](../../c-runtime-library/reference/matherr.md); ściślej mówiąc, ta funkcja nie raportuje wszystkie wyjątki FE_INEXACT.  
  
## <a name="remarks"></a>Uwagi  
 Główną różnicą między tej funkcji i `rint` jest ta funkcja nie zgłaszał niedokładnymi zmiennoprzecinkowych wyjątków punktu.  
  
 Ponieważ maksymalne wartości zmiennoprzecinkowe są dokładne liczb całkowitych, ta funkcja nigdy nie będzie przepełnienie siebie. dane wyjściowe mogą zamiast przepełnienie zwracanej wartości, w zależności od instalowanej wersji funkcji używasz.  
  
## <a name="requirements"></a>Wymagania  
  
|Funkcja|Nagłówek C|Nagłówek C++|  
|--------------|--------------|------------------|  
|`nearbyint`,                `nearbyintf`,  `nearbyintl`|\<Math.h >|\<cmath >|  
  
 Aby uzyskać dodatkowe informacje o zgodności, zobacz [zgodności](../../c-runtime-library/compatibility.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Alfabetyczne odwołanie funkcji](../../c-runtime-library/reference/crt-alphabetical-function-reference.md)