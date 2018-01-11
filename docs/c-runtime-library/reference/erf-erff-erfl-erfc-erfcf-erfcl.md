---
title: "ERF, erff —, erfl —, erfc, erfcf —, erfcl | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- erff
- erfl
- erf
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
- erfl
- erf
- erff
dev_langs: C++
helpviewer_keywords:
- erfl function
- erff function
- erf function
ms.assetid: 144d90d3-e437-41c2-a659-cd57596023b5
caps.latest.revision: "7"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 54256f68263ea966466c9c038f429ab4a73fc868
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="erf-erff-erfl-erfc-erfcf-erfcl"></a>erf, erff, erfl, erfc, erfcf, erfcl
Oblicza funkcji błąd lub uzupełniające błąd wartości.  
  
## <a name="syntax"></a>Składnia  
  
```  
double erf(  
   double x  
);  
float erf(  
   float x  
); // C++ only  
long double erf(  
   long double x  
); // C++ only  
float erff(  
   float x  
);  
long double erfl(  
   long double x  
);  
double erfc(  
   double x  
);  
float erfc(  
   float x  
); // C++ only  
long double erfc(  
   long double x  
); // C++ only  
float erfcf(  
   float x  
);  
long double erfcl(  
   long double x  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `x`  
 Wartość zmiennoprzecinkowa.  
  
## <a name="return-value"></a>Wartość zwracana  
 `erf` Zwracają gausach funkcji błąd `x`. `erfc` Zwracają gausach uzupełniające funkcję błąd `x`.  
  
## <a name="remarks"></a>Uwagi  
 `erf` Funkcje obliczania funkcji błędu gausach x, który jest zdefiniowany jako:  
  
 ![Funkcja błędu x](../../c-runtime-library/reference/media/crt_erf_formula.PNG "CRT_erf_formula")  
  
 Uzupełniające funkcji błędu gausach jest zdefiniowany jako 1 - erf(x). `erf` Zwracają wartość z zakresu od -1,0 do 1,0. Nie ma żadnych zwracany błąd. `erfc` Zwracają wartość z zakresu od 0 do 2. Jeśli `x` jest za duża dla `erfc`, `errno` zmienna jest ustawiona na `ERANGE`.  
  
 Ponieważ C++ pozwala przeładowanie, można wywoływać przeciążenia `erf` i `erfc` który przyjmować i zwracać `float` i `long double` typów. W programie C `erf` i `erfc` zawsze przyjmować i zwracać `double`.  
  
## <a name="requirements"></a>Wymagania  
  
|Funkcja|Wymagany nagłówek|  
|--------------|---------------------|  
|`erf`, `erff`, `erfl`, `erfc`, `erfcf`, `erfcl`|\<Math.h >|  
  
 Aby uzyskać dodatkowe informacje o zgodności, zobacz [zgodności](../../c-runtime-library/compatibility.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Obsługa liczb zmiennoprzecinkowych](../../c-runtime-library/floating-point-support.md)