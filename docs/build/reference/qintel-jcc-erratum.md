---
title: /QIntel-jcc-erratum
description: Opisuje opcję/QIntel-jcc-erratum języka MicrosoftC++ C/COMPILER (MSVC).
ms.date: 01/07/2020
f1_keywords:
- QIntel-jcc-erratum
helpviewer_keywords:
- /QIntel-jcc-erratum
- -QIntel-jcc-erratum
ms.openlocfilehash: f311da04b833b06124c5e6237ea83a31319858ca
ms.sourcegitcommit: a930a9b47bd95599265d6ba83bb87e46ae748949
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/22/2020
ms.locfileid: "76520880"
---
# <a name="qintel-jcc-erratum"></a>/QIntel-jcc-erratum

::: moniker range="<=vs-2017"

Opcja **/QIntel-JCC-Erratum** jest dostępna w programie Visual Studio 2019 w wersji 16,5 lub nowszej.

::: moniker-end

::: moniker range=">=vs-2019"

Określa, że kompilator generuje instrukcje w celu ograniczenia wpływu na wydajność spowodowany przez kod warunkowy Intel skoku (JCC) sprawdzenia erraty włączenia mikrokodu Update w niektórych procesorach Intel.

## <a name="syntax"></a>Składnia

> **/QIntel-jcc-erratum**

## <a name="remarks"></a>Uwagi

W obszarze **/QIntel-JCC-Erratum**kompilator wykrywa Instrukcje skoku i odrzucania makr, które przecinają się lub kończą na 32-bajtowych granicach. Wyrównuje te instrukcje do granicy. Ta zmiana zmniejsza wpływ na wydajność aktualizacji włączenia mikrokodu, które uniemożliwiają JCC sprawdzenia erraty w niektórych procesorach Intel. Aby uzyskać więcej informacji na temat sprawdzenia erraty, zobacz środki [zaradcze dla sprawdzenia erraty kodu warunkowego](https://www.intel.com/content/dam/support/us/en/documents/processors/mitigations-jump-conditional-code-erratum.pdf) w witrynie sieci Web firmy Intel.

Opcja **/QIntel-JCC-Erratum** jest dostępna w programie Visual Studio 2019 w wersji 16,5 lub nowszej. Ta opcja jest dostępna tylko w kompilatorach przeznaczonych dla procesorów x86 i x64. Opcja jest niedostępna w kompilatorach przeznaczonych dla procesorów ARM.

Opcja **/QIntel-JCC-Erratum** jest domyślnie wyłączona i działa tylko w zoptymalizowanych kompilacjach. Ta opcja umożliwia zwiększenie rozmiaru kodu.

**/QIntel-JCC-Erratum** jest niezgodny z [/CLR](clr-common-language-runtime-compilation.md).

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Aby ustawić tę opcję kompilatora w środowisku programowania Visual Studio

1. Otwórz okno dialogowe **strony właściwości** projektu. Aby uzyskać szczegółowe informacje, zobacz [ C++ Ustawianie właściwości kompilatora i Build w programie Visual Studio](../working-with-project-properties.md).

1. Wybierz **Właściwości konfiguracji** > stronie właściwości **generowanie kodu** **C++ C/** >.

1. Wybierz wartość właściwości **enable Intel JCC sprawdzenia erraty** . Wybierz **przycisk OK** , aby zastosować zmianę.

### <a name="to-set-this-compiler-option-programmatically"></a>Aby programowo ustawić tę opcję kompilatora

- Zobacz <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>.

## <a name="see-also"></a>Zobacz także

[/Q opcji (operacje na niskim poziomie)](q-options-low-level-operations.md)\
[Opcje kompilatora MSVC](compiler-options.md)\
[Składnia wiersza polecenia kompilatora MSVC](compiler-command-line-syntax.md)

::: moniker-end
