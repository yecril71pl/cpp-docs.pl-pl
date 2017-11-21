---
title: "Limity liczb całkowitych | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs: C++
helpviewer_keywords:
- integral limits
- limits, integer
- LIMITS.H header file
- integer limits
ms.assetid: 6922bdbf-0f49-443b-bc03-ee182e4cbd57
caps.latest.revision: "8"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: f36633fb6b94e820ddb8884a387004889b33d9d6
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="integer-limits"></a>Limity liczb całkowitych
**Dotyczące firmy Microsoft**  
  
 W poniższej tabeli wymieniono limity dla typów całkowitych. Te limity również są definiowane w standardowy nagłówek limity plików. H.  
  
### <a name="limits-on-integer-constants"></a>Limity stałe całkowite  
  
|Stała|Znaczenie|Wartość|  
|--------------|-------------|-----------|  
|**CHAR_BIT —**|Liczba bitów w najmniejszą zmiennej, która nie jest polem bitowym.|8|  
|**SCHAR_MIN —**|Minimalna wartość dla zmiennej typu **podpisany char**.|-128|  
|**SCHAR_MAX —**|Maksymalna wartość dla zmiennej typu **podpisany char**.|127|  
|**UCHAR_MAX —**|Maksymalna wartość dla zmiennej typu `unsigned char`.|255 (0xff)|  
|**CHAR_MIN —**|Minimalna wartość dla zmiennej typu `char`.|-128; 0, jeśli używana z opcją /|  
|**CHAR_MAX —**|Maksymalna wartość dla zmiennej typu `char`.|127; 255, jeśli używana z opcją /|  
|**MB_LEN_MAX —**|Maksymalna liczba bajtów w literał stałej.|5|  
|**SHRT_MIN —**|Minimalna wartość dla zmiennej typu **krótki**.|-32768|  
|**SHRT_MAX —**|Maksymalna wartość dla zmiennej typu **krótki**.|32767|  
|**USHRT_MAX —**|Maksymalna wartość dla zmiennej typu **niepodpisane krótko**.|65535 (0xffff)|  
|**INT_MIN —**|Minimalna wartość dla zmiennej typu `int`.|-2147483648|  
|**INT_MAX —**|Maksymalna wartość dla zmiennej typu `int`.|2147483647|  
|**UINT_MAX —**|Maksymalna wartość dla zmiennej typu `unsigned int`.|4294967295 (0xffffffff)|  
|**LONG_MIN —**|Minimalna wartość dla zmiennej typu **długi**.|-2147483648|  
|**LONG_MAX —**|Maksymalna wartość dla zmiennej typu **długi**.|2147483647|  
|**ULONG_MAX —**|Maksymalna wartość dla zmiennej typu `unsigned long`.|4294967295 (0xffffffff)|  
|**_I64_MIN**|Minimalna wartość dla zmiennej typu`__int64`|-9223372036854775808|  
|**_I64_MAX**|Maksymalna wartość dla zmiennej typu`__int64`|9223372036854775807|  
|**_UI64_MAX**|Maksymalna wartość dla zmiennej typu **__int64 bez znaku**|18446744073709551615 są (0xffffffffffffffff)|  
  
 Jeśli wartość przekracza reprezentacją największa liczba całkowita, kompilator Microsoft generuje błąd.  
  
**KOŃCOWY określonych firmy Microsoft**  
  
## <a name="see-also"></a>Zobacz też  
 [Limity liczb zmiennoprzecinkowych](../cpp/floating-limits.md)