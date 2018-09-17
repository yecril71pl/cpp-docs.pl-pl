---
title: -O1, - O2 (Minimalizuj rozmiar, Maksymalizuj szybkość) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 09/25/2017
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- /o2
- /o1
dev_langs:
- C++
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
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 832ea689b2db9a34b55664b695747079ac277bae
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/17/2018
ms.locfileid: "45702562"
---
# <a name="o1-o2-minimize-size-maximize-speed"></a>/O1, /O2 (Minimalizuj rozmiar, maksymalizuj szybkość)

Wybiera zestaw wstępnie zdefiniowanych opcji, które wpływają na rozmiar i prędkość wygenerowanego kodu.

## <a name="syntax"></a>Składnia

> / O1, / O2

## <a name="remarks"></a>Uwagi

**/O1** i **/O2** opcje kompilatora są szybko ustawić kilka opcji optymalizacji określone jednocześnie. **/O1** opcja ustawia opcje optymalizacji poszczególnych Utwórz najmniejszych kod w większości przypadków. **/O2** opcja ustawia opcje tworzenia najszybszy kod w większości przypadków. **/O2** opcji jest ustawieniem domyślnym dla kompilacji wydania. W poniższej tabeli przedstawiono określone opcje, które są ustawiane przez **/O1** i **/O2**:

|Opcja|Wartość równoważna|
|------------|-------------------|
|**/ O1** (minimalizacja rozmiaru)|[/Og](../../build/reference/og-global-optimizations.md) [/Os](../../build/reference/os-ot-favor-small-code-favor-fast-code.md) [/Oy](../../build/reference/oy-frame-pointer-omission.md) [/ob2](../../build/reference/ob-inline-function-expansion.md) [/GF](../../build/reference/gf-eliminate-duplicate-strings.md) [/Gy](../../build/reference/gy-enable-function-level-linking.md)|
|**/ O2** (Maksymalizuj szybkość)|[/Og](../../build/reference/og-global-optimizations.md) [/Oi](../../build/reference/oi-generate-intrinsic-functions.md) [/Ot](../../build/reference/os-ot-favor-small-code-favor-fast-code.md) [/Oy](../../build/reference/oy-frame-pointer-omission.md) [/ob2](../../build/reference/ob-inline-function-expansion.md) [/GF](../../build/reference/gf-eliminate-duplicate-strings.md) [/Gy](../../build/reference/gy-enable-function-level-linking.md)|

**/ O1** i **/O2** wzajemnie się wykluczają.

> [!NOTE]
> **x86 określonych** te opcje oznaczają użytkowania pominięcie wskaźnika ramki ([/Oy](../../build/reference/oy-frame-pointer-omission.md)) opcji.

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Aby ustawić tę opcję kompilatora w środowisku programowania Visual Studio

1. Otwórz projekt **stron właściwości** okno dialogowe. Aby uzyskać więcej informacji, zobacz [Praca z właściwościami projektu](../../ide/working-with-project-properties.md).

1. W obszarze **właściwości konfiguracji**, otwórz **C/C++** , a następnie wybierz **optymalizacji** stronę właściwości.

1. Modyfikowanie **optymalizacji** właściwości.

### <a name="to-set-this-compiler-option-programmatically"></a>Aby programowo ustawić tę opcję kompilatora

- Zobacz <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.Optimization%2A>.

## <a name="see-also"></a>Zobacz też

[/O opcje (Optymalizuj kod)](../../build/reference/o-options-optimize-code.md)
[opcje kompilatora](../../build/reference/compiler-options.md)<br/>
[Ustawianie opcji kompilatora](../../build/reference/setting-compiler-options.md)<br/>
[/EH (Model obsługi wyjątku)](../../build/reference/eh-exception-handling-model.md)
