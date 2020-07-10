---
title: intrinsic, pragma
description: Wewnętrzna pragma MSVC jest używana do określania obsługiwanych funkcji wewnętrznych do użycia jako elementy wewnętrzne.
ms.date: 07/08/2020
f1_keywords:
- intrinsic_CPP
- vc-pragma.intrinsic
helpviewer_keywords:
- intrinsic pragma
- pragmas, intrinsic
ms.assetid: 25c86ac7-ef40-47b7-a2c0-fada9c5dc3c5
ms.openlocfilehash: 31f4ebc2fdd4c5c984160d441b4e0a723c686a46
ms.sourcegitcommit: 80c8a512b361bd84e38958beb1a1bf6db7434021
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/09/2020
ms.locfileid: "86180958"
---
# <a name="intrinsic-pragma"></a>`intrinsic`pragm

Określa, że wywołania funkcji określonych na liście argumentów pragma są wewnętrzne.

## <a name="syntax"></a>Składnia

> **`#pragma intrinsic(`** *`function1`* [**`,`** _`function2`_ ... ] **`)`**

## <a name="remarks"></a>Uwagi

**`intrinsic`** Pragma informuje kompilator, że funkcja ma znane zachowanie. Kompilator może wywołać funkcję i nie zamieniać wywołania funkcji z instrukcjami wbudowanymi, jeśli spowoduje to lepszą wydajność.

Poniżej wymieniono funkcje biblioteki z formularzami wewnętrznymi. Gdy **`intrinsic`** pragma jest widoczna, zacznie obowiązywać przy pierwszej definicji funkcji zawierającej określoną funkcję wewnętrzną. Efekt jest kontynuowany na końcu pliku źródłowego lub do wyglądu `function` dyrektywy pragma określającej tę samą funkcję wewnętrzną. **`intrinsic`** Dyrektywy pragma można używać tylko poza definicją funkcji, na poziomie globalnym.

Następujące funkcje mają formy wewnętrzne i są używane w przypadku określenia [`/Oi`](../build/reference/oi-generate-intrinsic-functions.md) :

|  |  |  |  |
|--|--|--|--|
| [`_disable`](../intrinsics/disable.md) | [`_outp`](../c-runtime-library/outp-outpw-outpd.md) | [`fabs`](../c-runtime-library/reference/fabs-fabsf-fabsl.md) | [`strcmp`](../c-runtime-library/reference/strcmp-wcscmp-mbscmp.md) |
| [`_enable`](../intrinsics/enable.md) | [`_outpw`](../c-runtime-library/outp-outpw-outpd.md) | [`labs`](../c-runtime-library/reference/abs-labs-llabs-abs64.md) | [`strcpy`](../c-runtime-library/reference/strcpy-wcscpy-mbscpy.md) |
| [`_inp`](../c-runtime-library/inp-inpw-inpd.md) | [`_rotl`](../c-runtime-library/reference/rotl-rotl64-rotr-rotr64.md) | [`memcmp`](../c-runtime-library/reference/memcmp-wmemcmp.md) | [`strlen`](../c-runtime-library/reference/strlen-wcslen-mbslen-mbslen-l-mbstrlen-mbstrlen-l.md) |
| [`_inpw`](../c-runtime-library/inp-inpw-inpd.md) | [`_rotr`](../c-runtime-library/reference/rotl-rotl64-rotr-rotr64.md) | [`memcpy`](../c-runtime-library/reference/memcpy-wmemcpy.md) |  |
| [`_lrotl`](../c-runtime-library/reference/lrotl-lrotr.md) | [`_strset`](../c-runtime-library/reference/strset-strset-l-wcsset-wcsset-l-mbsset-mbsset-l.md) | [`memset`](../c-runtime-library/reference/memset-wmemset.md) |  |
| [`_lrotr`](../c-runtime-library/reference/lrotl-lrotr.md) | [`abs`](../c-runtime-library/reference/abs-labs-llabs-abs64.md) | [`strcat`](../c-runtime-library/reference/strcat-wcscat-mbscat.md) |  |

Programy korzystające z funkcji wewnętrznych są szybsze, ponieważ nie mają narzutu wywołań funkcji. Jednak mogą być większe ze względu na dodatkowy wygenerowany kod.

