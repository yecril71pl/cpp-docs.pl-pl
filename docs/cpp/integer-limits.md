---
title: "Limity liczb całkowitych | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 01/29/2018
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- integral limits
- limits, integer
- limits.h header file
- integer limits
ms.assetid: 6922bdbf-0f49-443b-bc03-ee182e4cbd57
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: a5fc79f225d340777751ca513c0fb47dd33e17ad
ms.sourcegitcommit: 185e11ab93af56ffc650fe42fb5ccdf1683e3847
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/29/2018
---
# <a name="integer-limits"></a>Limity liczb całkowitych

**Microsoft Specific**

W poniższej tabeli wymieniono limity dla typów całkowitych. Te limity również są zdefiniowane w pliku standardowy nagłówek < Limits.h — >.

## <a name="limits-on-integer-constants"></a>Limity stałe całkowite

|Stała|Znaczenie|Wartość|
|--------------|-------------|-----------|
|**CHAR_BIT**|Liczba bitów w najmniejszą zmiennej, która nie jest polem bitowym.|8|
|**SCHAR_MIN**|Minimalna wartość dla zmiennej typu **podpisany char**.|-128|
|**SCHAR_MAX**|Maksymalna wartość dla zmiennej typu **podpisany char**.|127|
|**UCHAR_MAX**|Maksymalna wartość dla zmiennej typu **unsigned char**.|255 (0xff)|
|**CHAR_MIN**|Minimalna wartość dla zmiennej typu **char**.|-128; 0, jeśli używana z opcją /|
|**CHAR_MAX**|Maksymalna wartość dla zmiennej typu **char**.|127; 255, jeśli używana z opcją /|
|**MB_LEN_MAX**|Maksymalna liczba bajtów w literał stałej.|5|
|**SHRT_MIN**|Minimalna wartość dla zmiennej typu **krótki**.|-32768|
|**SHRT_MAX**|Maksymalna wartość dla zmiennej typu **krótki**.|32767|
|**USHRT_MAX**|Maksymalna wartość dla zmiennej typu **niepodpisane krótko**.|65535 (0xffff)|
|**INT_MIN**|Minimalna wartość dla zmiennej typu **int**.|-2147483648|
|**INT_MAX**|Maksymalna wartość dla zmiennej typu **int**.|2147483647|
|**UINT_MAX**|Maksymalna wartość dla zmiennej typu **unsigned int**.|4294967295 (0xffffffff)|
|**LONG_MIN —**|Minimalna wartość dla zmiennej typu **długi**.|-2147483648|
|**LONG_MAX**|Maksymalna wartość dla zmiennej typu **długi**.|2147483647|
|**ULONG_MAX**|Maksymalna wartość dla zmiennej typu **unsigned long**.|4294967295 (0xffffffff)|
|**LLONG_MIN**|Minimalna wartość dla zmiennej typu **długi czas**|-9223372036854775808|
|**LLONG_MAX**|Maksymalna wartość dla zmiennej typu **długi czas**|9223372036854775807|
|**ULLONG_MAX**|Maksymalna wartość dla zmiennej typu **unsigned long long**|18446744073709551615 (0xffffffffffffffff)|

Jeśli wartość przekracza reprezentacją największa liczba całkowita, kompilator Microsoft generuje błąd.

**KOŃCOWY określonych firmy Microsoft**

## <a name="see-also"></a>Zobacz też

[Limity liczb zmiennoprzecinkowych](../cpp/floating-limits.md)  
