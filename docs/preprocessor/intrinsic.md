---
title: wewnętrzne | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 04/11/2018
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- intrinsic_CPP
- vc-pragma.intrinsic
dev_langs:
- C++
helpviewer_keywords:
- intrinsic pragma
- pragmas, intrinsic
ms.assetid: 25c86ac7-ef40-47b7-a2c0-fada9c5dc3c5
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 496971736e1f303d61b83e15b2ba1c03083f8d53
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/19/2018
ms.locfileid: "46422795"
---
# <a name="intrinsic"></a>— funkcja

Określa, czy wewnętrznych wywołań funkcji określona w pragmie listy argumentów.

## <a name="syntax"></a>Składnia

```cpp
#pragma intrinsic( function1 [, function2, ...] )
```

## <a name="remarks"></a>Uwagi

**Wewnętrzne** pragma informuje kompilator, że funkcja znane zachowanie.  Kompilator może wywołać funkcję i zastępuje wywołania funkcji z instrukcjami w tekście, jeśli spowoduje lepszą wydajność.

Funkcje bibliotek z formularzami wewnętrzne są wymienione poniżej. Gdy **wewnętrzne** pragmy jest widoczny, wprowadzone w pierwszej definicji funkcji zawierający określoną funkcję wewnętrzne. Efekt kontynuuje do końca pliku źródłowego lub wyglądu `function` pragma, określając tę samą funkcję wewnętrzne. **Wewnętrzne** dyrektywa może zostać użyta tylko poza definicją funkcji — na poziomie globalnym.

Następujące funkcje mają wewnętrzne forms i formularzy wewnętrzne są używane podczas określania [/Oi](../build/reference/oi-generate-intrinsic-functions.md):

|||||
|-|-|-|-|
|[_disable](../intrinsics/disable.md)|[_outp —](../c-runtime-library/outp-outpw-outpd.md)|[fabs —](../c-runtime-library/reference/fabs-fabsf-fabsl.md)|[strcmp](../c-runtime-library/reference/strcmp-wcscmp-mbscmp.md)|
|[_enable](../intrinsics/enable.md)|[_outpw](../c-runtime-library/outp-outpw-outpd.md)|[Warsztaty](../c-runtime-library/reference/abs-labs-llabs-abs64.md)|[strcpy](../c-runtime-library/reference/strcpy-wcscpy-mbscpy.md)|
|[_inp —](../c-runtime-library/inp-inpw-inpd.md)|[_rotl](../c-runtime-library/reference/rotl-rotl64-rotr-rotr64.md)|[memcmp](../c-runtime-library/reference/memcmp-wmemcmp.md)|[strlen](../c-runtime-library/reference/strlen-wcslen-mbslen-mbslen-l-mbstrlen-mbstrlen-l.md)|
|[_inpw](../c-runtime-library/inp-inpw-inpd.md)|[_rotr —](../c-runtime-library/reference/rotl-rotl64-rotr-rotr64.md)|[memcpy](../c-runtime-library/reference/memcpy-wmemcpy.md)||
|[_lrotl](../c-runtime-library/reference/lrotl-lrotr.md)|[_strset](../c-runtime-library/reference/strset-strset-l-wcsset-wcsset-l-mbsset-mbsset-l.md)|[memset](../c-runtime-library/reference/memset-wmemset.md)||
|[_lrotr —](../c-runtime-library/reference/lrotl-lrotr.md)|[ABS](../c-runtime-library/reference/abs-labs-llabs-abs64.md)|[strcat](../c-runtime-library/reference/strcat-wcscat-mbscat.md)||

Programy, które używają funkcje wewnętrzne są szybsze, ponieważ nie masz obciążenie związane z wywołania funkcji, ale może być większy ze względu na dodatkowe wygenerowany kod.

**x86 Specific**

`_disable` i `_enable` funkcje wewnętrzne Generowanie trybu jądra instrukcje Włącz/Wyłącz przerwań i może być przydatna w sterowników trybu jądra.

### <a name="example"></a>Przykład

Skompiluj następujący kod z wiersza polecenia za pomocą `cl -c -FAs sample.c` i przyjrzyj się sample.asm, aby zobaczyć, że zmieniania pomysłów w x86 instrukcje interfejsu wiersza polecenia i STI:

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

**Koniec x86 określonych**

Funkcje zmiennoprzecinkowe wymienione poniżej nie ma wartość true, formularze wewnętrzne. Zamiast tego mają wersje, które argumenty przekazywane bezpośrednio do zmiennoprzecinkowych mikroukładu niż wypychanie ich na stosie program:

|||||
|-|-|-|-|
|[ACOS](../c-runtime-library/reference/acos-acosf-acosl.md)|[COSH](../c-runtime-library/reference/cosh-coshf-coshl.md)|[Pow](../c-runtime-library/reference/pow-powf-powl.md)|[TANH](../c-runtime-library/reference/tanh-tanhf-tanhl.md)|
|[ASIN](../c-runtime-library/reference/asin-asinf-asinl.md)|[Fmod —](../c-runtime-library/reference/fmod-fmodf.md)|[SINH](../c-runtime-library/reference/sinh-sinhf-sinhl.md)||

 Funkcje liczb zmiennoprzecinkowych, wymienionych poniżej ma wartość true, formularze wewnętrzne po określeniu [/Oi](../build/reference/oi-generate-intrinsic-functions.md), [/Og](../build/reference/og-global-optimizations.md), i [Fast](../build/reference/fp-specify-floating-point-behavior.md) (lub dowolną opcję, która obejmuje /Og: [/ Ox](../build/reference/ox-full-optimization.md), [/O1](../build/reference/o1-o2-minimize-size-maximize-speed.md)and/O2):

|||||
|-|-|-|-|
|[atan](../c-runtime-library/reference/atan-atanf-atanl-atan2-atan2f-atan2l.md)|[EXP](../c-runtime-library/reference/exp-expf.md)|[log10](../c-runtime-library/reference/log-logf-log10-log10f.md)|[sqrt](../c-runtime-library/reference/sqrt-sqrtf-sqrtl.md)|
|[atan2](../c-runtime-library/reference/atan-atanf-atanl-atan2-atan2f-atan2l.md)|[log](../c-runtime-library/reference/log-logf-log10-log10f.md)|[SIN](../c-runtime-library/reference/sin-sinf-sinl.md)|[tan](../c-runtime-library/reference/tan-tanf-tanl.md)|
|[COS](../c-runtime-library/reference/cos-cosf-cosl.md)||||

Możesz użyć [/FP: strict](../build/reference/fp-specify-floating-point-behavior.md) lub [/Za](../build/reference/za-ze-disable-language-extensions.md) do zastąpienia generowania true wewnętrzne opcje zmiennoprzecinkowych. W takich przypadkach funkcje są generowane jako biblioteki procedur, które argumenty przekazywane bezpośrednio do zmiennoprzecinkowych mikroukładu zamiast wypychanie ich na stosie program.

Zobacz [funkcji #pragma](../preprocessor/function-c-cpp.md) informacji i obejrzeć przykład włączenia/wyłączenia funkcji wewnętrznych w bloku tekstu źródłowego.

## <a name="see-also"></a>Zobacz także

[Dyrektywy pragma i słowo kluczowe __Pragma](../preprocessor/pragma-directives-and-the-pragma-keyword.md)<br/>
[Funkcje wewnętrzne kompilatora](../intrinsics/compiler-intrinsics.md)  