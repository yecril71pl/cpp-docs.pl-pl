---
title: "wewnętrzne | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- intrinsic_CPP
- vc-pragma.intrinsic
dev_langs: C++
helpviewer_keywords:
- intrinsic pragma
- pragmas, intrinsic
ms.assetid: 25c86ac7-ef40-47b7-a2c0-fada9c5dc3c5
caps.latest.revision: "7"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 1531c0ceb34711153fb2577255d7d6fe463ee021
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="intrinsic"></a>— funkcja
Określa, że wywołania funkcji znajduje się na liście argumentów pragma wewnętrznej.  
  
## <a name="syntax"></a>Składnia  
  
```  
  
#pragma intrinsic( function1 [, function2, ...] )  
```  
  
## <a name="remarks"></a>Uwagi  
 **Wewnętrzne** pragma informuje kompilator, że funkcja znane zachowanie.  Kompilator może wywołać funkcję i zastępuje wywołanie funkcji z instrukcjami w tekście, jeśli będzie zapewnia lepszą wydajność.  
  
 Funkcje bibliotek z formularzami wewnętrzne są wymienione poniżej. Raz **wewnętrzne** pragma jest widoczne, będzie wprowadzona w pierwszym definicji funkcji zawierających określony funkcji wewnętrznej. Efekt nadal na końcu pliku źródłowego lub wygląd **funkcja** pragma określenie tej samej funkcji wewnętrznej. **Wewnętrzne** pragmy można użyć tylko poza definicją funkcji — na poziomie globalnym.  
  
 Następujące funkcje zostały wewnętrzne formularzy i wewnętrzne formularze są używane podczas określania [/Oi](../build/reference/oi-generate-intrinsic-functions.md):  
  
|||||  
|-|-|-|-|  
|[_disable](../intrinsics/disable.md)|[_outp —](../c-runtime-library/outp-outpw-outpd.md)|[fabs —](../c-runtime-library/reference/fabs-fabsf-fabsl.md)|[strcmp —](../c-runtime-library/reference/strcmp-wcscmp-mbscmp.md)|  
|[_włącz](../intrinsics/enable.md)|[_outpw —](../c-runtime-library/outp-outpw-outpd.md)|[Labs](../c-runtime-library/reference/abs-labs-llabs-abs64.md)|[strcpy](../c-runtime-library/reference/strcpy-wcscpy-mbscpy.md)|  
|[_inp —](../c-runtime-library/inp-inpw-inpd.md)|[_rotl —](../c-runtime-library/reference/rotl-rotl64-rotr-rotr64.md)|[funkcji memcmp](../c-runtime-library/reference/memcmp-wmemcmp.md)|[strlen —](../c-runtime-library/reference/strlen-wcslen-mbslen-mbslen-l-mbstrlen-mbstrlen-l.md)|  
|[_inpw —](../c-runtime-library/inp-inpw-inpd.md)|[_rotr —](../c-runtime-library/reference/rotl-rotl64-rotr-rotr64.md)|[memcpy](../c-runtime-library/reference/memcpy-wmemcpy.md)||  
|[_lrotl —](../c-runtime-library/reference/lrotl-lrotr.md)|[_strset —](../c-runtime-library/reference/strset-strset-l-wcsset-wcsset-l-mbsset-mbsset-l.md)|[funkcji memset](../c-runtime-library/reference/memset-wmemset.md)||  
|[_lrotr —](../c-runtime-library/reference/lrotl-lrotr.md)|[ABS](../c-runtime-library/reference/abs-labs-llabs-abs64.md)|[strcat —](../c-runtime-library/reference/strcat-wcscat-mbscat.md)||  
  
 Programy używające funkcji wewnętrznej są szybsze, ponieważ bez nakładów związanych z wywołania funkcji, ale może być większy z powodu dodatkowy kod wygenerowany.  
  
 **x86 określonych**  
  
 Funkcje wewnętrzne _disable i _włącz Generowanie instrukcji trybu jądra, aby włączyć/wyłączyć przerwań i może okazać się przydatne przy sterowniki trybu jądra.  
  
