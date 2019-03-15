---
title: /Zc:forScope (Wymuszaj zgodność w zakresie pętli For)
ms.date: 03/06/2018
f1_keywords:
- VC.Project.VCCLCompilerTool.ForceConformanceInForLoopScope
- VC.Project.VCCLWCECompilerTool.ForceConformanceInForLoopScope
- /zc:forScope
helpviewer_keywords:
- /Zc compiler options [C++]
- -Zc compiler options [C++]
- Conformance compiler options
- Zc compiler options [C++]
ms.assetid: 3031f02d-3b14-4ad0-869e-22b0110c3aed
ms.openlocfilehash: 7f98667d3a771994d1b4e54b429f42cb566c102c
ms.sourcegitcommit: 8105b7003b89b73b4359644ff4281e1595352dda
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2019
ms.locfileid: "57810259"
---
# <a name="zcforscope-force-conformance-in-for-loop-scope"></a>/Zc:forScope (Wymuszaj zgodność w zakresie pętli For)

Używany do implementowania standardowego zachowania C++ dla [dla](../../cpp/for-statement-cpp.md) pętli for z rozszerzeniami Microsoft ([/Ze](za-ze-disable-language-extensions.md)).

## <a name="syntax"></a>Składnia

> **/Zc:forScope**[**-**]

## <a name="remarks"></a>Uwagi

Standardowe zachowanie jest umożliwienie **dla** inicjatora pętli wykraczają poza zakres po **dla** pętli. W obszarze **/Zc:forScope-** i [/Ze](za-ze-disable-language-extensions.md), **dla** inicjatora pętli pozostaje w zakresie do czasu zakończenia zakres lokalny.

**/Zc: forscope** opcja jest domyślnie włączone. **/ Zc: forscope** nie występuje kiedy [/ permissive-](permissive-standards-conformance.md) określono opcję.

**/Zc:forScope-** opcja jest przestarzały i zostanie usunięta w przyszłej wersji. Korzystanie z **/Zc:forScope-** generuje ostrzeżenie d9035 dla wycofywania.

Poniższy kod jest kompilowany w obszarze **/Ze** , ale nie w obszarze **/Za**:

```cpp
// zc_forScope.cpp
// compile by using: cl /Zc:forScope- /Za zc_forScope.cpp
// C2065, D9035 expected
int main() {
    // Compile by using cl /Zc:forScope- zc_forScope.cpp
    // to compile this non-standard code as-is.
    // Uncomment the following line to resolve C2065 for /Za.
    // int i;
    for (int i = 0; i < 1; i++)
        ;
    i = 20;   // i has already gone out of scope under /Za
}
```

Jeśli używasz **/Zc:forScope-**, ostrzeżenie C4288 (funkcja domyślnie wyłączona) jest generowany, gdy zmienna jest w zakresie z powodu deklaracji, która została wprowadzona w poprzednim zakresie. Aby to wykazać, Usuń `//` znaków w przykładowym kodzie, aby zadeklarować `int i`.

Możesz zmodyfikować zachowanie środowiska wykonawczego **/Zc: forscope** przy użyciu [jest zgodna z](../../preprocessor/conform.md) pragmy.

Jeśli używasz **/Zc:forScope-** w projekcie, który ma istniejący plik .pch, generowane jest ostrzeżenie, **/Zc:forScope-** jest ignorowana, a kompilacja jest kontynuowana przy użyciu istniejących plików .pch. Jeśli chcesz, aby plik .pch wygenerowanych, użyj [/Yc (Utwórz prekompilowany plik nagłówkowy)](yc-create-precompiled-header-file.md).

Aby uzyskać więcej informacji na temat problemów ze zgodnością w języku Visual C++, zobacz [niestandardowe zachowanie](../../cpp/nonstandard-behavior.md).

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Aby ustawić tę opcję kompilatora w środowisku programowania Visual Studio

1. Otwórz projekt **stron właściwości** okno dialogowe. Aby uzyskać więcej informacji, zobacz [kompilatora i tworzenia właściwości ustaw C++ w programie Visual Studio](../working-with-project-properties.md).

1. Wybierz **właściwości konfiguracji** > **C/C++** > **języka** stronę właściwości.

1. Modyfikowanie **Wymuszaj zgodność w zakresie pętli — dla** właściwości.

### <a name="to-set-this-compiler-option-programmatically"></a>Aby programowo ustawić tę opcję kompilatora

- Zobacz <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.ForceConformanceInForLoopScope%2A>.

## <a name="see-also"></a>Zobacz także

[/Zc (Zgodność)](zc-conformance.md)<br/>
[/Za, /Ze (Wyłącz rozszerzenia językowe)](za-ze-disable-language-extensions.md)<br/>
