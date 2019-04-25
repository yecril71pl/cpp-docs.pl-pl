---
title: Stałe całkowite języka C
ms.date: 02/27/2018
helpviewer_keywords:
- integer constants
ms.assetid: fcf6b83c-2038-49ec-91ca-3d5ca1f83037
ms.openlocfilehash: 4a3d6b945f3611b8e51029c0a5ec5dc77b2cbaa0
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62326891"
---
# <a name="c-integer-constants"></a>Stałe całkowite języka C

*Stała całkowita* ułamek dziesiętny (podstawa 10), ósemkowym (podstawa 8) lub liczbą szesnastkową (podstawa 16), która reprezentuje wartość całkowitą. Użyj stałych całkowitych do reprezentowania wartości całkowitych, które nie można jej zmienić.

## <a name="syntax"></a>Składnia

*stała całkowita*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*decimal-constant* *integer-suffix*<sub>opt</sub><br/>
&nbsp;&nbsp;&nbsp;&nbsp;*octal-constant* *integer-suffix*<sub>opt</sub><br/>
&nbsp;&nbsp;&nbsp;&nbsp;*hexadecimal-constant* *integer-suffix*<sub>opt</sub><br/>

*decimal-constant*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*nonzero-digit*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*decimal-constant* *digit*<br/>

*stałej ósemkowej*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**0**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*octal-constant* *octal-digit*<br/>

*hexadecimal-constant*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*hexadecimal-prefix* *hexadecimal-digit*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*hexadecimal-constant* *hexadecimal-digit*<br/>

*Prefiks szesnastkowe*: jeden z<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**0x**  **0X**<br/>

*cyfry niezerowych*: jeden z<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**1 2 3 4 5 6 7 8 9**<br/>

*cyfrą systemu ósemkowego*: jeden z<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**0 1 2 3 4 5 6 7**<br/>

*cyfry szesnastkowe*: jeden z<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**0 1 2 3 4 5 6 7 8 9**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**b c d e f**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**A B C D E F**<br/>

*integer-suffix*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*unsigned-suffix* *long-suffix*<sub>opt</sub><br/>
&nbsp;&nbsp;&nbsp;&nbsp;*unsigned-suffix* *long-long-suffix*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*unsigned-suffix* *64-bit-integer-suffix*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*long-suffix* *unsigned-suffix*<sub>opt</sub><br/>
&nbsp;&nbsp;&nbsp;&nbsp;*long-long-suffix* *unsigned-suffix*<sub>opt</sub><br/>
&nbsp;&nbsp;&nbsp;&nbsp;*64-bit-integer-suffix*<br/>

*unsigned-suffix*: jeden z<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**u U**<br/>

*Long-suffix*: jeden z<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**l L**<br/>

*Long — long-suffix*: jeden z<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**ll LL**<br/>

*64-bit — integer-suffix*: jeden z<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**i64 I64**<br/>

**I64** i **I64** sufiksy są specyficzne dla firmy Microsoft.

Stałe całkowite są pozytywne, chyba że są poprzedzone znakiem minus (**-**). Znak minus jest interpretowany jako Jednoargumentowy operator arytmetyczny negacji. (Zobacz [jednoargumentowe operatory arytmetyczne](../c-language/unary-arithmetic-operators.md) uzyskać informacji na temat tego operatora.)

Jeśli zaczyna się stałą całkowitą **0 x** lub **0 X**, jest szesnastkowe. Jeśli zaczyna się od cyfry **0**, jest ósemkową. W przeciwnym razie jest przyjmowana dziesiętną.

Następujące stałe całkowite są równoważne:

```C
28
0x1C   /* = Hexadecimal representation for decimal 28 */
034    /* = Octal representation for decimal 28 */
```

Żadne znaki odstępu, można oddzielić cyfr stałą całkowitą. Te przykłady przedstawiają niektóre z prawidłowych stałych dziesiętną, ósemkowa i szesnastkowa.

```C
    /* Decimal Constants */
    int                 dec_int    = 28;
    unsigned            dec_uint   = 4000000024u;
    long                dec_long   = 2000000022l;
    unsigned long       dec_ulong  = 4000000000ul;
    long long           dec_llong  = 9000000000LL;
    unsigned long long  dec_ullong = 900000000001ull;
    __int64             dec_i64    = 9000000000002I64;
    unsigned __int64    dec_ui64   = 90000000000004ui64;

    /* Octal Constants */
    int                 oct_int    = 024;
    unsigned            oct_uint   = 04000000024u;
    long                oct_long   = 02000000022l;
    unsigned long       oct_ulong  = 04000000000UL;
    long long           oct_llong  = 044000000000000ll;
    unsigned long long  oct_ullong = 044400000000000001Ull;
    __int64             oct_i64    = 04444000000000000002i64;
    unsigned __int64    oct_ui64   = 04444000000000000004uI64;

    /* Hexadecimal Constants */
    int                 hex_int    = 0x2a;
    unsigned            hex_uint   = 0XA0000024u;
    long                hex_long   = 0x20000022l;
    unsigned long       hex_ulong  = 0XA0000021uL;
    long long           hex_llong  = 0x8a000000000000ll;
    unsigned long long  hex_ullong = 0x8A40000000000010uLL;
    __int64             hex_i64    = 0x4a44000000000020I64;
    unsigned __int64    hex_ui64   = 0x8a44000000000040Ui64;
```

## <a name="see-also"></a>Zobacz także

[Stałe języka C](../c-language/c-constants.md)<br/>
