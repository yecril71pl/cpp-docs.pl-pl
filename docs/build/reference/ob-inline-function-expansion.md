---
title: /Ob (Rozszerzenie funkcji wbudowanej)
ms.date: 09/25/2017
f1_keywords:
- VC.Project.VCCLWCECompilerTool.InlineFunctionExpansion
- VC.Project.VCCLCompilerTool.InlineFunctionExpansion
- /ob
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
ms.openlocfilehash: 6bf16e5725916e81e64d80c0a1f96bf502c8826c
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62320230"
---
# <a name="ob-inline-function-expansion"></a>/Ob (Rozszerzenie funkcji wbudowanej)

Kontroluje wbudowane rozwijanie funkcji.

## <a name="syntax"></a>Składnia

> /Ob{0|1|2}

## <a name="arguments"></a>Argumenty

**0**<br/>
Wyłącza wbudowane rozszerzenia. Domyślnie rozszerzenie występuje według uznania kompilatora wszystkie funkcje, często nazywane *auto-inlining*.

**1**<br/>
Umożliwia rozwinięcie tylko funkcje oznaczone [wbudowane](../../cpp/inline-functions-cpp.md), `__inline`, lub `__forceinline`, lub w funkcji składowej C++, zdefiniowane w deklaracji klasy.

**2**<br/>
Wartość domyślna. Umożliwia rozwijanie funkcje oznaczone jako `inline`, `__inline`, lub `__forceinline`oraz wszystkie inne funkcje, które wybierze kompilator.

**/ Ob2** jest w działa, gdy [/O1, / O2 (Minimalizuj rozmiar, Maksymalizuj szybkość)](o1-o2-minimize-size-maximize-speed.md) lub [OX (Włącz większość optymalizacji szybkości)](ox-full-optimization.md) jest używany.

Ta opcja wymaga, aby włączyć optymalizacje przy użyciu **/O1**, **/O2**, **ox**, lub **/Og**.

## <a name="remarks"></a>Uwagi

Kompilator traktuje opcje rozszerzenia wbudowane i słów kluczowych jako sugestie. Nie ma żadnej gwarancji, że dowolnej funkcji będą rozwinięte wbudowanego. Można wyłączyć rozszerzenia w tekście, ale nie może wymusić na kompilatorze wbudowane określonej funkcji, nawet w przypadku używania `__forceinline` — słowo kluczowe.

Możesz użyć `#pragma` [auto_inline](../../preprocessor/auto-inline.md) dyrektywy, które mają zostać wykluczone funkcje pod uwagę podczas tworzenia dla wbudowane rozwijanie. Zobacz też `#pragma` [wewnętrzne](../../preprocessor/intrinsic.md) dyrektywy.

> [!NOTE]
> Informacje zebrane w trakcie przebiegów testowych profilowania zastępuje optymalizacje, które normalnie w efekcie w przypadku określenia **/Ob**, **/Os**, lub **/Ot**. Aby uzyskać więcej informacji, zobacz [optymalizacje Profile-Guided](../profile-guided-optimizations.md).

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Aby ustawić tę opcję kompilatora w środowisku programowania Visual Studio

1. Otwórz projekt **stron właściwości** okno dialogowe. Aby uzyskać więcej informacji, zobacz [kompilatora i tworzenia właściwości ustaw C++ w programie Visual Studio](../working-with-project-properties.md).

1. Rozwiń **właściwości konfiguracji**, **C/C++** i wybierz **optymalizacji**.

1. Modyfikowanie **rozwijania funkcji Inline** właściwości.

### <a name="to-set-this-compiler-option-programmatically"></a>Aby programowo ustawić tę opcję kompilatora

- Zobacz <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.InlineFunctionExpansion%2A>.

## <a name="see-also"></a>Zobacz także

[/O Opcje (Optymalizuj kod)](o-options-optimize-code.md)<br/>
[Opcje kompilatora MSVC](compiler-options.md)<br/>
[Składnia wiersza polecenia kompilatora MSVC](compiler-command-line-syntax.md)
