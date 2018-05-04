---
title: -FC (pełna ścieżka pliku kodu źródłowego w diagnostyce) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- VC.Project.VCCLCompilerTool.UseFullPaths
- /FC
dev_langs:
- C++
helpviewer_keywords:
- /FC compiler option [C++]
- -FC compiler option [C++]
ms.assetid: 1f11414e-cb42-421b-be68-9d369aab036b
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 4a721b6887b6c5c07d96a79b06f05e6d7855250b
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
---
# <a name="fc-full-path-of-source-code-file-in-diagnostics"></a>/FC (Pełna ścieżka pliku kodu źródłowego w Diagnostyce)

Powoduje, że kompilator, aby wyświetlić pełną ścieżkę przekazane do kompilatora w diagnostyce plików kodu źródłowego.

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

Bez **/FC**, diagnostyczny będzie wyglądać podobny do następującego diagnostycznych:

- compiler_option_FC.cpp(5): błąd C2143: błąd składni: Brak ";" przed "}"

Z **/FC**, diagnostyczny będzie wyglądać podobny do następującego diagnostycznych:

- c:\test\compiler_option_fc.cpp(5): błąd C2143: błąd składni: Brak ";" przed "}"

 **/FC** również jest niezbędny, jeśli chcesz wyświetlić pełną ścieżkę nazwy pliku, korzystając z &#95; &#95;pliku&#95; &#95; makra. Zobacz [wstępnie zdefiniowane makra](../../preprocessor/predefined-macros.md) Aby uzyskać więcej informacji na temat &#95; &#95;pliku&#95;&#95;.

**/FC** implikuje przez **/zi**. Aby uzyskać więcej informacji na temat **/zi**, zobacz [/z7, / zi, /ZI (Format informacji debugowania)](../../build/reference/z7-zi-zi-debug-information-format.md).

**/FC** generuje pełnych ścieżek w małe litery.

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Aby ustawić tę opcję kompilatora w środowisku programowania Visual Studio

1. Otwórz projekt **strony właściwości** okno dialogowe. Aby uzyskać więcej informacji, zobacz [Praca z właściwościami projektu](../../ide/working-with-project-properties.md).

1. Wybierz **właściwości konfiguracji** > **C/C++** > **zaawansowane** strony właściwości.

1. Modyfikowanie **używaj pełnych ścieżek** właściwości.

### <a name="to-set-this-linker-option-programmatically"></a>Aby programowo ustawić tę opcję konsolidatora

- Zobacz <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.UseFullPaths%2A>.

## <a name="see-also"></a>Zobacz też

[Opcje kompilatora](../../build/reference/compiler-options.md)   
[Ustawianie opcji kompilatora](../../build/reference/setting-compiler-options.md)
