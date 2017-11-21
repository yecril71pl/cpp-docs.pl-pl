---
title: "FMA fmaf —, fmal | Dokumentacja firmy Microsoft"
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
- fma
- fmaf
- fmal
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
- fma
- fmaf
- fmal
- math/fma
- math/fmaf
- math/fmal
dev_langs: C++
helpviewer_keywords:
- fma function
- fmaf function
- fmal function
ms.assetid: 584a6037-da1e-4e86-9f0c-97aae86de0c0
caps.latest.revision: "10"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: ec77e462b357708153f26b5289f35c2ee7b7a104
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="fma-fmaf-fmal"></a>fma, fmaf, fmal
Mnoży dwie wartości ze sobą, dodaje trzecia wartość, a następnie zaokrągla wyniku bez utraty żadnych precyzji z powodu pośredniczące zaokrąglania.  
  
## <a name="syntax"></a>Składnia  
  
```  
double fma(  
   double x,   
   double y,   
   double z  
);  
  
float fma(  
   float  x,   
   float  y,   
   float z  
); //C++ only  
  
long double fma(  
   long double  x,   
   long double  y,   
   long double z  
); //C++ only  
  
float fmaf(  
   float  x,   
   float  y,   
   float z  
);  
  
long double fmal(  
   long double  x,   
   long double  y,   
   long double z  
);  
  
```  
  
#### <a name="parameters"></a>Parametry  
 [in]`x`  
 Pierwsza wartość wielokrotnie.  
  
 [in]`y`  
 Druga wartość używana w wielokrotnie.  
  
 [in]`z`  
 Wartość do dodania.  
  
## <a name="return-value"></a>Wartość zwracana  
 Zwraca `(x * y) + z`. Wartość zwracana jest następnie zaokrąglana przy użyciu bieżącego formatu zaokrąglania.  
  
 W przeciwnym razie może zwracać jedną z następujących wartości:  
  
|Problem|Zwraca|  
|-----------|------------|  
|`x`= NIESKOŃCZONOŚCI, `y` = 0 lub<br /><br /> `x`= 0, `y` = INFINITY|NaN|  
|`x`lub `y` mniej dokładne więcej NIESKOŃCZONOŚCI, `z` = NIESKOŃCZONOŚCI symbol przeciwnego|NaN|  
|`x`lub `y` = NaN|NaN|  
|nie (`x` = 0, `y`= nieograniczonego) i `z` = NaN<br /><br /> nie (`x`= nieokreślony, `y`= 0) i `z` = NaN|NaN|  
|Błąd przepełnienia zakresu|±HUGE_VAL, ±HUGE_VALF lub ±HUGE_VALL|  
|Błąd zakresu niedopełnienie|prawidłowa wartość zaokrągloną.|  
  
 Błędy są zgłaszane jak określono w [_matherr —](../../c-runtime-library/reference/matherr.md).  
  
## <a name="remarks"></a>Uwagi  
 Ponieważ C++ pozwala przeładowanie, można wywoływać przeciążenia `fma` który przyjmować i zwracać **float** i **podwójnej długości** typów. W programie C `fma` zawsze przyjmuje i zwraca **podwójne**.  
  
 Ta funkcja oblicza wartość tak, jakby zostały podjęte dokładnością nieskończone, a następnie zaokrągla wynik końcowy.  
  
## <a name="requirements"></a>Wymagania  
  
|Funkcja|Nagłówek C|Nagłówek C++|  
|--------------|--------------|------------------|  
|`fma`, `fmaf`, `fmal`|\<Math.h >|\<cmath >|  
  
 Aby uzyskać dodatkowe informacje o zgodności, zobacz [zgodności](../../c-runtime-library/compatibility.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Alfabetyczne odwołanie funkcji](../../c-runtime-library/reference/crt-alphabetical-function-reference.md)   
 [pozostałe remainderf —, remainderl](../../c-runtime-library/reference/remainder-remainderf-remainderl.md)   
 [remquo —, remquof —, remquol —](../../c-runtime-library/reference/remquo-remquof-remquol.md)