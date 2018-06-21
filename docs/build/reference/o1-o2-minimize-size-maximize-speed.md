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
ms.openlocfilehash: 5003695c5ae2b16faf8aa80f68928858a3a48288
ms.sourcegitcommit: 4cdfff1114829599ab54178767f57664ad3424d1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/20/2018
ms.locfileid: "36270555"
---
# <a name="o1-o2-minimize-size-maximize-speed"></a>/O1, /O2 (Minimalizuj rozmiar, maksymalizuj szybkość)

Wybiera wstępnie zdefiniowane opcje, które mają wpływ na rozmiar i szybkość wygenerowanego kodu.

## <a name="syntax"></a>Składnia

> / O1  
> / O2

## <a name="remarks"></a>Uwagi

**/O1** i **/O2** — opcje kompilatora są szybko ustawić kilka opcji optymalizacji określone jednocześnie. **/O1** opcji ustawia opcje optymalizacji poszczególnych utworzonych najmniejszą kodu w większości przypadków. **/O2** opcji ustawia opcje, które utworzyć najszybszy kod w większości przypadków. **/O2** opcja jest ustawieniem domyślnym dla wersji kompilacji. W poniższej tabeli zamieszczono określone opcje, które są ustawiane przez **/O1** i **/O2**:

|Opcja|Wartość równoważna wartości|
|------------|-------------------|
|**/ O1** (Minimalizuj rozmiar)|[/Og](../../build/reference/og-global-optimizations.md) [/OS](../../build/reference/os-ot-favor-small-code-favor-fast-code.md) [/Oy](../../build/reference/oy-frame-pointer-omission.md) [/ob2](../../build/reference/ob-inline-function-expansion.md) [/GF](../../build/reference/gf-eliminate-duplicate-strings.md) [/Gy](../../build/reference/gy-enable-function-level-linking.md)|
|**/ O2** (Maksymalizuj szybkość)|[/Og](../../build/reference/og-global-optimizations.md) [/Oi](../../build/reference/oi-generate-intrinsic-functions.md) [/Ot](../../build/reference/os-ot-favor-small-code-favor-fast-code.md) [/Oy](../../build/reference/oy-frame-pointer-omission.md) [/ob2](../../build/reference/ob-inline-function-expansion.md) [/GF](../../build/reference/gf-eliminate-duplicate-strings.md) [/Gy](../../build/reference/gy-enable-function-level-linking.md)|

**/ O1** i **/O2** wykluczają się wzajemnie.

> [!NOTE]  
> **x86 Specific**  
> Te opcje oznaczać użycia pominięcie wskaźnika ramki ([/Oy](../../build/reference/oy-frame-pointer-omission.md)) opcja.

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Aby ustawić tę opcję kompilatora w środowisku programowania Visual Studio

1. Otwórz projekt **strony właściwości** okno dialogowe. Aby uzyskać więcej informacji, zobacz [Praca z właściwościami projektu](../../ide/working-with-project-properties.md).

1. W obszarze **właściwości konfiguracji**, otwórz **C/C++** , a następnie wybierz **optymalizacji** strony właściwości.

1. Modyfikowanie **optymalizacji** właściwości.

### <a name="to-set-this-compiler-option-programmatically"></a>Aby programowo ustawić tę opcję kompilatora

- Zobacz <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.Optimization%2A>.

## <a name="see-also"></a>Zobacz też

[/O Opcje (Optymalizuj kod)](../../build/reference/o-options-optimize-code.md)  
[Opcje kompilatora](../../build/reference/compiler-options.md)  
[Ustawianie opcji kompilatora](../../build/reference/setting-compiler-options.md)  
[/EH (Model obsługi wyjątku)](../../build/reference/eh-exception-handling-model.md)
