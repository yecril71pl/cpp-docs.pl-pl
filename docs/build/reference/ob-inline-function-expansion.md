---
title: /Ob (Rozszerzenie funkcji wbudowanej)
ms.date: 08/08/2019
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
ms.openlocfilehash: 238e5533c062678c59b61ebeba71eee3231fb5fb
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/27/2020
ms.locfileid: "87215221"
---
# <a name="ob-inline-function-expansion"></a>/Ob (Rozszerzenie funkcji wbudowanej)

Kontroluje wbudowane rozwijanie funkcji. Domyślnie podczas optymalizowania, rozszerzanie odbywa się zgodnie z uznaniem kompilatora dla wszystkich funkcji, często nazywane *autoskalowaniem*.

## <a name="syntax"></a>Składnia

::: moniker range=">=vs-2019"

> **/Ob**{**0** | **1** | **2** | **3**}

::: moniker-end

::: moniker range="<=vs-2017"

> **/Ob**{**0** | **1** | **2**}

::: moniker-end

## <a name="arguments"></a>Argumenty

**2,0**\
Wartość domyślna w obszarze [/od](od-disable-debug.md). Wyłącza wbudowane rozszerzenia.

**jedno**\
Zezwala na rozszerzanie tylko funkcji oznaczonych jako [inline](../../cpp/inline-functions-cpp.md), [__inline](../../cpp/inline-functions-cpp.md)lub [__forceinline](../../cpp/inline-functions-cpp.md)lub w funkcji składowej C++ zdefiniowanej w deklaracji klasy.

**dwóch**\
Wartość domyślna w obszarze [/O1](o1-o2-minimize-size-maximize-speed.md) i [/O2](o1-o2-minimize-size-maximize-speed.md). Zezwala kompilatorowi na rozwijanie dowolnej funkcji, która nie jest jawnie oznaczona jako niewyróżniający.

::: moniker range=">=vs-2019"

**r.3**\
Ta opcja określa bardziej agresywne wykreślenie poza **/Ob2**, ale ma takie same ograniczenia. Opcja **/Ob3** jest dostępna od programu Visual Studio 2019.

::: moniker-end

## <a name="remarks"></a>Uwagi

Kompilator traktuje wbudowane opcje rozwijania i słowa kluczowe jako sugestie. Nie ma gwarancji, że jakakolwiek funkcja zostanie rozwinięta w tekście. Można wyłączyć rozszerzanie wbudowane, ale nie można wymusić wbudowania określonej funkcji przez kompilator, nawet w przypadku użycia **`__forceinline`** słowa kluczowego.

Aby wykluczyć funkcje z rozważania jako kandydaci do rozwinięcia wbudowane, można użyć [__declspec (NoLine)](../../cpp/noinline.md)lub regionu oznaczonego przez [#pragma auto_inline (off)](../../preprocessor/auto-inline.md) i [#pragma auto_inline (on)](../../preprocessor/auto-inline.md) . Aby uzyskać informacje na temat innego sposobu udostępniania wskazówek dotyczących dekreślenia do kompilatora, zobacz [wewnętrzną dyrektywę #pragma](../../preprocessor/intrinsic.md) .

> [!NOTE]
> Informacje zbierane z przebiegów testów profilowania zastępują optymalizacje, które w przeciwnym razie byłyby stosowane, ponieważ określono **/ob**, **/OS**lub **/OT**. Aby uzyskać więcej informacji, zapoznaj się z tematem [optymalizacje](../profile-guided-optimizations.md)profilowane.

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Aby ustawić tę opcję kompilatora w środowisku programowania Visual Studio

1. Otwórz okno dialogowe **strony właściwości** projektu. Aby uzyskać szczegółowe informacje, zobacz [Ustawianie kompilatora C++ i właściwości kompilacji w programie Visual Studio](../working-with-project-properties.md).

1. Wybierz **Configuration Properties**  >  stronę właściwości optymalizacji**C/C++** właściwości konfiguracji  >  **Optimization** .

1. Zmodyfikuj właściwość **rozwinięcia funkcji wbudowanej** .

::: moniker range=">=vs-2019"

Opcja **/Ob3** jest niedostępna we właściwości **rozwinięcia funkcji wbudowanej** . Aby ustawić **/Ob3**:

1. Otwórz okno dialogowe **strony właściwości** projektu. Aby uzyskać szczegółowe informacje, zobacz [Ustawianie kompilatora C++ i właściwości kompilacji w programie Visual Studio](../working-with-project-properties.md).

1. Wybierz **Configuration Properties** > stronę właściwości konfiguracja wiersza polecenia **C/C++** > **Command Line** .

1. Wprowadź **/Ob3** w polu **Opcje dodatkowe**.

::: moniker-end

### <a name="to-set-this-compiler-option-programmatically"></a>Aby programowo ustawić tę opcję kompilatora

- Zobacz: <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.InlineFunctionExpansion%2A>.

## <a name="see-also"></a>Zobacz także

[/O opcje (Optymalizuj kod)](o-options-optimize-code.md)\
[Opcje kompilatora MSVC](compiler-options.md)\
[Składnia wiersza polecenia kompilatora MSVC](compiler-command-line-syntax.md)
