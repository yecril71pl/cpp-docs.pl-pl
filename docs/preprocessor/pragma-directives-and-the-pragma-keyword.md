---
title: "Dyrektywy pragma i słowo kluczowe __Pragma | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: '#pragma'
dev_langs: C++
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
caps.latest.revision: "20"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 845c2fab98d246ccee51aff721b1ceb011e3803c
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="pragma-directives-and-the-pragma-keyword"></a>Dyrektywy pragma i słowo kluczowe __Pragma
Pragma — dyrektywy Określ maszyny lub operacyjnego-funkcji specyficznych dla kompilatora. `__pragma` — Słowo kluczowe, która jest specyficzna dla kompilatora firmy Microsoft, umożliwia kod dyrektywy pragma w definicjach makr.  
  
## <a name="syntax"></a>Składnia  
  
```  
  
      #pragma token-string  
__pragma(token-string)  
```  
  
## <a name="remarks"></a>Uwagi  
 Każda implementacja C i C++ obsługuje niektóre funkcje, które są unikatowe dla systemu operacyjnego lub komputer hosta. Na przykład niektóre programy muszą wykonywać precyzyjną kontrolę nad obszary pamięci, którym jest umieszczany danych lub aby kontrolować sposób pewność, że parametry odbierania funkcji. `#pragma` Dyrektywy umożliwiają dla każdego kompilatora oferowanie funkcji specyficznych dla komputera i systemu operacyjnego przy zachowaniu ogólnej zgodności z języków C i C++.  
  
 Dyrektywy pragma są dotyczące komputera lub systemu operacyjnego, które zgodnie z definicją i są zwykle różne dla każdego kompilatora. W instrukcji warunkowej, można Pragm nowych funkcji preprocesora lub podaj informacje zdefiniowane w implementacji, aby kompilatora.  
  
 `token-string` Jest ciąg znaków zawierający instrukcję określonych kompilatora i argumentów, jeśli istnieje. Znak liczby (**#**) musi być pierwszym znakiem z systemem innym niż biały na wiersz zawierający pragma; -białe znaki można oddzielić znak liczby i słowem "pragma". Po `#pragma`, zapisać dowolny tekst, który translator można przeanalizować jako wstępnego przetwarzania tokenów. Argument `#pragma` podlega rozwinięciu makra.  
  
 Jeśli kompilator znajdzie pragma, która nie rozpoznaje, ostrzeżenie i kontynuuje kompilacji.  
  
 Kompilatory języka Microsoft C i C++ rozpoznaje następujących pragm:  
  
||||  
|-|-|-|  
|[alloc_text](../preprocessor/alloc-text.md)|[auto_inline](../preprocessor/auto-inline.md)|[bss_seg](../preprocessor/bss-seg.md)|  
|[check_stack](../preprocessor/check-stack.md)|[code_seg](../preprocessor/code-seg.md)|[komentarz](../preprocessor/comment-c-cpp.md)|  
|[składnik](../preprocessor/component.md)|[jest zgodna z](../preprocessor/conform.md) <sup>1</sup>|[const_seg](../preprocessor/const-seg.md)|  
|[data_seg](../preprocessor/data-seg.md)|[przestarzałe](../preprocessor/deprecated-c-cpp.md)|[detect_mismatch](../preprocessor/detect-mismatch.md)|  
|[fenv_access](../preprocessor/fenv-access.md)|[float_control](../preprocessor/float-control.md)|[fp_contract](../preprocessor/fp-contract.md)|  
|[Funkcja](../preprocessor/function-c-cpp.md)|[hdrstop](../preprocessor/hdrstop.md)|[include_alias](../preprocessor/include-alias.md)|  
|[init_seg](../preprocessor/init-seg.md) <sup>1</sup>|[inline_depth](../preprocessor/inline-depth.md)|[inline_recursion](../preprocessor/inline-recursion.md)|  
|[intrinsic](../preprocessor/intrinsic.md)|[pętla](../preprocessor/loop.md) <sup>1</sup>|[make_public](../preprocessor/make-public.md)|  
|[zarządzane](../preprocessor/managed-unmanaged.md)|[komunikat](../preprocessor/message.md)||  
|[omp](../preprocessor/omp.md)|[once](../preprocessor/once.md)||  
|[optymalizuj](../preprocessor/optimize.md)|[pakiet](../preprocessor/pack.md)|[pointers_to_members](../preprocessor/pointers-to-members.md) <sup>1</sup>|  
|[pop_macro](../preprocessor/pop-macro.md)|[push_macro](../preprocessor/push-macro.md)|[region, endregion](../preprocessor/region-endregion.md)|  
|[runtime_checks](../preprocessor/runtime-checks.md)|[sekcja](../preprocessor/section.md)|[setlocale](../preprocessor/setlocale.md)|  
|[strict_gs_check](../preprocessor/strict-gs-check.md)|[niezarządzane](../preprocessor/managed-unmanaged.md)|[vtordisp](../preprocessor/vtordisp.md) <sup>1</sup>|  
|[ostrzeżenie](../preprocessor/warning.md)|||  
  
 1. Obsługiwane tylko przez kompilator języka C++.  
  
## <a name="pragmas-and-compiler-options"></a>Dyrektywy pragma i opcje kompilatora  
 Niektóre dyrektywy pragma zawierają te same funkcje co opcje kompilatora. W przypadku pragma w kodzie źródłowym przesłania zachowanie określonego przez opcję kompilatora. Na przykład, jeśli określono [/Zp8](../build/reference/zp-struct-member-alignment.md), można zastąpić to ustawienie kompilatora określonych sekcji kodu z [pakietu](../preprocessor/pack.md):  
  
```  
cl /Zp8 ...  
  
<file> - packing is 8  
// ...  
#pragma pack(push, 1) - packing is now 1  
// ...  
#pragma pack(pop) - packing is 8  
</file>  
```  
  
## <a name="the-pragma-keyword"></a>__Pragma() — słowo kluczowe  
 **Określone firmy Microsoft**  
  
 Kompilator obsługuje również `__pragma` — słowo kluczowe, który ma te same funkcje jako `#pragma` dyrektywy, ale mogą być używane wbudowane w definicji makra. `#pragma` Nie można użyć dyrektywy w definicji makra, ponieważ kompilator interpretuje numer znak (#) w dyrektywie jako [operator tworzenia ciągów (#)](../preprocessor/stringizing-operator-hash.md).  
  
 Poniższy przykład kodu pokazuje sposób `__pragma` — słowo kluczowe może być używana w makrze. Ten kod jest fragmentem książki nagłówek mfcdual.h acdual — przykład w "Przykłady obsługi modelu COM kompilatora":  
  
```  
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
  
 **Microsoft zakończenia określonych**  
  
## <a name="see-also"></a>Zobacz też  
 [Odwołania preprocesora C/C++](../preprocessor/c-cpp-preprocessor-reference.md)   
 [Pragma C](../c-language/c-pragmas.md)   
 [Słowa kluczowe](../cpp/keywords-cpp.md)