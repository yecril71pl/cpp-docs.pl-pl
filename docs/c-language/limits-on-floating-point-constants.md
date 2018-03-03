---
title: "Limity dla stałych zmiennoprzecinkowych | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-language
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- ranges, floating-point constants
- floating-point constants, limits
- FLOAT.H header file
- constants, floating-point
- limits, floating-point constants
- floating-point numbers, floating limits
ms.assetid: 2d975868-2af6-45d7-a8af-db79f2c6b67b
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 715f337a4c94e65641660b4becbb33d6a151d9ca
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="limits-on-floating-point-constants"></a>Limity dla stałych zmiennoprzecinkowych
**Dotyczące firmy Microsoft**  
  
 Limity wartości stałe zmiennoprzecinkowe są podane w poniższej tabeli. Plik nagłówka FLOAT. H zawiera te informacje.  
  
### <a name="limits-on-floating-point-constants"></a>Limity dla stałych zmiennoprzecinkowych  
  
|Stała|Znaczenie|Wartość|  
|--------------|-------------|-----------|  
|**FLT_DIG —**<br />**DBL_DIG —**<br />**LDBL_DIG**|Liczba cyfr, *q*, że liczba zmiennoprzecinkowa z *q* cyfr dziesiętnych mogą być zaokrąglane do odwzorowanie liczby zmiennoprzecinkowej i ponownie bez utraty dokładności.|6<br />15<br />15|  
|**FLT_EPSILON —**<br />**DBL_EPSILON —**<br />**LDBL_EPSILON**|Najmniejsza liczba dodatnia *x*, że *x* + 1.0 nie jest równa 1.0|1.192092896e-07F<br />2.2204460492503131e-016<br />2.2204460492503131e-016|  
|**FLT_GUARD**||0|  
|**FLT_MANT_DIG —**<br />**DBL_MANT_DIG —**<br />**LDBL_MANT_DIG**|Liczba cyfr w podstawa określony przez **flt_radix —** w mantysy zmiennoprzecinkowych. Podstawa jest 2; Dlatego te wartości określają usługi bits.|24<br />53<br />53|  
|**FLT_MAX —**<br />**DBL_MAX —**<br />**LDBL_MAX**|Maksymalna liczba zmiennoprzecinkowa można przedstawić.|3.402823466e + 38F<br />1, 7976931348623158e + 308<br />1, 7976931348623158e + 308|  
|**FLT_MAX_10_EXP —**<br />**DBL_MAX_10_EXP —**<br />**LDBL_MAX_10_EXP**|Maksymalna liczba całkowita, tak, aby 10 podniesione do tej liczby jest można przedstawić liczba zmiennoprzecinkowa.|38<br />308<br />308|  
|**FLT_MAX_EXP —**<br />**DBL_MAX_EXP —**<br />**LDBL_MAX_EXP**|Maksymalna liczba całkowita tak, aby **flt_radix —** wywoływane w celu, że numer jest reprezentacja liczba zmiennoprzecinkowa.|128<br />1024<br />1024|  
|**FLT_MIN —**<br />**DBL_MIN —**<br />**LDBL_MIN**|Minimalna wartość dodatnią.|1.175494351e-38F<br />2.2250738585072014e-308<br />2.2250738585072014e-308|  
|**FLT_MIN_10_EXP —**<br />**DBL_MIN_10_EXP —**<br />**LDBL_MIN_10_EXP**|Minimalna liczba całkowita ujemna tak, aby 10 podniesiony do tego numeru jest można przedstawić liczba zmiennoprzecinkowa.|-37<br />-307<br />-307|  
|**FLT_MIN_EXP —**<br />**DBL_MIN_EXP —**<br />**LDBL_MIN_EXP**|Minimalna liczba całkowita ujemna tak, aby **flt_radix —** wywoływane w celu, że numer jest reprezentacja liczba zmiennoprzecinkowa.|-125<br />-1021<br />-1021|  
|**FLT_NORMALIZE**||0|  
|**FLT_RADIX —**<br />**_DBL_RADIX —**<br />**_LDBL_RADIX**|Podstawa wykładnika reprezentacji.|2<br />2<br />2|  
|**FLT_ROUNDS —**<br />**_DBL_ROUNDS —**<br />**_LDBL_ROUNDS**|Tryb zaokrąglania dodawanie liczb zmiennoprzecinkowych.|1 (obok)<br />1 (obok)<br />1 (obok)|  
  
 Należy pamiętać, że informacje przedstawione w powyższej tabeli może różnić się w przyszłości implementacji.  
  
 **KOŃCOWY określonych firmy Microsoft**  
  
## <a name="see-also"></a>Zobacz też  
 [Stałe zmiennoprzecinkowe języka C](../c-language/c-floating-point-constants.md)