---
title: Limity dla C++ języków C i Integer
ms.date: 10/21/2019
helpviewer_keywords:
- limits, integer
- limits, integer constants
- integer limits
ms.assetid: 0c23cbd6-29fb-4d9c-b689-5984e19748de
ms.openlocfilehash: 6940f36e37ec58ca8fe23c9062928cbf90b125bd
ms.sourcegitcommit: ea9d78dbb93bf3f8841dde93dbc12bd66f6f32ff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/22/2019
ms.locfileid: "72778374"
---
# <a name="c-and-c-integer-limits"></a>Limity dla C++ języków C i Integer

**Specyficzne dla firmy Microsoft**

Limity dla typów całkowitych w C i C++ są wymienione w poniższej tabeli. Limity te są zdefiniowane w standardowym pliku nagłówkowym C `<limits.h>`. @No__t_1 C++ nagłówka biblioteki standardowej zawiera `<climits>`, w tym `<limits.h>`.

Firma Microsoft C zezwala również na deklarowanie zmiennych liczb całkowitych, które są typami całkowitymi o rozmiarze 8-, 16-, 32-lub 64-bitowym. Aby uzyskać więcej informacji na temat rozmiarów liczb całkowitych w C, zobacz [rozmiar liczb całkowitych](../c-language/c-sized-integer-types.md).

## <a name="limits-on-integer-constants"></a>Limity dla stałych całkowitych

|**Stałego**|Znaczenie|Wartość|
|------------------|-------------|-----------|
|**CHAR_BIT**|Liczba bitów w najmniejszej zmiennej, która nie jest polem bitowym.|8|
|**SCHAR_MIN**|Minimalna wartość dla zmiennej typu znak ze **znakiem**.|-128|
|**SCHAR_MAX**|Maksymalna wartość dla zmiennej typu znak ze **znakiem**.|127|
|**UCHAR_MAX**|Maksymalna wartość dla zmiennej typu **char bez znaku**.|255 (0xFF)|
|**CHAR_MIN**|Minimalna wartość dla zmiennej typu **char**.|-128; 0 w przypadku użycia opcji/J|
|**CHAR_MAX**|Maksymalna wartość dla zmiennej typu **char**.|127; 255 Jeśli użyto opcji/J|
|**MB_LEN_MAX**|Maksymalna liczba bajtów w stałej wieloznakowej.|5|
|**SHRT_MIN**|Minimalna wartość dla zmiennej typu **Short**.|-32768|
|**SHRT_MAX**|Maksymalna wartość zmiennej typu **Short**.|32767|
|**USHRT_MAX**|Maksymalna wartość zmiennej typu **unsigned Short**.|65535 (0xFFFF)|
|**INT_MIN**|Minimalna wartość dla zmiennej typu **int**.|-2147483647-1|
|**INT_MAX**|Maksymalna wartość dla zmiennej typu **int**.|2147483647|
|**UINT_MAX**|Maksymalna wartość dla zmiennej typu **unsigned int**.|4294967295 (0xffffffff)|
|**LONG_MIN**|Minimalna wartość dla zmiennej typu **Long**.|-2147483647-1|
|**LONG_MAX**|Maksymalna wartość dla zmiennej typu **Long**.|2147483647|
|**ULONG_MAX**|Maksymalna wartość dla zmiennej typu **unsigned long**.|4294967295 (0xffffffff)|
|**LLONG_MIN**|Minimalna wartość dla zmiennej typu **Long**Long.|-9 223 372 036 854 775 807-1|
|**LLONG_MAX**|Maksymalna wartość dla zmiennej typu **Long**Long.|9 223 372 036 854 775 807|
|**ULLONG_MAX**|Maksymalna wartość dla zmiennej typu **unsigned long long**.|18446744073709551615 są (0xFFFFFFFFFFFFFFFF)|

Jeśli wartość przekracza największą reprezentację całkowitą, kompilator firmy Microsoft generuje błąd.

**ZAKOŃCZENIE określonych przez firmę Microsoft**

## <a name="see-also"></a>Zobacz także

[Stałe całkowite języka C](../c-language/c-integer-constants.md)
