---
title: Limity liczb zmiennoprzecinkowych | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs: C++
helpviewer_keywords:
- ranges, floating-point constants
- floating-point constants, limits
- FLOAT.H header file
- limits, floating-point constants
- floating-point numbers [C++]
- floating limits
ms.assetid: fc718652-1f4c-4ed8-af60-0e769637459c
caps.latest.revision: "7"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: cb5257b9b70750172a79b4c22a7da6c728664807
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="floating-limits"></a>Limity liczb zmiennoprzecinkowych
**Dotyczące firmy Microsoft**  
  
 W poniższej tabeli wymieniono limity dla stałych zmiennoprzecinkowych wartości. Te limity również są zdefiniowane w pliku standardowy nagłówek typu FLOAT. H.  
  
### <a name="limits-on-floating-point-constants"></a>Limity dla stałych zmiennoprzecinkowych  
  
|Stała|Znaczenie|Wartość|  
|--------------|-------------|-----------|  
|FLT_DIG — DBL_DIG — LDBL_DIG|Liczba cyfr, q, taki, że liczba zmiennoprzecinkowa z cyfr dziesiętnych q mogą być zaokrąglane do odwzorowanie liczby zmiennoprzecinkowej i ponownie bez utraty dokładności.|6 15 15|  
|FLT_EPSILON — DBL_EPSILON — LDBL_EPSILON|Najmniejsza liczba dodatnia x, że x + 1.0 nie jest równa 1.0.|1.192092896e-07F 2.2204460492503131e-016 2.2204460492503131e-016|  
|FLT_GUARD||0|  
|FLT_MANT_DIG — DBL_MANT_DIG — LDBL_MANT_DIG|Liczba cyfr w podstawa określone przez flt_radix — w mantysy zmiennoprzecinkowych. Podstawa jest 2; Dlatego te wartości określają usługi bits.|24 53 53|  
|FLT_MAX — DBL_MAX — LDBL_MAX|Maksymalna liczba zmiennoprzecinkowa można przedstawić.|3.402823466e + 38F 1, 7976931348623158e + 308 1, 7976931348623158e + 308|  
|FLT_MAX_10_EXP — DBL_MAX_10_EXP — LDBL_MAX_10_EXP|Maksymalna liczba całkowita, tak, aby 10 podniesione do tej liczby jest można przedstawić liczba zmiennoprzecinkowa.|38 308 308|  
|FLT_MAX_EXP — DBL_MAX_EXP — LDBL_MAX_EXP|Maksymalna liczba całkowita tak, aby flt_radix — zaokrąglona do tej liczby jest liczbą zmiennoprzecinkową punktu można przedstawić.|128 1024 1024|  
|FLT_MIN — DBL_MIN — LDBL_MIN|Minimalna wartość dodatnią.|1.175494351e-38F 2.2250738585072014e-308 2.2250738585072014e-308|  
|FLT_MIN_10_EXP — DBL_MIN_10_EXP — LDBL_MIN_10_EXP|Minimalnej liczbie całkowitej ujemna tak, aby 10 podniesiony do tego numeru jest liczbą zmiennoprzecinkową punktu można przedstawić.|-37<br /><br /> -307<br /><br /> -307|  
|FLT_MIN_EXP — DBL_MIN_EXP — LDBL_MIN_EXP|Minimalna liczba całkowita ujemna tak, aby flt_radix — podniesiony do tego numeru jest można przedstawić liczba zmiennoprzecinkowa.|-125<br /><br /> -1021<br /><br /> -1021|  
|FLT_NORMALIZE||0|  
|FLT_RADIX — _DBL_RADIX — _LDBL_RADIX|Podstawa wykładnika reprezentacji.|2 2 2|  
|FLT_ROUNDS — _DBL_ROUNDS — _LDBL_ROUNDS|Tryb zaokrąglania dodawanie liczb zmiennoprzecinkowych.|1 (obok) 1 (obok) 1 (obok)|  
  
> [!NOTE]
>  Informacje w tabeli może różnić się w przyszłych wersjach produktu.  
  
**KOŃCOWY określonych firmy Microsoft**  
  
## <a name="see-also"></a>Zobacz też  
 [Limity liczb całkowitych](../cpp/integer-limits.md)