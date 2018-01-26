---
title: / Qsafe_fp_loads | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 01/24/2018
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: e079e084c641318c9bec0820263487139b4d5076
ms.sourcegitcommit: 9a0a287d6940591523af959ebdac5affa36220da
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/25/2018
---
# <a name="qsafefploads"></a>/Qsafe_fp_loads

Wymaga instrukcje przenoszenia całkowitą dla wartości zmiennoprzecinkowych i wyłącza optymalizacje niektórych zmiennoprzecinkowe obciążenia.

## <a name="syntax"></a>Składnia

> **/Qsafe_fp_loads**

## <a name="remarks"></a>Uwagi

**/ Qsafe_fp_loads** jest dostępna tylko w kompilatory który docelowe x86; nie jest dostępna w kompilatorów, które odnoszą się do x64 lub ARM.

**/ Qsafe_fp_loads** wymusza kompilator, aby używał instrukcje przenoszenia całkowitą zamiast instrukcji zmiennoprzecinkowych Przenieś do przenoszenia danych między pamięci i MMX rejestruje. Ta opcja umożliwia wyłączenie rejestrowania obciążenia optymalizacji liczb zmiennoprzecinkowych wartości, które mogą być ładowane w wielu ścieżek formantu, gdy wartość może spowodować wyjątek przy ładowaniu — na przykład wartości NaN.

Ta opcja jest zastępowana [/FP: except](../../build/reference/fp-specify-floating-point-behavior.md). **/ Qsafe_fp_loads** określa podzestaw zachowanie kompilatora, określonej przez **/FP: except**.

**/ Qsafe_fp_loads** jest niezgodny z [/CLR](../../build/reference/clr-common-language-runtime-compilation.md) i [Fast](../../build/reference/fp-specify-floating-point-behavior.md). Aby uzyskać więcej informacji na temat ruchomy punkt — opcje kompilatora, zobacz [/fp (określenie zachowania Floating-Point)](../../build/reference/fp-specify-floating-point-behavior.md).

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Aby ustawić tę opcję kompilatora w środowisku programowania Visual Studio

1. Otwórz projekt **strony właściwości** okno dialogowe. Aby uzyskać więcej informacji, zobacz [Praca z właściwościami projektu](../../ide/working-with-project-properties.md).

1. Wybierz **właściwości konfiguracji** > **C/C++** > **wiersza polecenia** strony właściwości.

1. Wybierz opcję kompilatora w **dodatkowe opcje** pole. Wybierz **OK** do zastosowania zmiany.

### <a name="to-set-this-compiler-option-programmatically"></a>Aby programowo ustawić tę opcję kompilatora

- Zobacz <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>.

## <a name="see-also"></a>Zobacz także

[/Q Opcje (Operacje na niskim poziomie)](../../build/reference/q-options-low-level-operations.md)  
[Opcje kompilatora](../../build/reference/compiler-options.md)  
[Ustawianie opcji kompilatora](../../build/reference/setting-compiler-options.md)  
