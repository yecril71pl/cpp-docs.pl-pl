---
title: "Limity liczb całkowitych C++ | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-language
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- limits, integer
- limits, integer constants
- integer limits
ms.assetid: 0c23cbd6-29fb-4d9c-b689-5984e19748de
caps.latest.revision: "11"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 4c1596f035da98524238e558ffe23816730aa42b
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="c-integer-limits"></a>Limity liczb całkowitych C++
**Dotyczące firmy Microsoft**  
  
 W poniższej tabeli wymieniono limity dla typów całkowitych. Ograniczenia te są zdefiniowane w standardowy nagłówek limity plików. H. Microsoft C umożliwia również deklaracji zmiennych całkowite o określonym rozmiarze, które typy całkowite o rozmiarze 8-16- i 32-bitowej. Aby uzyskać więcej informacji o rozmiarze liczb całkowitych, zobacz [typów całkowitych o rozmiarze](../c-language/c-sized-integer-types.md).  
  
### <a name="limits-on-integer-constants"></a>Limity stałe całkowite  
  
|**Stałe**|Znaczenie|Wartość|  
|------------------|-------------|-----------|  
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
|**INT_MIN —**|Minimalna wartość dla zmiennej typu `int`.|-2147483647 - 1|  
|**INT_MAX —**|Maksymalna wartość dla zmiennej typu `int`.|2147483647|  
|**UINT_MAX —**|Maksymalna wartość dla zmiennej typu `unsigned int`.|4294967295 (0xffffffff)|  
|**LONG_MIN —**|Minimalna wartość dla zmiennej typu **długi**.|-2147483647 - 1|  
|**LONG_MAX —**|Maksymalna wartość dla zmiennej typu **długi**.|2147483647|  
|**ULONG_MAX —**|Maksymalna wartość dla zmiennej typu `unsigned long`.|4294967295 (0xffffffff)|  
  
 Jeśli wartość przekracza reprezentacją największa liczba całkowita, kompilator Microsoft generuje błąd.  
  
 **KOŃCOWY określonych firmy Microsoft**  
  
## <a name="see-also"></a>Zobacz też  
 [Stałe całkowite języka C](../c-language/c-integer-constants.md)