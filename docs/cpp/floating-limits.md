---
title: Limity liczb zmiennoprzecinkowych | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- ranges, floating-point constants
- floating-point constants, limits
- float.h header file
- limits, floating-point constants
- floating-point numbers [C++]
- floating limits
ms.assetid: fc718652-1f4c-4ed8-af60-0e769637459c
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 9a111d2ea3e8e5503754b0d9c0c1a4f69170a41c
ms.sourcegitcommit: 2b9e8af9b7138f502ffcba64e2721f7ef52af23b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/01/2018
ms.locfileid: "39401762"
---
# <a name="floating-limits"></a>Limity liczb zmiennoprzecinkowych
**Microsoft Specific**  
  
 W poniższej tabeli wymieniono ograniczenia dotyczące wartości stałych zmiennoprzecinkowych. Te limity są również określone w pliku standardowy nagłówek \<float.h >.  
  
### <a name="limits-on-floating-point-constants"></a>Limity dla stałych zmiennoprzecinkowych  
  
|Stała|Znaczenie|Wartość|  
|--------------|-------------|-----------|  
|FLT_DIG DBL_DIG LDBL_DIG|Liczba cyfr, pytania i odpowiedzi, takie, że liczba zmiennoprzecinkowa cyfry dziesiętne funkcji pytania i odpowiedzi mogą być zaokrąglane do reprezentacja liczb zmiennoprzecinkowych i ponownie bez utraty dokładności.|6 15 15|  
|FLT_EPSILON DBL_EPSILON LDBL_EPSILON|Najmniejsza liczba dodatnia, x, x + 1.0 nie jest równa 1.0.|1.192092896e-07F 2.2204460492503131e-016 2.2204460492503131e-016|  
|FLT_GUARD||0|  
|FLT_MANT_DIG DBL_MANT_DIG LDBL_MANT_DIG|Liczba cyfr w podstawy określone przez FLT_RADIX w mantysę zmiennoprzecinkowych. Podstawa jest 2; Dlatego te wartości określają usługi bits.|24 53 53|  
|FLT_MAX DBL_MAX LDBL_MAX|Maksymalna liczba zmiennoprzecinkowa stałego.|3.402823466e+38F 1.7976931348623158e+308 1.7976931348623158e+308|  
|FLT_MAX_10_EXP DBL_MAX_10_EXP LDBL_MAX_10_EXP|Maksymalna liczba całkowita w taki sposób, że 10 podniesioną do tego numeru jest stałego liczba zmiennoprzecinkowa.|38 308 308|  
|FLT_MAX_EXP DBL_MAX_EXP LDBL_MAX_EXP|Maksymalna liczba całkowita, tak, aby FLT_RADIX podniesioną do tej liczby jest liczbą stałego — liczba zmiennoprzecinkowa.|128 1024 1024|  
|FLT_MIN DBL_MIN LDBL_MIN|Minimalna wartość dodatnią.|1.175494351e-38F 2.2250738585072014e-308 2.2250738585072014e-308|  
|FLT_MIN_10_EXP DBL_MIN_10_EXP LDBL_MIN_10_EXP|Minimalna ujemną liczbę całkowitą taki sposób, że 10 podniesioną do tej liczby jest reprezentowanych liczbą — liczba zmiennoprzecinkowa.|-37<br /><br /> -307<br /><br /> -307|  
|FLT_MIN_EXP DBL_MIN_EXP LDBL_MIN_EXP|Minimalna ujemną liczbę całkowitą taki sposób, że FLT_RADIX podniesioną do tej liczby jest reprezentowanych liczba zmiennoprzecinkowa.|-125<br /><br /> -1021<br /><br /> -1021|  
|FLT_NORMALIZE||0|  
|FLT_RADIX _DBL_RADIX _LDBL_RADIX|Podstawy reprezentacji wykładnika.|2 2 2|  
|FLT_ROUNDS _DBL_ROUNDS _LDBL_ROUNDS|Trybu zaokrąglania do dodania zmiennoprzecinkowych.|1 (w) 1 (w) 1 (w pobliżu)|  
  
> [!NOTE]
>  Informacje przedstawione w tabeli może różnić się w przyszłych wersjach produktu.  
  
**END specyficzny dla Microsoft**  
  
## <a name="see-also"></a>Zobacz także  
 [Limity liczb całkowitych](../cpp/integer-limits.md)