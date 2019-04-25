---
title: Limity liczb całkowitych C++
ms.date: 01/29/2018
helpviewer_keywords:
- limits, integer
- limits, integer constants
- integer limits
ms.assetid: 0c23cbd6-29fb-4d9c-b689-5984e19748de
ms.openlocfilehash: 057da1ac8e4549a05d10a01cc3aead678045d9c5
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62312430"
---
# <a name="c-integer-limits"></a>Limity liczb całkowitych C++

**Microsoft Specific**

Limity dla typów całkowitoliczbowych są wymienione w poniższej tabeli. Limity te są definiowane w standardowy nagłówek limity plików. H. Microsoft C umożliwia również deklaracji zmiennych wielkości liczb całkowitych, które są typów całkowitych o rozmiarze 8-, 16- i 32-bitowy. Aby uzyskać więcej informacji na temat liczb całkowitych o rozmiarze, zobacz [typy liczb całkowitych o rozmiarze](../c-language/c-sized-integer-types.md).

## <a name="limits-on-integer-constants"></a>Limity dla stałych liczba całkowita

|**Stałe**|Znaczenie|Wartość|
|------------------|-------------|-----------|
|**CHAR_BIT**|Liczba bitów w najmniejszym zmiennej, która nie jest polem bitowym.|8|
|**SCHAR_MIN**|Minimalna wartość do zmiennej typu **podpisany char**.|-128|
|**SCHAR_MAX**|Maksymalna wartość dla zmiennej typu **podpisany char**.|127|
|**UCHAR_MAX**|Maksymalna wartość dla zmiennej typu **unsigned char**.|255 (0xff)|
|**CHAR_MIN**|Minimalna wartość do zmiennej typu **char**.|od -128; 0, jeśli używana z opcją/j.|
|**CHAR_MAX**|Maksymalna wartość dla zmiennej typu **char**.|127; 255, jeśli używana z opcją/j.|
|**MB_LEN_MAX**|Maksymalna liczba bajtów w stała multicharacter składa.|5|
|**SHRT_MIN**|Minimalna wartość do zmiennej typu **krótki**.|-32768|
|**SHRT_MAX**|Maksymalna wartość dla zmiennej typu **krótki**.|32767|
|**USHRT_MAX**|Maksymalna wartość dla zmiennej typu **typ unsigned short**.|65535 (0xffff)|
|**INT_MIN**|Minimalna wartość do zmiennej typu **int**.|-2147483647 - 1|
|**INT_MAX**|Maksymalna wartość dla zmiennej typu **int**.|2147483647|
|**UINT_MAX**|Maksymalna wartość dla zmiennej typu **unsigned int**.|4294967295 (0xffffffff)|
|**LONG_MIN**|Minimalna wartość do zmiennej typu **długie**.|-2147483647 - 1|
|**LONG_MAX**|Maksymalna wartość dla zmiennej typu **długie**.|2147483647|
|**ULONG_MAX**|Maksymalna wartość dla zmiennej typu **unsigned long**.|4294967295 (0xffffffff)|

Jeśli wartość przekracza największych reprezentacja liczby całkowitej, kompilator Microsoft generuje błąd.

**END specyficzny dla Microsoft**

## <a name="see-also"></a>Zobacz także

[Stałe całkowite języka C](../c-language/c-integer-constants.md)
