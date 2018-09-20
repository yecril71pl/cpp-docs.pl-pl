---
title: -Ob (rozszerzenie funkcji wbudowanej) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 09/25/2017
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- VC.Project.VCCLWCECompilerTool.InlineFunctionExpansion
- VC.Project.VCCLCompilerTool.InlineFunctionExpansion
- /ob
dev_langs:
- C++
helpviewer_keywords:
- inline functions, function expansion compiler option [C++]
- -Ob1 compiler option [C++]
- -Ob0 compiler option [C++]
- /Ob0 compiler option [C++]
- /Ob1 compiler option [C++]
- any suitable compiler option [C++]
- Ob2 compiler option [C++]
- Ob1 compiler option [C++]
- /Ob2 compiler option [C++]
- Ob compiler option [C++]
- -Ob2 compiler option [C++]
- disable compiler option [C++]
- -Ob compiler option [C++]
- /Ob compiler option [C++]
- only __inline compiler option [C++]
- Ob0 compiler option [C++]
- inline expansion, compiler option
ms.assetid: f134e6df-e939-4980-a01d-47425dbc562a
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 43c67e4919680167bdde5e9f8ad9426229956fad
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/19/2018
ms.locfileid: "46401995"
---
# <a name="ob-inline-function-expansion"></a>/Ob (Rozszerzenie funkcji wbudowanej)

Kontroluje wbudowane rozwijanie funkcji.

## <a name="syntax"></a>Składnia

> /OB {0 | 1 | 2}

## <a name="arguments"></a>Argumenty

**0**<br/>
Wyłącza wbudowane rozszerzenia. Domyślnie rozszerzenie występuje według uznania kompilatora wszystkie funkcje, często nazywane *auto-inlining*.

**1**<br/>
Umożliwia rozwinięcie tylko funkcje oznaczone [wbudowane](../../cpp/inline-functions-cpp.md), `__inline`, lub `__forceinline`, lub w funkcji składowej C++, zdefiniowane w deklaracji klasy.

**2**<br/>
Wartość domyślna. Umożliwia rozwijanie funkcje oznaczone jako `inline`, `__inline`, lub `__forceinline`oraz wszystkie inne funkcje, które wybierze kompilator.

**/ Ob2** jest w działa, gdy [/O1, / O2 (Minimalizuj rozmiar, Maksymalizuj szybkość)](../../build/reference/o1-o2-minimize-size-maximize-speed.md) lub [OX (Włącz większość optymalizacji szybkości)](../../build/reference/ox-full-optimization.md) jest używany.

Ta opcja wymaga, aby włączyć optymalizacje przy użyciu **/O1**, **/O2**, **ox**, lub **/Og**.

## <a name="remarks"></a>Uwagi

Kompilator traktuje opcje rozszerzenia wbudowane i słów kluczowych jako sugestie. Nie ma żadnej gwarancji, że dowolnej funkcji będą rozwinięte wbudowanego. Można wyłączyć rozszerzenia w tekście, ale nie może wymusić na kompilatorze wbudowane określonej funkcji, nawet w przypadku używania `__forceinline` — słowo kluczowe.

Możesz użyć `#pragma` [auto_inline](../../preprocessor/auto-inline.md) dyrektywy, które mają zostać wykluczone funkcje pod uwagę podczas tworzenia dla wbudowane rozwijanie. Zobacz też `#pragma` [wewnętrzne](../../preprocessor/intrinsic.md) dyrektywy.

> [!NOTE]
> Informacje zebrane w trakcie przebiegów testowych profilowania zastępuje optymalizacje, które normalnie w efekcie w przypadku określenia **/Ob**, **/Os**, lub **/Ot**. Aby uzyskać więcej informacji, zobacz [optymalizacje Profile-Guided](../../build/reference/profile-guided-optimizations.md).

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Aby ustawić tę opcję kompilatora w środowisku programowania Visual Studio

1. Otwórz projekt **stron właściwości** okno dialogowe. Aby uzyskać więcej informacji, zobacz [Praca z właściwościami projektu](../../ide/working-with-project-properties.md).

1. Rozwiń **właściwości konfiguracji**, **C/C++** i wybierz **optymalizacji**.

1. Modyfikowanie **rozwijania funkcji Inline** właściwości.

### <a name="to-set-this-compiler-option-programmatically"></a>Aby programowo ustawić tę opcję kompilatora

- Zobacz <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.InlineFunctionExpansion%2A>.

## <a name="see-also"></a>Zobacz też

[/O Opcje (Optymalizuj kod)](../../build/reference/o-options-optimize-code.md)<br/>
[Opcje kompilatora](../../build/reference/compiler-options.md)<br/>
[Ustawianie opcji kompilatora](../../build/reference/setting-compiler-options.md)