### <a name="x86-specific-example"></a>przykład dotyczący procesora x86

Elementy `_disable` i `_enable` wewnętrzne generują instrukcje trybu jądra w celu wyłączenia lub włączenia przerwań i mogą być przydatne w przypadku sterowników trybu jądra.

Skompiluj następujący kod z wiersza polecenia `cl -c -FAs sample.c` i sprawdź *`sample.asm`* , czy zapoznaj się z instrukcją x86 i STI:

```cpp
// pragma_directive_intrinsic.cpp
// processor: x86
#include <dos.h>   // definitions for _disable, _enable
#pragma intrinsic(_disable)
#pragma intrinsic(_enable)
void f1(void) {
   _disable();
   // do some work here that should not be interrupted
   _enable();
}
int main() {
}
```

### <a name="intrinsic-floating-point-functions"></a>Wewnętrzne funkcje zmiennoprzecinkowe

Te funkcje zmiennoprzecinkowe nie mają prawdziwych form wewnętrznych. Zamiast tego mają wersje, które przekazują argumenty bezpośrednio do mikroukładu zmiennoprzecinkowego, a nie wypychanie ich na stosie:

|  |  |  |  |
|--|--|--|--|
| [`acos`](../c-runtime-library/reference/acos-acosf-acosl.md) | [`cosh`](../c-runtime-library/reference/cosh-coshf-coshl.md) | [`pow`](../c-runtime-library/reference/pow-powf-powl.md) | [`tanh`](../c-runtime-library/reference/tanh-tanhf-tanhl.md) |
| [`asin`](../c-runtime-library/reference/asin-asinf-asinl.md) | [`fmod`](../c-runtime-library/reference/fmod-fmodf.md) | [`sinh`](../c-runtime-library/reference/sinh-sinhf-sinhl.md) |  |

Te funkcje zmiennoprzecinkowe mają prawdziwe formy wewnętrzne podczas określania [`/Oi`](../build/reference/oi-generate-intrinsic-functions.md) i [`/fp:fast`](../build/reference/fp-specify-floating-point-behavior.md) (lub dowolnej opcji, która zawiera **`/Oi`** : [`/Ox`](../build/reference/ox-full-optimization.md) , [`/O1`](../build/reference/o1-o2-minimize-size-maximize-speed.md) i [`/O2`](../build/reference/o1-o2-minimize-size-maximize-speed.md) ):

|  |  |  |  |
|--|--|--|--|
| [`atan`](../c-runtime-library/reference/atan-atanf-atanl-atan2-atan2f-atan2l.md) | [`exp`](../c-runtime-library/reference/exp-expf.md) | [`log10`](../c-runtime-library/reference/log-logf-log10-log10f.md) | [`sqrt`](../c-runtime-library/reference/sqrt-sqrtf-sqrtl.md) |
| [`atan2`](../c-runtime-library/reference/atan-atanf-atanl-atan2-atan2f-atan2l.md) | [`log`](../c-runtime-library/reference/log-logf-log10-log10f.md) | [`sin`](../c-runtime-library/reference/sin-sinf-sinl.md) | [`tan`](../c-runtime-library/reference/tan-tanf-tanl.md) |
| [`cos`](../c-runtime-library/reference/cos-cosf-cosl.md) |  |  |  |

Można użyć [`/fp:strict`](../build/reference/fp-specify-floating-point-behavior.md) lub [`/Za`](../build/reference/za-ze-disable-language-extensions.md) , aby zastąpić generowanie prawdziwych wewnętrznych opcji zmiennoprzecinkowych. W takim przypadku funkcje są generowane jako procedury bibliotek, które przechodzą argumenty bezpośrednio do mikroukładu zmiennoprzecinkowego zamiast wypychania ich do stosu programu.

Zapoznaj się z [`#pragma function`](../preprocessor/function-c-cpp.md) informacjami i przykładem na temat włączania i wyłączania elementów wewnętrznych dla bloku tekstu źródłowego.

## <a name="see-also"></a>Zobacz też

[Dyrektywy pragma i `__pragma` słowo kluczowe](../preprocessor/pragma-directives-and-the-pragma-keyword.md)\
[Funkcje wewnętrzne kompilatora](../intrinsics/compiler-intrinsics.md)
