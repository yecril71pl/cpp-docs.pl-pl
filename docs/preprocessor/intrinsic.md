---
title: intrinsic, pragma
ms.date: 08/29/2019
f1_keywords:
- intrinsic_CPP
- vc-pragma.intrinsic
helpviewer_keywords:
- intrinsic pragma
- pragmas, intrinsic
ms.assetid: 25c86ac7-ef40-47b7-a2c0-fada9c5dc3c5
ms.openlocfilehash: bb4403abf5e278ed3727af660579e22ab69592c7
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/03/2019
ms.locfileid: "70220945"
---
# <a name="intrinsic-pragma"></a>intrinsic, pragma

Określa, że wywołania funkcji określonych na liście argumentów pragma są wewnętrzne.

## <a name="syntax"></a>Składnia

> **#pragma wewnętrznie (** *function1* [ **,** _function2_ ...] **)**

## <a name="remarks"></a>Uwagi

**Wewnętrzna** pragma informuje kompilator, że funkcja ma znane zachowanie. Kompilator może wywołać funkcję i nie zamieniać wywołania funkcji z instrukcjami wbudowanymi, jeśli spowoduje to lepszą wydajność.

Poniżej wymieniono funkcje biblioteki z formularzami wewnętrznymi. Po napotkaniu **wewnętrznej** dyrektywy pragma obowiązuje ona w pierwszej definicji funkcji zawierającej określoną funkcję wewnętrzną. Efekt jest kontynuowany na końcu pliku źródłowego lub do wyglądu `function` dyrektywy pragma określającej tę samą funkcję wewnętrzną. **Wewnętrznej** dyrektywy pragma można używać tylko poza definicją funkcji, na poziomie globalnym.

Poniższe funkcje mają formy wewnętrzne, a wewnętrzne formy są używane po określeniu [/Oi](../build/reference/oi-generate-intrinsic-functions.md):

|||||
|-|-|-|-|
|[_disable](../intrinsics/disable.md)|[_outp](../c-runtime-library/outp-outpw-outpd.md)|[fabs —](../c-runtime-library/reference/fabs-fabsf-fabsl.md)|[strcmp](../c-runtime-library/reference/strcmp-wcscmp-mbscmp.md)|
|[_enable](../intrinsics/enable.md)|[_outpw](../c-runtime-library/outp-outpw-outpd.md)|[Labs](../c-runtime-library/reference/abs-labs-llabs-abs64.md)|[strcpy](../c-runtime-library/reference/strcpy-wcscpy-mbscpy.md)|
|[_inp](../c-runtime-library/inp-inpw-inpd.md)|[_rotl](../c-runtime-library/reference/rotl-rotl64-rotr-rotr64.md)|[memcmp](../c-runtime-library/reference/memcmp-wmemcmp.md)|[strlen](../c-runtime-library/reference/strlen-wcslen-mbslen-mbslen-l-mbstrlen-mbstrlen-l.md)|
|[_inpw](../c-runtime-library/inp-inpw-inpd.md)|[_rotr](../c-runtime-library/reference/rotl-rotl64-rotr-rotr64.md)|[memcpy](../c-runtime-library/reference/memcpy-wmemcpy.md)||
|[_lrotl](../c-runtime-library/reference/lrotl-lrotr.md)|[_strset](../c-runtime-library/reference/strset-strset-l-wcsset-wcsset-l-mbsset-mbsset-l.md)|[memset](../c-runtime-library/reference/memset-wmemset.md)||
|[_lrotr](../c-runtime-library/reference/lrotl-lrotr.md)|[ABS](../c-runtime-library/reference/abs-labs-llabs-abs64.md)|[strcat](../c-runtime-library/reference/strcat-wcscat-mbscat.md)||

Programy korzystające z funkcji wewnętrznych są szybsze, ponieważ nie mają narzutu wywołań funkcji, ale mogą być większe ze względu na dodatkowy wygenerowany kod.

**x86 Specific**

Elementy `_disable` i`_enable` wewnętrzne generują instrukcje trybu jądra w celu wyłączenia lub włączenia przerwań i mogą być przydatne w przypadku sterowników trybu jądra.

### <a name="example"></a>Przykład

Skompiluj następujący kod z wiersza polecenia z `cl -c -FAs sample.c` i poszukaj przykład. ASM, aby zobaczyć, że zapoznają się z instrukcją procesora x86 i STI:

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

**Zakończenie specyficzne dla architektury x86**

Wymienione poniżej funkcje zmiennoprzecinkowe nie mają prawdziwych form wewnętrznych. Zamiast tego mają wersje, które przekazują argumenty bezpośrednio do mikroukładu zmiennoprzecinkowego, a nie wypychanie ich do stosu programu:

|||||
|-|-|-|-|
|[Acos](../c-runtime-library/reference/acos-acosf-acosl.md)|[cosh](../c-runtime-library/reference/cosh-coshf-coshl.md)|[pow](../c-runtime-library/reference/pow-powf-powl.md)|[TANH —](../c-runtime-library/reference/tanh-tanhf-tanhl.md)|
|[Asin](../c-runtime-library/reference/asin-asinf-asinl.md)|[FMOD —](../c-runtime-library/reference/fmod-fmodf.md)|[SINH](../c-runtime-library/reference/sinh-sinhf-sinhl.md)||

Funkcje zmiennoprzecinkowe wymienione poniżej mają prawdziwe elementy wewnętrzne w przypadku określenia [/Oi](../build/reference/oi-generate-intrinsic-functions.md), [/og](../build/reference/og-global-optimizations.md)i [/FP: Fast](../build/reference/fp-specify-floating-point-behavior.md) (lub dowolnej opcji, która obejmuje/og: [/OX](../build/reference/ox-full-optimization.md), [/O1](../build/reference/o1-o2-minimize-size-maximize-speed.md)i [/O2](../build/reference/o1-o2-minimize-size-maximize-speed.md)):

|||||
|-|-|-|-|
|[atan](../c-runtime-library/reference/atan-atanf-atanl-atan2-atan2f-atan2l.md)|[EXP](../c-runtime-library/reference/exp-expf.md)|[log10](../c-runtime-library/reference/log-logf-log10-log10f.md)|[sqrt](../c-runtime-library/reference/sqrt-sqrtf-sqrtl.md)|
|[atan2](../c-runtime-library/reference/atan-atanf-atanl-atan2-atan2f-atan2l.md)|[log](../c-runtime-library/reference/log-logf-log10-log10f.md)|[sinus](../c-runtime-library/reference/sin-sinf-sinl.md)|[Tan](../c-runtime-library/reference/tan-tanf-tanl.md)|
|[cos](../c-runtime-library/reference/cos-cosf-cosl.md)||||

Można użyć [/FP: Strict](../build/reference/fp-specify-floating-point-behavior.md) lub [/za](../build/reference/za-ze-disable-language-extensions.md) , aby zastąpić generowanie prawdziwych wewnętrznych opcji zmiennoprzecinkowych. W takim przypadku funkcje są generowane jako procedury bibliotek, które przechodzą argumenty bezpośrednio do mikroukładu zmiennoprzecinkowego zamiast wypychania ich do stosu programu.

Zobacz [#pragma funkcji](../preprocessor/function-c-cpp.md) , aby uzyskać informacje i przykład włączania/wyłączania elementów wewnętrznych dla bloku tekstu źródłowego.

## <a name="see-also"></a>Zobacz także

[Dyrektywy pragma i słowo kluczowe __pragma](../preprocessor/pragma-directives-and-the-pragma-keyword.md)\
[Funkcje wewnętrzne kompilatora](../intrinsics/compiler-intrinsics.md)
