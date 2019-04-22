---
title: Dyrektywy pragma i słowo kluczowe __Pragma
ms.date: 11/04/2016
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
ms.openlocfilehash: b6c2ff579c6fafa78cbfd0a2879a71fca2bfaa01
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59027444"
---
# <a name="pragma-directives-and-the-pragma-keyword"></a>Dyrektywy pragma i słowo kluczowe __Pragma

Dyrektywy pragma określają funkcje kompilatora lub operacyjny specyficzny dla komputera. **__Pragma** słowo kluczowe, które są specyficzne dla kompilatora Microsoft, umożliwia kodowanie dyrektyw pragma kodu w ramach definicji makra.

## <a name="syntax"></a>Składnia

```
#pragma token-string
__pragma(token-string)
```

## <a name="remarks"></a>Uwagi

Każda implementacja C i C++ obsługuje niektóre funkcje unikatowe dla jego komputera hosta lub systemu operacyjnego. Na przykład niektóre programy muszą wykonywać precyzyjną kontrolę nad obszarami pamięci, w których umieszczono dane lub kontrolować sposób pewność, że funkcje uzyskiwania parametrów. **#Pragma** dyrektywy oferują sposób, by każdy kompilator oferował funkcje dotyczące komputera i systemu operacyjnego przy zachowaniu ogólnej kompatybilności z językami C i C++ dla.

Dyrektywy pragma są określonej maszyny lub systemu operacyjnego, które zgodnie z definicją i są zazwyczaj inne dla każdego kompilatora. Dyrektywy pragma może służyć w instrukcjach warunkowych, aby dostarczyć nowe funkcje preprocesora lub informacje zdefiniowane w implementacji do kompilatora.

`token-string` Jest ciąg znaków, który zapewnia konkretną instrukcję kompilatora i argumenty, jeśli istnieje. Znak numeru (**#**) musi być pierwszym znakiem bez odstępu w wierszu, która zawiera dyrektywę; białe znaki można rozdzielić znakiem liczby i słowo "dyrektywa". Następujące **#pragma**, wpisz dowolny tekst, który translator można analizować jako przetworzone wstępnie tokeny. Argument **#pragma** podlega rozwinięciu makra.

Jeśli kompilator znajdzie pragmę, której nie rozpoznaje, generuje ostrzeżenie i kontynuuje kompilację.

Kompilatory Microsoft C i C++ rozpoznają następujące pragmy:

||||
|-|-|-|
|[alloc_text](../preprocessor/alloc-text.md)|[auto_inline](../preprocessor/auto-inline.md)|[bss_seg](../preprocessor/bss-seg.md)|
|[check_stack](../preprocessor/check-stack.md)|[code_seg](../preprocessor/code-seg.md)|[Komentarz](../preprocessor/comment-c-cpp.md)|
|[składnik](../preprocessor/component.md)|[jest zgodna z](../preprocessor/conform.md) <sup>1</sup>|[const_seg](../preprocessor/const-seg.md)|
|[data_seg](../preprocessor/data-seg.md)|[deprecated](../preprocessor/deprecated-c-cpp.md)|[detect_mismatch](../preprocessor/detect-mismatch.md)|
|[fenv_access](../preprocessor/fenv-access.md)|[float_control](../preprocessor/float-control.md)|[fp_contract](../preprocessor/fp-contract.md)|
|[— Funkcja](../preprocessor/function-c-cpp.md)|[hdrstop](../preprocessor/hdrstop.md)|[include_alias](../preprocessor/include-alias.md)|
|[init_seg](../preprocessor/init-seg.md) <sup>1</sup>|[inline_depth](../preprocessor/inline-depth.md)|[inline_recursion](../preprocessor/inline-recursion.md)|
|[intrinsic](../preprocessor/intrinsic.md)|[pętla](../preprocessor/loop.md) <sup>1</sup>|[make_public](../preprocessor/make-public.md)|
|[Zarządzane](../preprocessor/managed-unmanaged.md)|[komunikat](../preprocessor/message.md)||
|[omp](../preprocessor/omp.md)|[once](../preprocessor/once.md)||
|[optymalizuj](../preprocessor/optimize.md)|[pakiet](../preprocessor/pack.md)|[pointers_to_members](../preprocessor/pointers-to-members.md) <sup>1</sup>|
|[pop_macro](../preprocessor/pop-macro.md)|[push_macro](../preprocessor/push-macro.md)|[region, endregion](../preprocessor/region-endregion.md)|
|[runtime_checks](../preprocessor/runtime-checks.md)|[sekcja](../preprocessor/section.md)|[setlocale](../preprocessor/setlocale.md)|
|[strict_gs_check](../preprocessor/strict-gs-check.md)|[niezarządzane](../preprocessor/managed-unmanaged.md)|[vtordisp](../preprocessor/vtordisp.md) <sup>1</sup>|
|[ostrzeżenie](../preprocessor/warning.md)|||

<sup>1</sup> obsługiwana tylko przez kompilator języka C++.

## <a name="pragmas-and-compiler-options"></a>Opcje kompilatora i dyrektyw pragma

Niektóre informacje pragmatyczne zapewniają taką samą funkcjonalność jak opcje kompilatora. Gdy pragmę w kodzie źródłowym, zastępuje ona zachowanie określone przez opcję kompilatora. Na przykład, jeśli określono [/zp8](../build/reference/zp-struct-member-alignment.md), można zastąpić to ustawienie kompilatora dla poszczególnych sekcji kodu za pomocą [pakiet](../preprocessor/pack.md):

```
cl /Zp8 ...

<file> - packing is 8
// ...
#pragma pack(push, 1) - packing is now 1
// ...
#pragma pack(pop) - packing is 8
</file>
```

## <a name="the-pragma-keyword"></a>The __pragma() Keyword

**Microsoft specific**

Kompilator obsługuje również **__pragma** słowo kluczowe, które ma taką samą funkcjonalność jako **#pragma** dyrektywy, ale mogą być używane jako wbudowane w definicję makra. **#Pragma** dyrektywy nie można używać w definicji makra, ponieważ kompilator zinterpretuje znak numeru (#) w dyrektywie jako [operator tworzenia ciągu (#)](../preprocessor/stringizing-operator-hash.md).

Poniższy przykład kodu demonstruje sposób, w jaki **__pragma** — słowo kluczowe może być używana w makrze. Ten kod jest wyszczególniony z nagłówka mfcdual.h w przykładzie acdual w "Przykładach obsługi kompilatora COM":

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

**Koniec specyficzne dla firmy Microsoft**

## <a name="see-also"></a>Zobacz także

[Dokumentacja preprocesora języka C/C++](../preprocessor/c-cpp-preprocessor-reference.md)<br/>
[Pragma, dyrektywy języka C](../c-language/c-pragmas.md)<br/>
[Słowa kluczowe](../cpp/keywords-cpp.md)