## <a name="example"></a>Przykład  
 Skompiluj następujący kod w wierszu polecenia z "cl - c-FAs sample.c" i przyjrzyj się sample.asm, aby zobaczyć, czy sprawią x86 instrukcje interfejsu wiersza polecenia i STI:  
  
```  
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
  
 **Konkretnego celu x86**  
  
 Funkcje liczb zmiennoprzecinkowych wymienionych poniżej nie ma wartość true, formularze wewnętrzne. Zamiast tego mają wersje, które przekazywać argumenty bezpośrednio do liczb zmiennoprzecinkowych mikroukładu niż wypychanie ich na stosie program:  
  
|||||  
|-|-|-|-|  
|[ACOS](../c-runtime-library/reference/acos-acosf-acosl.md)|[COSH](../c-runtime-library/reference/cos-cosf-cosl-cosh-coshf-coshl.md)|[Pow](../c-runtime-library/reference/pow-powf-powl.md)|[TANH](../c-runtime-library/reference/tan-tanf-tanl-tanh-tanhf-tanhl.md)|  
|[ASIN](../c-runtime-library/reference/asin-asinf-asinl.md)|[fmod —](../c-runtime-library/reference/fmod-fmodf.md)|[SINH](../c-runtime-library/reference/sin-sinf-sinl-sinh-sinhf-sinhl.md)||  
  
 Funkcje liczb zmiennoprzecinkowych wymienionych poniżej ma wartość true, formularze wewnętrzne po określeniu [/Oi](../build/reference/oi-generate-intrinsic-functions.md), [/Og](../build/reference/og-global-optimizations.md), i [Fast](../build/reference/fp-specify-floating-point-behavior.md) (lub każda opcja, która obejmuje /Og: [/ Ox](../build/reference/ox-full-optimization.md), [/O1](../build/reference/o1-o2-minimize-size-maximize-speed.md)i/O2):  
  
|||||  
|-|-|-|-|  
|[ATAN](../c-runtime-library/reference/atan-atanf-atanl-atan2-atan2f-atan2l.md)|[EXP](../c-runtime-library/reference/exp-expf.md)|[LOG10](../c-runtime-library/reference/log-logf-log10-log10f.md)|[SQRT](../c-runtime-library/reference/sqrt-sqrtf-sqrtl.md)|  
|[ATAN2](../c-runtime-library/reference/atan-atanf-atanl-atan2-atan2f-atan2l.md)|[Dziennik](../c-runtime-library/reference/log-logf-log10-log10f.md)|[SIN](../c-runtime-library/reference/sin-sinf-sinl-sinh-sinhf-sinhl.md)|[tan](../c-runtime-library/reference/tan-tanf-tanl-tanh-tanhf-tanhl.md)|  
|[COS](../c-runtime-library/reference/cos-cosf-cosl-cosh-coshf-coshl.md)||||  
  
 Można użyć [/FP: strict](../build/reference/fp-specify-floating-point-behavior.md) lub [/Za](../build/reference/za-ze-disable-language-extensions.md) do przesłonięcia generowania true wewnętrzne opcje zmiennoprzecinkowych. W takim przypadku funkcje są generowane jako procedury biblioteki, które przekazywać argumenty bezpośrednio do liczb zmiennoprzecinkowych mikroukładu zamiast wypychanie ich na stosie programu.  
  
 Zobacz [funkcja pragma #](../preprocessor/function-c-cpp.md) informacji oraz przykład włączyć lub wyłączyć funkcje wewnętrzne w bloku tekstu źródłowego.  
  
## <a name="see-also"></a>Zobacz też  
 [Dyrektywy pragma i słowo kluczowe __Pragma](../preprocessor/pragma-directives-and-the-pragma-keyword.md)   
 [Funkcje wewnętrzne kompilatora](../intrinsics/compiler-intrinsics.md)