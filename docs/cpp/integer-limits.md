---
title: Limity liczb całkowitych
ms.date: 01/29/2018
helpviewer_keywords:
- integral limits
- limits, integer
- limits.h header file
- integer limits
ms.assetid: 6922bdbf-0f49-443b-bc03-ee182e4cbd57
ms.openlocfilehash: 75cd05e73aba2d2e82e8077e0a289d8b0fae7ec4
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/24/2020
ms.locfileid: "80178227"
---
# <a name="integer-limits"></a>Limity liczb całkowitych

**Specyficzne dla firmy Microsoft**

Limity dla typów całkowitych są wymienione w poniższej tabeli. Te limity są również zdefiniowane w standardowym pliku nagłówkowym \<limity. h >.

## <a name="limits-on-integer-constants"></a>Limity dla stałych całkowitych

|Stały|Znaczenie|Wartość|
|--------------|-------------|-----------|
|CHAR_BIT|Liczba bitów w najmniejszej zmiennej, która nie jest polem bitowym.|8|
|SCHAR_MIN|Minimalna wartość dla zmiennej typu znak ze **znakiem**.|-128|
|SCHAR_MAX|Maksymalna wartość dla zmiennej typu znak ze **znakiem**.|127|
|UCHAR_MAX|Maksymalna wartość dla zmiennej typu **char bez znaku**.|255 (0xFF)|
|CHAR_MIN|Minimalna wartość dla zmiennej typu **char**.|-128; 0 w przypadku użycia opcji/J|
|CHAR_MAX|Maksymalna wartość dla zmiennej typu **char**.|127; 255 Jeśli użyto opcji/J|
|MB_LEN_MAX|Maksymalna liczba bajtów w stałej wieloznakowej.|5|
|SHRT_MIN|Minimalna wartość dla zmiennej typu **Short**.|-32768|
|SHRT_MAX|Maksymalna wartość zmiennej typu **Short**.|32767|
|USHRT_MAX|Maksymalna wartość zmiennej typu **unsigned Short**.|65535 (0xffff)|
|INT_MIN|Minimalna wartość dla zmiennej typu **int**.|-2147483648|
|INT_MAX|Maksymalna wartość dla zmiennej typu **int**.|2147483647|
|UINT_MAX|Maksymalna wartość dla zmiennej typu **unsigned int**.|4294967295 (0xffffffff)|
|LONG_MIN|Minimalna wartość dla zmiennej typu **Long**.|-2147483648|
|LONG_MAX|Maksymalna wartość dla zmiennej typu **Long**.|2147483647|
|ULONG_MAX|Maksymalna wartość dla zmiennej typu **unsigned long**.|4294967295 (0xffffffff)|
|LLONG_MIN|Minimalna wartość dla zmiennej typu **Long** Long|-9223372036854775808|
|LLONG_MAX|Maksymalna wartość dla zmiennej typu **Long** Long|9223372036854775807|
|ULLONG_MAX|Maksymalna wartość dla zmiennej typu **unsigned long long**|18446744073709551615 (0xffffffffffffffff)|

Jeśli wartość przekracza największą reprezentację całkowitą, kompilator firmy Microsoft generuje błąd.

**ZAKOŃCZENIE określonych przez firmę Microsoft**

## <a name="see-also"></a>Zobacz też

[Limity liczb zmiennoprzecinkowych](../cpp/floating-limits.md)
