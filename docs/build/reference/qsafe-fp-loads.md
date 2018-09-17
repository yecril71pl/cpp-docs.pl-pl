---
title: / Qsafe_fp_loads | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 01/24/2018
ms.technology:
- cpp-tools
ms.topic: reference
dev_langs:
- C++
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 0af28b391390f28be4e111b55c909dcae66ca2f8
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/17/2018
ms.locfileid: "45713664"
---
# <a name="qsafefploads"></a>/Qsafe_fp_loads

Wymaga całkowitoliczbowych instrukcji przeniesienia dla wartości zmiennopozycyjnych i wyłącza niektóre optymalizację ładowania zmiennoprzecinkowych.

## <a name="syntax"></a>Składnia

> **/Qsafe_fp_loads**

## <a name="remarks"></a>Uwagi

**/ Qsafe_fp_loads** jest dostępna tylko w kompilatorach przeznaczone na platformę x86; nie jest dostępna w kompilatorach, których platformą docelową x64 lub ARM.

**/ Qsafe_fp_loads** rejestruje kompilatorowi używanie całkowitoliczbowych instrukcji przeniesienia zamiast instrukcji zmiennoprzecinkowych przeniesienia do przenoszenia danych między pamięcią i MMX wymusza. Ta opcja powoduje wyłączenie optymalizacji obciążenia rejestru dla wartości zmiennoprzecinkowych, które mogą być ładowane w wielu ścieżek kontroli, gdy wartość może spowodować wyjątek podczas ładowania — na przykład, wartość NaN.

Ta opcja jest zastępowany przez [/FP: except](../../build/reference/fp-specify-floating-point-behavior.md). **/ Qsafe_fp_loads** określa podzestaw zachowanie kompilatora, który jest określony przez **/FP: except**.

**/ Qsafe_fp_loads** jest niezgodny z [/CLR](../../build/reference/clr-common-language-runtime-compilation.md) i [Fast](../../build/reference/fp-specify-floating-point-behavior.md). Aby uzyskać więcej informacji na temat punktu zmiennoprzecinkowego — opcje kompilatora, zobacz [/FP (określenie zachowania zmiennopozycyjna)](../../build/reference/fp-specify-floating-point-behavior.md).

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Aby ustawić tę opcję kompilatora w środowisku programowania Visual Studio

1. Otwórz projekt **stron właściwości** okno dialogowe. Aby uzyskać więcej informacji, zobacz [Praca z właściwościami projektu](../../ide/working-with-project-properties.md).

1. Wybierz **właściwości konfiguracji** > **C/C++** > **wiersza polecenia** stronę właściwości.

1. Wpisz opcję kompilatora w **dodatkowe opcje** pole. Wybierz **OK** do zastosowania zmiany.

### <a name="to-set-this-compiler-option-programmatically"></a>Aby programowo ustawić tę opcję kompilatora

- Zobacz <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>.

## <a name="see-also"></a>Zobacz także

[/Q opcje (operacje na niskim poziomie)](../../build/reference/q-options-low-level-operations.md)
[opcje kompilatora](../../build/reference/compiler-options.md)<br/>
[Ustawianie opcji kompilatora](../../build/reference/setting-compiler-options.md)
