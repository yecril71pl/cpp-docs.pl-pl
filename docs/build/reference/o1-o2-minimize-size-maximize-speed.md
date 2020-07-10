---
title: /O1, /O2 (Minimalizuj rozmiar, maksymalizuj szybkość)
description: Opcje kompilatora MSVC/O1 i/O2 określają wszystkie optymalizacje dla minimalnej wielkości lub maksymalnej prędkości.
ms.date: 07/08/2020
f1_keywords:
- /O2
- /O1
helpviewer_keywords:
- maximize speed compiler option [C++]
- minimize size compiler option [C++]
- -O2 compiler option [C++]
- fast code
- small code
- O2 compiler option [C++]
- /O2 compiler option [C++]
- -O1 compiler option [C++]
- O1 compiler option [C++]
- /O1 compiler option [C++]
ms.assetid: 2d1423f5-53d9-44da-8908-b33a351656c2
ms.openlocfilehash: c1eda8395e604468cbb23572ec930d6171984fe4
ms.sourcegitcommit: 80c8a512b361bd84e38958beb1a1bf6db7434021
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/09/2020
ms.locfileid: "86180906"
---
# <a name="o1-o2-minimize-size-maximize-speed"></a>`/O1`, `/O2` (Minimalizuj rozmiar, maksymalizuj szybkość)

Wybiera wstępnie zdefiniowany zestaw opcji, które wpływają na rozmiar i szybkość wygenerowanego kodu.

## <a name="syntax"></a>Składnia

> **`/O1`**\
> **`/O2`**

## <a name="remarks"></a>Uwagi

**`/O1`** **`/O2`** Opcje kompilatora i są szybkim sposobem ustawiania kilku konkretnych opcji optymalizacji jednocześnie. **`/O1`** Opcja ustawia indywidualne opcje optymalizacji, które tworzą najmniejszy kod w większości przypadków. **`/O2`** Opcja ustawia opcje, które tworzą najszybszy kod w większości przypadków. **`/O2`** Opcja jest wartością domyślną dla kompilacji wydań. W tej tabeli przedstawiono konkretne opcje, które są ustawiane przez program **`/O1`** i **`/O2`** :

| Opcja | Równoważne |
|--|--|
| **`/O1`**(Minimalizuj rozmiar) | [`/Og`](og-global-optimizations.md) [`/Os`](os-ot-favor-small-code-favor-fast-code.md) [`/Oy`](oy-frame-pointer-omission.md) [`/Ob2`](ob-inline-function-expansion.md) [`/GF`](gf-eliminate-duplicate-strings.md) [`/Gy`](gy-enable-function-level-linking.md) |
| **`/O2`**(Maksymalizuj szybkość) | [`/Og`](og-global-optimizations.md) [`/Oi`](oi-generate-intrinsic-functions.md) [`/Ot`](os-ot-favor-small-code-favor-fast-code.md) [`/Oy`](oy-frame-pointer-omission.md) [`/Ob2`](ob-inline-function-expansion.md) [`/GF`](gf-eliminate-duplicate-strings.md) [`/Gy`](gy-enable-function-level-linking.md) |

**`/O1`** i wykluczają **`/O2`** się wzajemnie.

> [!NOTE]
> **specyficzne dla architektury x86**\
> Te opcje implikują użycie opcji pomijania wskaźnika ramki ( [`/Oy`](oy-frame-pointer-omission.md) ).

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Aby ustawić tę opcję kompilatora w środowisku programowania Visual Studio

1. Otwórz okno dialogowe **strony właściwości** projektu. Aby uzyskać szczegółowe informacje, zobacz [Ustawianie kompilatora C++ i właściwości kompilacji w programie Visual Studio](../working-with-project-properties.md).

1. Wybierz **Configuration Properties**  >  stronę właściwości optymalizacji**C/C++** właściwości konfiguracji  >  **Optimization** .

1. Zmodyfikuj właściwość **optymalizacji** .

### <a name="to-set-this-compiler-option-programmatically"></a>Aby programowo ustawić tę opcję kompilatora

- Zobacz: <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.Optimization%2A>.

## <a name="see-also"></a>Zobacz też

[`/O`Opcje (Optymalizuj kod)](o-options-optimize-code.md)<br/>
[Opcje kompilatora MSVC](compiler-options.md)<br/>
[Składnia wiersza polecenia kompilatora MSVC](compiler-command-line-syntax.md)<br/>
[`/EH`(Model obsługi wyjątków)](eh-exception-handling-model.md)
