---
title: /O1, /O2 (Minimalizuj rozmiar, maksymalizuj szybkość)
ms.date: 09/25/2017
f1_keywords:
- /o2
- /o1
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
ms.openlocfilehash: 3daf5dd5f9912194fd5d8aaeb4c7a312be142b69
ms.sourcegitcommit: 6b749db14b4cf3a2b8d581fda6fdd8cb98bc3207
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/05/2020
ms.locfileid: "82825351"
---
# <a name="o1-o2-minimize-size-maximize-speed"></a>/O1, /O2 (Minimalizuj rozmiar, maksymalizuj szybkość)

Wybiera wstępnie zdefiniowany zestaw opcji, które wpływają na rozmiar i szybkość wygenerowanego kodu.

## <a name="syntax"></a>Składnia

> O1
> /O2

## <a name="remarks"></a>Uwagi

Opcje kompilatora **/O1** i **/O2** to szybka metoda ustawiania kilku konkretnych opcji optymalizacji. Opcja **/O1** ustawia poszczególne opcje optymalizacji, które tworzą najmniejszy kod w większości przypadków. Opcja **/O2** ustawia opcje, które tworzą najszybszy kod w większości przypadków. Opcja **/O2** jest wartością domyślną dla kompilacji wydań. W tej tabeli przedstawiono konkretne opcje, które są ustawiane przez **/O1** i **/O2**:

|Opcja|Równoważne|
|------------|-------------------|
|**/O1** (Minimalizuj rozmiar)|[/Og](og-global-optimizations.md) [/OS](os-ot-favor-small-code-favor-fast-code.md) [/Oy](oy-frame-pointer-omission.md) [/Ob2](ob-inline-function-expansion.md) [/GF](gf-eliminate-duplicate-strings.md) [/Gy](gy-enable-function-level-linking.md)|
|**/O2** (maksymalizuj szybkość)|[/Og](og-global-optimizations.md) [/Oi](oi-generate-intrinsic-functions.md) [/OT](os-ot-favor-small-code-favor-fast-code.md) [/Oy](oy-frame-pointer-omission.md) [/Ob2](ob-inline-function-expansion.md) [/GF](gf-eliminate-duplicate-strings.md) [/Gy](gy-enable-function-level-linking.md)|

**/O1** i **/O2** wzajemnie się wykluczają.

> [!NOTE]
> **Specyficzne dla architektury x86**\
> Te opcje implikują użycie opcji pomijania wskaźnika ramki ([/Oy](oy-frame-pointer-omission.md)).

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Aby ustawić tę opcję kompilatora w środowisku programowania Visual Studio

1. Otwórz okno dialogowe **strony właściwości** projektu. Aby uzyskać szczegółowe informacje, zobacz [Ustawianie kompilatora C++ i właściwości kompilacji w programie Visual Studio](../working-with-project-properties.md).

1. W obszarze **Właściwości konfiguracji**Otwórz język **C/C++** , a następnie wybierz stronę właściwości **Optymalizacja** .

1. Zmodyfikuj właściwość **optymalizacji** .

### <a name="to-set-this-compiler-option-programmatically"></a>Aby programowo ustawić tę opcję kompilatora

- Zobacz: <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.Optimization%2A>.

## <a name="see-also"></a>Zobacz także

[/O Opcje (optymalizuj kod)](o-options-optimize-code.md)<br/>
[Opcje kompilatora MSVC](compiler-options.md)<br/>
[Składnia wiersza polecenia kompilatora MSVC](compiler-command-line-syntax.md)<br/>
[/EH (Model obsługi wyjątku)](eh-exception-handling-model.md)
