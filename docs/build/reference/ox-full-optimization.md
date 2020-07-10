---
title: /OX (Włącz optymalizację z największą szybkością)
description: Opcja MSVC/OX łączy niektóre opcje optymalizacji kompilatora umożliwiające przyspieszenie w jednej opcji.
ms.date: 07/08/2020
f1_keywords:
- VC.Project.VCCLCompilerTool.ToolOptimization
- /Ox
- /Oxs
helpviewer_keywords:
- Ox compiler option [C++]
- fast code [C++]
- /Ox compiler option [C++]
- -Ox compiler option [C++]
ms.assetid: 3ad7c30b-c615-428c-b1d0-2e024f81c760
ms.openlocfilehash: 10893fe1cf032f2ab56f27aa4af95b050c2ec37e
ms.sourcegitcommit: 80c8a512b361bd84e38958beb1a1bf6db7434021
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/09/2020
ms.locfileid: "86180841"
---
# <a name="ox-enable-most-speed-optimizations"></a>`/Ox`(Włącz optymalizację z największą szybkością)

**`/Ox`** Opcja kompilatora umożliwia łączenie optymalizacji, które preferują szybkość. W niektórych wersjach środowiska IDE programu Visual Studio i komunikatu pomocy kompilatora jest on nazywany *pełną optymalizacją*, ale **`/Ox`** Opcja kompilatora umożliwia tylko podzbiór opcji optymalizacji szybkości włączonej przez program **`/O2`** .

## <a name="syntax"></a>Składnia

> **`/Ox`**

## <a name="remarks"></a>Uwagi

**`/Ox`** Opcja kompilatora włącza **`/O`** Opcje kompilatora, które preferują szybkość. **`/Ox`** Opcja kompilatora nie zawiera dodatkowych [ `/GF` (eliminując zduplikowane ciągi)](gf-eliminate-duplicate-strings.md) i [ `/Gy` (Włącz łączenie na poziomie funkcji)](gy-enable-function-level-linking.md) włączonych przez [ `/O1` lub `/O2` (Minimalizuj rozmiar, maksymalizuj szybkość)](o1-o2-minimize-size-maximize-speed.md). Dodatkowe opcje stosowane przez program **`/O1`** i **`/O2`** mogą spowodować, że wskaźniki do ciągów lub do funkcji współużytkują adres docelowy, co może mieć wpływ na Debugowanie i ścisłą zgodność języka. **`/Ox`** Opcja jest łatwym sposobem na włączenie większości optymalizacji bez uwzględniania **`/GF`** i **`/Gy`** . Aby uzyskać więcej informacji, zobacz opisy [`/GF`](gf-eliminate-duplicate-strings.md) [`/Gy`](gy-enable-function-level-linking.md) opcji i.

**`/Ox`** Opcja kompilatora jest taka sama jak w połączeniu z następującymi opcjami:

- [ `/Ob` (Rozszerzenie funkcji wbudowanej)](ob-inline-function-expansion.md), gdzie parametr opcji ma wartość 2 ( **`/Ob2`** )

- [`/Oi`(Generuj funkcje wewnętrzne)](oi-generate-intrinsic-functions.md)

- [`/Ot`(Preferuj szybki kod)](os-ot-favor-small-code-favor-fast-code.md)

- [`/Oy`(Pominięcie wskaźnika ramki)](oy-frame-pointer-omission.md)

**`/Ox`** wykluczają się wzajemnie z:

- [`/O1`(Minimalizuj rozmiar)](o1-o2-minimize-size-maximize-speed.md)

- [`/O2`(Maksymalizuj szybkość)](o1-o2-minimize-size-maximize-speed.md)

- [`/Od`(Wyłącz (Debuguj))](od-disable-debug.md)

Możesz anulować odchylenia w kierunku **`/Ox`** opcji kompilatora, jeśli zostanie określona **`/Oxs`** , która łączy **`/Ox`** opcję kompilatora z [ `/Os` (Preferuj mały kod)](os-ot-favor-small-code-favor-fast-code.md). Połączone opcje preferują mniejszy rozmiar kodu.  **`/Oxs`** Opcja jest dokładnie taka sama jak określenie, **`/Ox`** **`/Os`** kiedy opcje są wyświetlane w danej kolejności.

Aby zastosować wszystkie dostępne optymalizacje na poziomie plików dla kompilacji wydań, zalecamy określenie [ `/O2` (maksymalizuj szybkość)](o1-o2-minimize-size-maximize-speed.md) zamiast **`/Ox`** , i [ `/O1` (minimalizowanie rozmiaru)](o1-o2-minimize-size-maximize-speed.md) zamiast **`/Oxs`** . Aby uzyskać większą optymalizację w kompilacjach wydania, należy również wziąć pod uwagę opcje kompilatora [ `/GL` (Optymalizacja całego programu)](gl-whole-program-optimization.md) i opcję konsolidatora [ `/LTCG` (generowanie kodu w czasie konsolidacji)](ltcg-link-time-code-generation.md) .

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Aby ustawić tę opcję kompilatora w środowisku programowania Visual Studio

1. Otwórz okno dialogowe **strony właściwości** projektu. Aby uzyskać szczegółowe informacje, zobacz [Ustawianie kompilatora C++ i właściwości kompilacji w programie Visual Studio](../working-with-project-properties.md).

1. Wybierz **Configuration Properties**  >  stronę właściwości optymalizacji**C/C++** właściwości konfiguracji  >  **Optimization** .

1. Zmodyfikuj właściwość **optymalizacji** .

### <a name="to-set-this-compiler-option-programmatically"></a>Aby programowo ustawić tę opcję kompilatora

- Zobacz: <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.Optimization%2A>.

## <a name="see-also"></a>Zobacz też

[`/O`Opcje (Optymalizuj kod)](o-options-optimize-code.md)<br/>
[Opcje kompilatora MSVC](compiler-options.md)<br/>
[Składnia wiersza polecenia kompilatora MSVC](compiler-command-line-syntax.md)
