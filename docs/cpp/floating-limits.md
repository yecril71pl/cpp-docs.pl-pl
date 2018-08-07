---
title: Limity liczb zmiennoprzecinkowych | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 08/03/2018
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
ms.openlocfilehash: 85a31aea113514651fc3e81ac147b5ea2974920c
ms.sourcegitcommit: 4586bfc32d8bc37ab08b24816d7fad5df709bfa3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/07/2018
ms.locfileid: "39604297"
---
# <a name="floating-limits"></a>Limity liczb zmiennoprzecinkowych

**Microsoft Specific**

W poniższej tabeli wymieniono ograniczenia dotyczące wartości stałych zmiennoprzecinkowych. Te limity są również określone w pliku standardowy nagłówek \<float.h >.  

## <a name="limits-on-floating-point-constants"></a>Limity dla stałych zmiennoprzecinkowych

|Stała|Znaczenie|Wartość|
|--------------|-------------|-----------|
|`FLT_DIG`<br/>`DBL_DIG`<br/>`LDBL_DIG`|Liczba cyfr, pytania i odpowiedzi, takie, że liczba zmiennoprzecinkowa cyfry dziesiętne funkcji pytania i odpowiedzi mogą być zaokrąglane do reprezentacja liczb zmiennoprzecinkowych i ponownie bez utraty dokładności.|6<br/>15<br/>15|
|`FLT_EPSILON`<br/>`DBL_EPSILON`<br/>`LDBL_EPSILON`|Najmniejsza liczba dodatnia, x, x + 1.0 nie jest równa 1.0.|1.192092896e-07F<br/>2.2204460492503131e-016<br/>2.2204460492503131e-016|
|`FLT_GUARD`||0|
|`FLT_MANT_DIG`<br/>`DBL_MANT_DIG`<br/>`LDBL_MANT_DIG`|Liczba cyfr w podstawy określony przez `FLT_RADIX` w mantysę zmiennoprzecinkowych. Podstawa jest 2; Dlatego te wartości określają usługi bits.|24<br/>53<br/>53|
|`FLT_MAX`<br/>`DBL_MAX`<br/>`LDBL_MAX`|Maksymalna liczba zmiennoprzecinkowa stałego.|3.402823466e + 38F<br/>1, 7976931348623158e + 308.<br/>1, 7976931348623158e + 308.|
|`FLT_MAX_10_EXP`<br/>`DBL_MAX_10_EXP`<br/>`LDBL_MAX_10_EXP`|Maksymalna liczba całkowita w taki sposób, że 10 podniesioną do tego numeru jest stałego liczba zmiennoprzecinkowa.|38<br/>308<br/>308|
|`FLT_MAX_EXP`<br/>`DBL_MAX_EXP`<br/>`LDBL_MAX_EXP`|Maksymalna liczba całkowita, `FLT_RADIX` podniesioną do, czy liczba jest liczbą stałego — liczba zmiennoprzecinkowa.|128<br/>1024<br/>1024|
|`FLT_MIN`<br/>`DBL_MIN`<br/>`LDBL_MIN`|Minimalna wartość dodatnią.|1.175494351e-38F<br/>2.2250738585072014e-308<br/>2.2250738585072014e-308|
|`FLT_MIN_10_EXP`<br/>`DBL_MIN_10_EXP`<br/>`LDBL_MIN_10_EXP`|Minimalna ujemną liczbę całkowitą taki sposób, że 10 podniesioną do tej liczby jest reprezentowanych liczbą — liczba zmiennoprzecinkowa.|-37<br/>-307<br/>-307|
|`FLT_MIN_EXP`<br/>`DBL_MIN_EXP`<br/>`LDBL_MIN_EXP`|Minimalna ujemną liczbę całkowitą, `FLT_RADIX` podniesioną do, że liczba jest reprezentowanych liczba zmiennoprzecinkowa.|-125<br/>-1021<br/>-1021|
|`FLT_NORMALIZE`||0|
|`FLT_RADIX`<br/>`_DBL_RADIX`<br/>`_LDBL_RADIX`|Podstawy reprezentacji wykładnika.|2<br/>2<br/>2|
|`FLT_ROUNDS`<br/>`_DBL_ROUNDS`<br/>`_LDBL_ROUNDS`|Trybu zaokrąglania do dodania zmiennoprzecinkowych.|1 (w pobliżu)<br/>1 (w pobliżu)<br/>1 (w pobliżu)|

> [!NOTE]
>  Informacje przedstawione w tabeli może różnić się w przyszłych wersjach produktu.

**END specyficzny dla Microsoft**

## <a name="see-also"></a>Zobacz także

[Limity liczb całkowitych](../cpp/integer-limits.md)  
