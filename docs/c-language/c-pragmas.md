---
title: Pragma — dyrektywy języka C
ms.date: 07/26/2020
helpviewer_keywords:
- pragmas, C/C++
ms.assetid: 3d6d36b4-d565-4632-a4cd-e39aeaded5ad
ms.openlocfilehash: ce8efb54eacf40a9feb7b629c2a61a32b3a71b79
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/25/2020
ms.locfileid: "88845214"
---
# <a name="c-pragmas"></a>Pragma — dyrektywy języka C

**Specyficzne dla firmy Microsoft**

*Pragma* instruuje kompilator, aby wykonał określoną akcję w czasie kompilacji. Dyrektywy pragma różnią się od kompilatora do kompilatora. Na przykład można użyć `optimize` dyrektywy pragma do ustawienia optymalizacji do wykonania w programie. Pragma języka Microsoft C:

:::row:::
    :::column:::
        [`alloc_text`](../preprocessor/alloc-text.md)\
        [`auto_inline`](../preprocessor/auto-inline.md)\
        [`bss_seg`](../preprocessor/bss-seg.md)\
        [`check_stack`](../preprocessor/check-stack.md)\
        [`code_seg`](../preprocessor/code-seg.md)\
        [`comment`](../preprocessor/comment-c-cpp.md)\
        [`component`](../preprocessor/component.md)\
        [`const_seg`](../preprocessor/const-seg.md)\
        [`data_seg`](../preprocessor/data-seg.md)
    :::column-end:::
    :::column:::
        [`deprecated`](../preprocessor/deprecated-c-cpp.md)\
        [`detect_mismatch`](../preprocessor/detect-mismatch.md)\
        [`fenv_access`](../preprocessor/fenv-access.md)\
        [`float_control`](../preprocessor/float-control.md)\
        [`fp_contract`](../preprocessor/fp-contract.md)\
        [`function`](../preprocessor/function-c-cpp.md)\
        [`hdrstop`](../preprocessor/hdrstop.md)\
        [`include_alias`](../preprocessor/include-alias.md)\
        [`inline_depth`](../preprocessor/inline-depth.md)
    :::column-end:::
    :::column:::
        [`inline_recursion`](../preprocessor/inline-recursion.md)\
        [`intrinsic`](../preprocessor/intrinsic.md)\
        [`make_public`](../preprocessor/make-public.md)\
        [`managed`](../preprocessor/managed-unmanaged.md)\
        [`message`](../preprocessor/message.md)\
        [`omp`](../preprocessor/omp.md)\
        [`once`](../preprocessor/once.md)\
        [`optimize`](../preprocessor/optimize.md)\
        [`pack`](../preprocessor/pack.md)
    :::column-end:::
    :::column:::
        [`pop_macro`](../preprocessor/pop-macro.md)\
        [`push_macro`](../preprocessor/push-macro.md)\
        [`region`, `endregion`](../preprocessor/region-endregion.md)\
        [`runtime_checks`](../preprocessor/runtime-checks.md)\
        [`section`](../preprocessor/section.md)\
        [`setlocale`](../preprocessor/setlocale.md)\
        [`strict_gs_check`](../preprocessor/strict-gs-check.md)\
        [`unmanaged`](../preprocessor/managed-unmanaged.md)\
        [`warning`](../preprocessor/warning.md)
    :::column-end:::
:::row-end:::

Zobacz [dyrektywy pragma i `__Pragma` słowo kluczowe,](../preprocessor/pragma-directives-and-the-pragma-keyword.md) aby zapoznać się z opisem dyrektywy pragma kompilatora języka Microsoft C.

**ZAKOŃCZENIE określonych przez firmę Microsoft**

## <a name="see-also"></a>Zobacz też

[Pliki źródłowe i programy źródłowe](../c-language/source-files-and-source-programs.md)
