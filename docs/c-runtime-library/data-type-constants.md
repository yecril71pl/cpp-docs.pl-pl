---
title: "Stałe typu danych | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- FLT_MIN
- SHRT_MAX
- CHAR_MIN
- MB_LEN_MAX
- DBL_EPSILON
- SHRT_MIN
- _FLT_RADIX
- FLT_DIG
- FLT_MAX_10_EXP
- FLT_MANT_DIG
- DBL_MAX_EXP
- SCHAR_MIN
- SCHAR_MAX
- DBL_MIN
- FLT_MIN_10_EXP
- _DBL_ROUNDS
- USHRT_MAX
- FLT_MAX_EXP
- LONG_MAX
- DBL_MAX
- DBL_DIG
- FLT_MIN_EXP
- INT_MIN
- DBL_MIN_10_EXP
- CHAR_BIT
- INT_MAX
- ULONG_MAX
- DBL_MIN_EXP
- LONG_MIN
- _FLT_ROUNDS
- DBL_MANT_DIG
- _DBL_RADIX
- CHAR_MAX
- FLT_MAX
- DBL_MAX_10_EXP
- UCHAR_MAX
- FLT_EPSILON
- UINT_MAX
dev_langs: C++
helpviewer_keywords:
- DBL_MAX_EXP constant
- _DBL_RADIX constant
- FLT_MIN_EXP constant
- DBL_EPSILON constant
- INT_MIN constant
- FLT_EPSILON constant
- DBL_MANT_DIG constant
- _FLT_RADIX constant
- DBL_MIN constant
- USHRT_MAX constant
- FLT_MAX_10_EXP constant
- _FLT_ROUNDS constant
- data type constants [C++]
- _DBL_ROUNDS constant
- CHAR_MAX constant
- FLT_MAX_EXP constant
- FLT_MIN constant
- CHAR_MIN constant
- FLT_MIN_10_EXP constant
- DBL_MIN_EXP constant
- SCHAR_MAX constant
- FLT_RADIX constant
- CHAR_BIT constant
- UCHAR_MAX constant
- DBL_RADIX constant
- FLT_ROUNDS constant
- LONG_MIN constant
- SHRT_MAX constant
- LONG_MAX constant
- DBL_MAX_10_EXP constant
- DBL_MIN_10_EXP constant
- INT_MAX constant
- constants [C++], data type
- ULONG_MAX constant
- FLT_DIG constant
- MB_LEN_MAX constant
- DBL_DIG constant
- SHRT_MIN constant
- DBL_MAX constant
- DBL_ROUNDS constant
- FLT_MAX constant
- UINT_MAX constant
- FLT_MANT_DIG constant
- SCHAR_MIN constant
ms.assetid: c0f1c405-0465-41d5-b5ff-e81cdb6f1622
caps.latest.revision: "6"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 1702065a8157596d4366af31fed3f2a80d53149c
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="data-type-constants"></a>Typ danych — Stałe
Stałe typu danych są zależne od implementacji zakresów wartości dozwolone na typy całkowite danych. Stałe wymienione poniżej Przypisz zakresy na typy całkowite danych i są definiowane w granicach. H.  
  
> [!NOTE]
>  /J — opcja kompilatora zmienia domyślne `char` typ `unsigned`.  
  
