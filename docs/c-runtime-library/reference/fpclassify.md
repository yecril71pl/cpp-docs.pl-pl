---
title: "fpclassify — | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
apiname: fpclassify
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
apitype: HeaderDef
f1_keywords:
- fpclassify
- math/fpclassify
helpviewer_keywords:
- fpclassify macro
- fpclassify function
ms.assetid: bf549499-7ff9-4a58-8692-f2d1cb6bab81
caps.latest.revision: "3"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 3f1dac5272bbc8cf956bf8bcfdbd31b1f71b4708
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="fpclassify"></a>fpclassify —
Zwraca zmiennoprzecinkowe klasyfikacji argumentu.  
  
## <a name="syntax"></a>Składnia  
  
```  
int fpclassify(   
   /* floating-point */ x   
);  
  
int fpclassify(   
   float x   
); // C++ only  
  
int fpclassify(   
   double x   
); // C++ only  
  
int fpclassify(   
   long double x   
); // C++ only  
  
```  
  
#### <a name="parameters"></a>Parametry  
 `x`  
 Wartość zmiennoprzecinkowa do testowania.  
  
## <a name="return-value"></a>Wartość zwracana  
 `fpclassify`Zwraca wartość wskazującą zmiennoprzecinkowe klasy argumentu `x`. W tej tabeli przedstawiono możliwe wartości zwracane przez `fpclassify`zdefiniowanej w \<math.h >.  
  
|Wartość|Opis|  
|-----------|-----------------|  
|`FP_NAN`|Cichy, sygnalizowania lub nieokreślony NaN|  
|`FP_INFINITE`|Infinity dodatnie lub ujemne|  
|`FP_NORMAL`|Dodatnie lub ujemne niezerową wartość znormalizowaną|  
|`FP_SUBNORMAL`|Nieznormalizowana wartość dodatnią lub ujemną|  
|`FP_ZERO`|Dodatnią lub ujemną wartość zero|  
  
## <a name="remarks"></a>Uwagi  
 W języku C `fpclassify` jest makrem; w języku C++ `fpclassify` jest przeciążony przy użyciu typów argumentu funkcji `float`, `double`, lub `long double`. W obu przypadkach wartość zwracana zależy od wprowadzenia typu wyrażenia argumentu, a nie na dowolnym reprezentacji pośredniej. Na przykład zwykłym `double` lub `long double` wartość może stać się nieskończoności, Brak reprezentacji zmiennoprzecinkowej lub zero wartości po konwersji na `float`.  
  
## <a name="requirements"></a>Wymagania  
  
|Funkcja/makra|Wymagany nagłówek (C)|Wymaganego nagłówka (C++)|  
|---------------------|---------------------------|-------------------------------|  
|`fpclassify`|\<Math.h >|\<Math.h > lub \<cmath >|  
  
 `fpclassify` Makro i `fpclassify` funkcje odpowiadają C99 i C ++ 11 specyfikacji. Aby uzyskać więcej informacji o zgodności, zobacz [zgodności](../../c-runtime-library/compatibility.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Obsługa liczb zmiennoprzecinkowych](../../c-runtime-library/floating-point-support.md)   
 [isnan, _isnan, _isnanf](../../c-runtime-library/reference/isnan-isnan-isnanf.md)