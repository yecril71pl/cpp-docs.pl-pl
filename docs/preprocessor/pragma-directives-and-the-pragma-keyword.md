---
title: Dyrektywy pragma i słowo kluczowe __pragma
ms.date: 08/29/2019
f1_keywords:
- '#pragma'
helpviewer_keywords:
- '#pragma directives, C/C++'
- __pragma keyword
- pragma directives, C/C++
- pragmas, C/C++
- preprocessor
- pragmas
- preprocessor, pragmas
- pragma directives (#pragma)
ms.assetid: 9867b438-ac64-4e10-973f-c3955209873f
ms.openlocfilehash: 2cf075e4ff8049593a1e77c5d2c1c259b224877b
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/03/2019
ms.locfileid: "70222300"
---
# <a name="pragma-directives-and-the-__pragma-keyword"></a>Dyrektywy pragma i słowo kluczowe __pragma

Dyrektywy pragma określają funkcje kompilatora specyficzne dla maszyny lub systemu operacyjnego. Słowo kluczowe **__pragma** , które jest specyficzne dla kompilatora Microsoft, umożliwia kod dyrektywy pragma w definicjach makr.

## <a name="syntax"></a>Składnia

> **#pragma** *token — ciąg*\
> **__pragma (** *token-String* **)**

## <a name="remarks"></a>Uwagi

Każda implementacja języka C i C++ obsługuje pewne funkcje, które są unikatowe dla jego komputera lub systemu operacyjnego. Niektóre programy, na przykład, muszą mieć precyzyjną kontrolę nad lokalizacją danych w pamięci lub kontrolować sposób, w jaki niektóre funkcje odbierają parametry. Dyrektywy **#pragma** oferują sposób, w jaki każdy kompilator oferuje funkcje specyficzne dla maszyn i systemu operacyjnego, jednocześnie zachowując ogólną zgodność z językami C i C++ .

Dyrektywy pragma są specyficzne dla maszyny lub systemu operacyjnego według definicji i są zwykle różne dla każdego kompilatora. Dyrektywy pragma mogą być używane w dyrektywach warunkowych, aby zapewnić nową funkcję preprocesora lub dostarczyć do kompilatora informacje zdefiniowane przez implementację.

*Token-String* to seria znaków, które dają konkretną instrukcję i argumenty kompilatora, jeśli istnieją. Numer ( **#** ) musi być pierwszym znakiem niebiałym w wierszu zawierającym pragmę. Znaki odstępu mogą oddzielić znak numeru i słowo "pragma". Poniżej **#pragma**Napisz dowolny tekst, który tłumaczy może analizować jako wstępnie przetworzony tokeny. Argument **#pragma** podlega rozwinięciu makra.

Kompilator generuje ostrzeżenie, gdy znajdzie pragma, że nie rozpoznaje i kontynuuje Kompilowanie.

Microsoft C i C++ kompilatory rozpoznają następujące dyrektywy pragma:

||||
|-|-|-|
|[alloc_text](../preprocessor/alloc-text.md)|[auto_inline](../preprocessor/auto-inline.md)|[bss_seg](../preprocessor/bss-seg.md)|
|[check_stack](../preprocessor/check-stack.md)|[code_seg](../preprocessor/code-seg.md)|[komentować](../preprocessor/comment-c-cpp.md)|
|[składnik](../preprocessor/component.md)|[zgodne](../preprocessor/conform.md) <sup>1</sup>|[const_seg](../preprocessor/const-seg.md)|
|[data_seg](../preprocessor/data-seg.md)|[deprecated](../preprocessor/deprecated-c-cpp.md)|[detect_mismatch](../preprocessor/detect-mismatch.md)|
|[fenv_access](../preprocessor/fenv-access.md)|[float_control](../preprocessor/float-control.md)|[fp_contract](../preprocessor/fp-contract.md)|
|[funkcyjn](../preprocessor/function-c-cpp.md)|[hdrstop](../preprocessor/hdrstop.md)|[include_alias](../preprocessor/include-alias.md)|
|[init_seg](../preprocessor/init-seg.md) <sup>1</sup>|[inline_depth](../preprocessor/inline-depth.md)|[inline_recursion](../preprocessor/inline-recursion.md)|
|[intrinsic](../preprocessor/intrinsic.md)|[Pętla](../preprocessor/loop.md) <sup>1</sup>|[make_public](../preprocessor/make-public.md)|
|[zarządzanych](../preprocessor/managed-unmanaged.md)|[komunikat](../preprocessor/message.md)|[omp](../preprocessor/omp.md)|
|[once](../preprocessor/once.md)|[optymalizuj](../preprocessor/optimize.md)|[pakiet](../preprocessor/pack.md)|
|[pointers_to_members](../preprocessor/pointers-to-members.md) <sup>1</sup>|[pop_macro](../preprocessor/pop-macro.md)|[push_macro](../preprocessor/push-macro.md)|
|[region, endregion](../preprocessor/region-endregion.md)|[runtime_checks](../preprocessor/runtime-checks.md)|[sekcja](../preprocessor/section.md)|
|[setlocale](../preprocessor/setlocale.md)|[strict_gs_check](../preprocessor/strict-gs-check.md)|[niepodlegającą](../preprocessor/managed-unmanaged.md)|
|[vtordisp](../preprocessor/vtordisp.md) <sup>1</sup>|[ostrzeżenie](../preprocessor/warning.md)||

<sup>1</sup> obsługiwane tylko przez C++ kompilator.

## <a name="pragmas-and-compiler-options"></a>Dyrektywy pragma i opcje kompilatora

Niektóre dyrektywy pragma zapewniają te same funkcje co opcje kompilatora. W przypadku napotkania dyrektywy pragma w kodzie źródłowym zastępuje ona zachowanie określone przez opcję kompilatora. Na przykład jeśli określono [/ZP8](../build/reference/zp-struct-member-alignment.md), można zastąpić to ustawienie kompilatora dla określonych sekcji kodu z [pakietem](../preprocessor/pack.md):

```cmd
cl /Zp8 some_file.cpp
```

```cpp
// some_file.cpp - packing is 8
// ...
#pragma pack(push, 1) - packing is now 1
// ...
#pragma pack(pop) - packing is 8 again
// ...
```

## <a name="the-__pragma-keyword"></a>Słowo kluczowe __pragma ()

**Microsoft specific**

Kompilator obsługuje także słowo kluczowe **__pragma** , które ma takie same funkcje jak dyrektywa **#pragma** . Różnica polega na tym, że słowo kluczowe **__pragma** jest możliwe do użycia w definicji makra. Dyrektywa **#pragma** nie jest użyteczna w definicji makra, ponieważ kompilator interpretuje znak znaku cyfry ("#") w dyrektywie jako [operator tworzenia ciągu (#)](../preprocessor/stringizing-operator-hash.md).

Poniższy przykład kodu demonstruje, jak słowo kluczowe **__pragma** może być używane w makrze. Ten kod jest pochodzący z nagłówka MFCDUAL. h w próbce ACDUAL w "Przykłady obsługi kompilatora COM":

```cpp
#define CATCH_ALL_DUAL \
CATCH(COleException, e) \
{ \
_hr = e->m_sc; \
} \
AND_CATCH_ALL(e) \
{ \
__pragma(warning(push)) \
__pragma(warning(disable:6246)) /*disable _ctlState prefast warning*/ \
AFX_MANAGE_STATE(pThis->m_pModuleState); \
__pragma(warning(pop)) \
_hr = DualHandleException(_riidSource, e); \
} \
END_CATCH_ALL \
return _hr; \
```

**Zakończenie określonych przez firmę Microsoft**

## <a name="see-also"></a>Zobacz także

[Dokumentacja językaC++ C/preprocesora](../preprocessor/c-cpp-preprocessor-reference.md)\
[Dyrektywy pragma języka C](../c-language/c-pragmas.md)\
[Słowa kluczowe](../cpp/keywords-cpp.md)
