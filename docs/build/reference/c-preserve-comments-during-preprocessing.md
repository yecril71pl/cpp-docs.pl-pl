---
title: /C (Zachowaj komentarze podczas przetwarzania wstępnego)
ms.date: 11/04/2016
f1_keywords:
- VC.Project.VCCLCompilerTool.KeepComments
- /c
- VC.Project.VCCLWCECompilerTool.KeepComments
helpviewer_keywords:
- comments, not stripping during preprocessing
- preserve comments during preprocessing
- -c compiler option [C++]
- c compiler option [C++]
- /c compiler option [C++]
ms.assetid: 944567ca-16bc-4728-befe-d414a7787f26
ms.openlocfilehash: b37e279af3995bd1d61c97dc88b49cdd95495c75
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50442604"
---
# <a name="c-preserve-comments-during-preprocessing"></a>/C (Zachowaj komentarze podczas przetwarzania wstępnego)

Zachowuje komentarze podczas przetwarzania wstępnego.

## <a name="syntax"></a>Składnia

```
/C
```

## <a name="remarks"></a>Uwagi

Ta opcja kompilatora wymaga **/E**, **/P**, lub **/EP** opcji.

Poniższy przykładowy kod wyświetli komentarz do kodu źródłowego.

```
// C_compiler_option.cpp
// compile with: /E /C /c
int i;   // a variable
```

Ten przykład generuje następujące dane wyjściowe.

```
#line 1 "C_compiler_option.cpp"
int i;   // a variable
```

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Aby ustawić tę opcję kompilatora w środowisku programowania Visual Studio

1. Otwórz projekt **stron właściwości** okno dialogowe. Aby uzyskać więcej informacji, zobacz [Praca z właściwościami projektu](../../ide/working-with-project-properties.md).

1. Kliknij przycisk **C/C++** folderu.

1. Kliknij przycisk **preprocesora** stronę właściwości.

1. Modyfikowanie **Zachowaj komentarze** właściwości.

### <a name="to-set-this-compiler-option-programmatically"></a>Aby programowo ustawić tę opcję kompilatora

- Zobacz <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.KeepComments%2A>.

## <a name="see-also"></a>Zobacz też

[Opcje kompilatora](../../build/reference/compiler-options.md)<br/>
[Ustawianie opcji kompilatora](../../build/reference/setting-compiler-options.md)<br/>
[/E (Przetwarzaj wstępnie do stdout)](../../build/reference/e-preprocess-to-stdout.md)<br/>
[/P (Przetwarzaj wstępnie do pliku)](../../build/reference/p-preprocess-to-a-file.md)<br/>
[/EP (Wstępnie przetwórz do stdout bez dyrektyw #line)](../../build/reference/ep-preprocess-to-stdout-without-hash-line-directives.md)