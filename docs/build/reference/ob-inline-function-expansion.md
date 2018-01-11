---
title: -Ob (rozszerzenie funkcji wbudowanej) | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 09/25/2017
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- VC.Project.VCCLWCECompilerTool.InlineFunctionExpansion
- VC.Project.VCCLCompilerTool.InlineFunctionExpansion
- /ob
dev_langs: C++
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
caps.latest.revision: "13"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: b83d470eaf6a30698d8c2836620a0688daa35cc1
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="ob-inline-function-expansion"></a>/Ob (Rozszerzenie funkcji wbudowanej)

Określa rozszerzenie funkcji wbudowanej funkcji.

## <a name="syntax"></a>Składnia

> /OB {0 | 1 | 2}

## <a name="arguments"></a>Argumenty

**0**  
Wyłącza wbudowane rozszerzenia. Domyślnie rozszerzenie występuje według uznania kompilatora na wszystkich funkcji, często nazywane *ze śródwierszowaniem automatycznie*.

**1**  
Umożliwia rozszerzanie tylko funkcje oznaczone [wbudowanego](../../cpp/inline-functions-cpp.md), `__inline`, lub `__forceinline`, lub w funkcji członkowskiej C++, zdefiniowane w deklaracji klasy.

**2**  
Wartość domyślna. Umożliwia rozszerzanie funkcje oznaczone jako `inline`, `__inline`, lub `__forceinline`oraz wszystkie inne funkcje, które wybierze kompilator.

**/ Ob2** jest w życie, kiedy [/O1, / O2 (Minimalizuj rozmiar, Maksymalizuj szybkość)](../../build/reference/o1-o2-minimize-size-maximize-speed.md) lub [OX (Włącz najbardziej prędkości optymalizacji)](../../build/reference/ox-full-optimization.md) jest używany.

Ta opcja wymaga włączenia optymalizacji za pomocą **/O1**, **/O2**, **ox**, lub **/Og**.  

## <a name="remarks"></a>Uwagi

Kompilator traktuje wbudowane opcje rozszerzeń i słowa kluczowe jako sugestie. Nie ma żadnej gwarancji, że dowolnej funkcji zostaną rozwinięte wbudowanego. Można wyłączyć rozszerzenia w tekście, ale nie może wymusić kompilator wbudowanego konkretną funkcję, nawet w przypadku używania `__forceinline` — słowo kluczowe.

Można użyć `#pragma` [auto_inline](../../preprocessor/auto-inline.md) dyrektywy do wykluczenia z brany pod uwagę jako kandydatów do rozszerzenie funkcji wbudowanej funkcji. Zobacz też `#pragma` [wewnętrzne](../../preprocessor/intrinsic.md) dyrektywy.

> [!NOTE]
> Informacje, które są zbierane z profilowania uruchomień testów zastępuje optymalizacji, które w przeciwnym razie będą w efekcie Jeśli określisz **/Ob**, **/OS**, lub **/Ot**. Aby uzyskać więcej informacji, zobacz [optymalizacje Profile-Guided](../../build/reference/profile-guided-optimizations.md).

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Aby ustawić tę opcję kompilatora w środowisku programowania Visual Studio

1. Otwórz projekt **strony właściwości** okno dialogowe. Aby uzyskać więcej informacji, zobacz [Praca z właściwościami projektu](../../ide/working-with-project-properties.md).

1. Rozwiń węzeł **właściwości konfiguracji**, **C/C++**i wybierz **optymalizacji**.

1. Modyfikowanie **rozwijania funkcji śródwierszowych** właściwości.

### <a name="to-set-this-compiler-option-programmatically"></a>Aby programowo ustawić tę opcję kompilatora

- Zobacz <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.InlineFunctionExpansion%2A>.

## <a name="see-also"></a>Zobacz też

[/O Opcje (Optymalizuj kod)](../../build/reference/o-options-optimize-code.md)  
[Opcje kompilatora](../../build/reference/compiler-options.md)  
[Ustawianie opcji kompilatora](../../build/reference/setting-compiler-options.md)