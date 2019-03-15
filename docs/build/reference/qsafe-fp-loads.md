---
title: /Qsafe_fp_loads
ms.date: 01/24/2018
ms.openlocfilehash: 57aece79dfab617121371e0489aa80f18e143372
ms.sourcegitcommit: faa42c8a051e746d99dcebe70fd4bbaf3b023ace
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2019
ms.locfileid: "57819695"
---
# <a name="qsafefploads"></a>/Qsafe_fp_loads

Wymaga całkowitoliczbowych instrukcji przeniesienia dla wartości zmiennopozycyjnych i wyłącza niektóre optymalizację ładowania zmiennoprzecinkowych.

## <a name="syntax"></a>Składnia

> **/Qsafe_fp_loads**

## <a name="remarks"></a>Uwagi

**/ Qsafe_fp_loads** jest dostępna tylko w kompilatorach przeznaczone na platformę x86; nie jest dostępna w kompilatorach, których platformą docelową x64 lub ARM.

**/ Qsafe_fp_loads** rejestruje kompilatorowi używanie całkowitoliczbowych instrukcji przeniesienia zamiast instrukcji zmiennoprzecinkowych przeniesienia do przenoszenia danych między pamięcią i MMX wymusza. Ta opcja powoduje wyłączenie optymalizacji obciążenia rejestru dla wartości zmiennoprzecinkowych, które mogą być ładowane w wielu ścieżek kontroli, gdy wartość może spowodować wyjątek podczas ładowania — na przykład, wartość NaN.

Ta opcja jest zastępowany przez [/FP: except](fp-specify-floating-point-behavior.md). **/ Qsafe_fp_loads** określa podzestaw zachowanie kompilatora, który jest określony przez **/FP: except**.

**/ Qsafe_fp_loads** jest niezgodny z [/CLR](clr-common-language-runtime-compilation.md) i [Fast](fp-specify-floating-point-behavior.md). Aby uzyskać więcej informacji na temat punktu zmiennoprzecinkowego — opcje kompilatora, zobacz [/FP (określenie zachowania zmiennopozycyjna)](fp-specify-floating-point-behavior.md).

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Aby ustawić tę opcję kompilatora w środowisku programowania Visual Studio

1. Otwórz projekt **stron właściwości** okno dialogowe. Aby uzyskać więcej informacji, zobacz [kompilatora i tworzenia właściwości ustaw C++ w programie Visual Studio](../working-with-project-properties.md).

1. Wybierz **właściwości konfiguracji** > **C/C++** > **wiersza polecenia** stronę właściwości.

1. Wpisz opcję kompilatora w **dodatkowe opcje** pole. Wybierz **OK** do zastosowania zmiany.

### <a name="to-set-this-compiler-option-programmatically"></a>Aby programowo ustawić tę opcję kompilatora

- Zobacz <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>.

## <a name="see-also"></a>Zobacz także

[/Q Opcje (Operacje na niskim poziomie)](q-options-low-level-operations.md)<br/>
[MSVC Compiler Options](compiler-options.md)<br/>
[Składnia wiersza polecenia kompilatora MSVC](compiler-command-line-syntax.md)