|Stała|Wartość|Znaczenie|  
|--------------|-----------|-------------|  
|**SCHAR_MAX —**|127|Maksymalna podpisany `char` wartość|  
|**SCHAR_MIN —**|-128|Co najmniej podpisany `char` wartość|  
|**UCHAR_MAX —**|255 (0xff)|Maksymalna `unsigned char` wartość|  
|**CHAR_BIT —**|8|Liczba bitów`char`|  
|**USHRT_MAX —**|65535 (0xffff)|Maksymalna **niepodpisane krótko** wartość|  
|**SHRT_MAX —**|32767|Maksymalna (ze znakiem) **krótki** wartość|  
|**SHRT_MIN —**|-32768|Minimalna (ze znakiem) **krótki** wartość|  
|**UINT_MAX —**|4294967295 (0xffffffff)|Maksymalna `unsigned int` wartość|  
|**ULONG_MAX —**|4294967295 (0xffffffff)|Maksymalna `unsigned long` wartość|  
|**INT_MAX —**|2147483647|Maksymalna (ze znakiem) `int` wartość|  
|**INT_MIN —**|-2147483647-1|Minimalna (ze znakiem) `int` wartość|  
|**LONG_MAX —**|2147483647|Maksymalna (ze znakiem) **długi** wartość|  
|**LONG_MIN —**|-2147483647-1|Minimalna (ze znakiem) **długi** wartość|  
|**CHAR_MAX —**|127 (jeśli jest używana z opcją / 255)|Maksymalna `char` wartość|  
|**CHAR_MIN —**|-128 (0, jeśli używana z opcją /)|Minimalna `char` wartość|  
|**MB_LEN_MAX —**|2|Maksymalna liczba bajtów w wielobajtowe`char`|  
|**_I64_MAX**|9223372036854775807|Maksymalna __ (podpisanego)**int64** wartość|  
|**_I64_MIN**|-9223372036854775807-1|Minimalna __ (podpisanego)**int64** wartość|  
|**_UI64_MAX**|0xffffffffffffffff|Maksymalna __ (bez znaku)**int64** wartość|  
  
 Stałe zapewniają zakresu i inne właściwości **podwójne** i **float** typy danych i są zdefiniowane w FLOAT. H:  
  
|Stała|Wartość|Opis|  
|--------------|-----------|-----------------|  
|**DBL_DIG —**|15|Liczba cyfr dziesiętnych dokładności|  
|**DBL_EPSILON —**|2.2204460492503131e-016|Najmniejsza tak, aby 1.0 +**dbl_epsilon —** ! = 1.0|  
|**DBL_MANT_DIG —**|53|Liczba bitów mantysy|  
|**DBL_MAX —**|1, 7976931348623158e + 308|Wartość maksymalna|  
|**DBL_MAX_10_EXP —**|308|Maksymalna wykładnik dziesiętną|  
|**DBL_MAX_EXP —**|1024|Maksymalna wykładnik binarne|  
|**DBL_MIN —**|2.2250738585072014e-308|Minimalna wartość dodatnią|  
|**DBL_MIN_10_EXP —**|(-307)|Minimalna wykładnik dziesiętną|  
|**DBL_MIN_EXP —**|(-1021)|Minimalna wykładnik binarne|  
|**_DBL_RADIX —**|2|Podstawa wykładnika|  
|**_DBL_ROUNDS —**|1|Dodanie zaokrąglania: w pobliżu|  
|**FLT_DIG —**|6|Liczba cyfr dziesiętnych dokładności|  
|**FLT_EPSILON —**|1.192092896e-07F|Najmniejsza tak, aby 1.0 +**flt_epsilon —** ! = 1.0|  
|**FLT_MANT_DIG —**|24|Liczba bitów mantysy|  
|**FLT_MAX —**|3.402823466e + 38F|Wartość maksymalna|  
|**FLT_MAX_10_EXP —**|38|Maksymalna wykładnik dziesiętną|  
|**FLT_MAX_EXP —**|128|Maksymalna wykładnik binarne|  
|**FLT_MIN —**|1.175494351e-38F|Minimalna wartość dodatnią|  
|**FLT_MIN_10_EXP —**|(-37)|Minimalna wykładnik dziesiętną|  
|**FLT_MIN_EXP —**|(-125)|Minimalna wykładnik binarne|  
|**FLT_RADIX —**|2|Podstawa wykładnika|  
|**FLT_ROUNDS —**|1|Dodanie zaokrąglania: w pobliżu|  
  
## <a name="see-also"></a>Zobacz też  
 [Stałe globalne](../c-runtime-library/global-constants.md)