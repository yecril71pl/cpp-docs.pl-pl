---
title: Limity liczb całkowitych | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 01/29/2018
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- integral limits
- limits, integer
- limits.h header file
- integer limits
ms.assetid: 6922bdbf-0f49-443b-bc03-ee182e4cbd57
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 5b9a516ef366952f9d55e16891dfcb7bb81fac7e
ms.sourcegitcommit: 2b9e8af9b7138f502ffcba64e2721f7ef52af23b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/01/2018
ms.locfileid: "39406022"
---
# <a name="integer-limits"></a>Limity liczb całkowitych

**Microsoft Specific**

Limity dla typów całkowitoliczbowych są wymienione w poniższej tabeli. Limity te są również określone w pliku standardowy nagłówek < limits.h >.

## <a name="limits-on-integer-constants"></a>Limity dla stałych liczba całkowita

|Stała|Znaczenie|Wartość|
|--------------|-------------|-----------|
|CHAR_BIT|Liczba bitów w najmniejszym zmiennej, która nie jest polem bitowym.|8|
|SCHAR_MIN|Minimalna wartość do zmiennej typu **podpisany char**.|-128|
|SCHAR_MAX|Maksymalna wartość dla zmiennej typu **podpisany char**.|127|
|UCHAR_MAX|Maksymalna wartość dla zmiennej typu **unsigned char**.|255 (0xff)|
|CHAR_MIN|Minimalna wartość do zmiennej typu **char**.|od -128; 0, jeśli używana z opcją/j.|
|CHAR_MAX|Maksymalna wartość dla zmiennej typu **char**.|127; 255, jeśli używana z opcją/j.|
|MB_LEN_MAX|Maksymalna liczba bajtów w stała multicharacter składa.|5|
|SHRT_MIN|Minimalna wartość do zmiennej typu **krótki**.|-32768|
|SHRT_MAX|Maksymalna wartość dla zmiennej typu **krótki**.|32767|
|USHRT_MAX|Maksymalna wartość dla zmiennej typu **typ unsigned short**.|65535 (0xffff)|
|INT_MIN|Minimalna wartość do zmiennej typu **int**.|-2147483648|
|INT_MAX|Maksymalna wartość dla zmiennej typu **int**.|2147483647|
|UINT_MAX|Maksymalna wartość dla zmiennej typu **unsigned int**.|4294967295 (0xffffffff)|
|LONG_MIN|Minimalna wartość do zmiennej typu **długie**.|-2147483648|
|LONG_MAX|Maksymalna wartość dla zmiennej typu **długie**.|2147483647|
|ULONG_MAX|Maksymalna wartość dla zmiennej typu **unsigned long**.|4294967295 (0xffffffff)|
|LLONG_MIN|Minimalna wartość do zmiennej typu **długi długi**|-9223372036854775808|
|LLONG_MAX|Maksymalna wartość dla zmiennej typu **długi długi**|9223372036854775807|
|ULLONG_MAX|Maksymalna wartość dla zmiennej typu **unsigned long long**|18446744073709551615 (0xffffffffffffffff)|

Jeśli wartość przekracza największych reprezentacja liczby całkowitej, kompilator Microsoft generuje błąd.

**END specyficzny dla Microsoft**

## <a name="see-also"></a>Zobacz także
 [Limity liczb zmiennoprzecinkowych](../cpp/floating-limits.md)  