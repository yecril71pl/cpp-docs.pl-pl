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
ms.openlocfilehash: d33fe6bceae09267fd3f79ffe3dc26864e87c764
ms.sourcegitcommit: 8105b7003b89b73b4359644ff4281e1595352dda
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2019
ms.locfileid: "57820588"
---
# <a name="o1-o2-minimize-size-maximize-speed"></a>/O1, /O2 (Minimalizuj rozmiar, maksymalizuj szybkość)

Wybiera zestaw wstępnie zdefiniowanych opcji, które wpływają na rozmiar i prędkość wygenerowanego kodu.

## <a name="syntax"></a>Składnia

> /O1 /O2

## <a name="remarks"></a>Uwagi

**/O1** i **/O2** opcje kompilatora są szybko ustawić kilka opcji optymalizacji określone jednocześnie. **/O1** opcja ustawia opcje optymalizacji poszczególnych Utwórz najmniejszych kod w większości przypadków. **/O2** opcja ustawia opcje tworzenia najszybszy kod w większości przypadków. **/O2** opcji jest ustawieniem domyślnym dla kompilacji wydania. W poniższej tabeli przedstawiono określone opcje, które są ustawiane przez **/O1** i **/O2**:

|Opcja|Wartość równoważna|
|------------|-------------------|
|**/ O1** (minimalizacja rozmiaru)|[/Og](og-global-optimizations.md) [/Os](os-ot-favor-small-code-favor-fast-code.md) [/Oy](oy-frame-pointer-omission.md) [/ob2](ob-inline-function-expansion.md) [/GF](gf-eliminate-duplicate-strings.md) [/Gy](gy-enable-function-level-linking.md)|
|**/ O2** (Maksymalizuj szybkość)|[/Og](og-global-optimizations.md) [/Oi](oi-generate-intrinsic-functions.md) [/Ot](os-ot-favor-small-code-favor-fast-code.md) [/Oy](oy-frame-pointer-omission.md) [/ob2](ob-inline-function-expansion.md) [/GF](gf-eliminate-duplicate-strings.md) [/Gy](gy-enable-function-level-linking.md)|

**/ O1** i **/O2** wzajemnie się wykluczają.

> [!NOTE]
> **x86 określonych** te opcje oznaczają użytkowania pominięcie wskaźnika ramki ([/Oy](oy-frame-pointer-omission.md)) opcji.

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Aby ustawić tę opcję kompilatora w środowisku programowania Visual Studio

1. Otwórz projekt **stron właściwości** okno dialogowe. Aby uzyskać więcej informacji, zobacz [kompilatora i tworzenia właściwości ustaw C++ w programie Visual Studio](../working-with-project-properties.md).

1. W obszarze **właściwości konfiguracji**, otwórz **C/C++** , a następnie wybierz **optymalizacji** stronę właściwości.

1. Modyfikowanie **optymalizacji** właściwości.

### <a name="to-set-this-compiler-option-programmatically"></a>Aby programowo ustawić tę opcję kompilatora

- Zobacz <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.Optimization%2A>.

## <a name="see-also"></a>Zobacz także

[/O Opcje (Optymalizuj kod)](o-options-optimize-code.md)<br/>
[MSVC Compiler Options](compiler-options.md)<br/>
[Składnia wiersza polecenia kompilatora MSVC](compiler-command-line-syntax.md)<br/>
[/EH (Model obsługi wyjątku)](eh-exception-handling-model.md)
