---
title: /FC (Pełna ścieżka pliku kodu źródłowego w Diagnostyce)
ms.date: 11/04/2016
f1_keywords:
- VC.Project.VCCLCompilerTool.UseFullPaths
- /FC
helpviewer_keywords:
- /FC compiler option [C++]
- -FC compiler option [C++]
ms.assetid: 1f11414e-cb42-421b-be68-9d369aab036b
ms.openlocfilehash: 3629ec35f0be5ebfd384b949acb2910dcbea3318
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50624916"
---
# <a name="fc-full-path-of-source-code-file-in-diagnostics"></a>/FC (Pełna ścieżka pliku kodu źródłowego w Diagnostyce)

Powoduje, że kompilator, aby wyświetlić pełną ścieżkę plików kodu źródłowego przekazanych do kompilatora w diagnostyce.

## <a name="syntax"></a>Składnia

> /FC

## <a name="remarks"></a>Uwagi

Rozważmy poniższy przykładowy kod:

```cpp
// compiler_option_FC.cpp
int main( ) {
   int i   // C2143
}
```

Bez **/FC**, diagnostyczny powinien wyglądać podobnie do tego tekście diagnostycznym:

- compiler_option_FC.cpp(5): błąd C2143: błąd składniowy: brakuje ";" przed "}"

Za pomocą **/FC**, diagnostyczny powinien wyglądać podobnie do tego tekście diagnostycznym:

- c:\test\compiler_option_fc.cpp(5): błąd C2143: błąd składniowy: brakuje ";" przed "}"

**/FC** jest również wymagane, jeśli chcesz wyświetlić pełną ścieżkę nazwę pliku, korzystając z &#95; &#95;pliku&#95; &#95; makra. Zobacz [wstępnie zdefiniowane makra](../../preprocessor/predefined-macros.md) więcej informacji na temat &#95; &#95;pliku&#95;&#95;.

**/FC** opcji jest implikowany przez **/zi**. Aby uzyskać więcej informacji na temat **/zi**, zobacz [/z7, / zi, /ZI (Format informacji debugowania)](../../build/reference/z7-zi-zi-debug-information-format.md).

**/FC** danych wyjściowych pełnych ścieżek w małe litery.

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Aby ustawić tę opcję kompilatora w środowisku programowania Visual Studio

1. Otwórz projekt **stron właściwości** okno dialogowe. Aby uzyskać więcej informacji, zobacz [Praca z właściwościami projektu](../../ide/working-with-project-properties.md).

1. Wybierz **właściwości konfiguracji** > **C/C++** > **zaawansowane** stronę właściwości.

1. Modyfikowanie **używaj pełnych ścieżek** właściwości.

### <a name="to-set-this-linker-option-programmatically"></a>Aby programowo ustawić tę opcję konsolidatora

- Zobacz <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.UseFullPaths%2A>.

## <a name="see-also"></a>Zobacz też

[Opcje kompilatora](../../build/reference/compiler-options.md)<br/>
[Ustawianie opcji kompilatora](../../build/reference/setting-compiler-options.md)
