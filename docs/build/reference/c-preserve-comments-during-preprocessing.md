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
ms.openlocfilehash: 6d0cf8e5f628f3f5301f54d7c853bfc2ab63cb7e
ms.sourcegitcommit: 573b36b52b0de7be5cae309d45b68ac7ecf9a6d8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/10/2019
ms.locfileid: "74988357"
---
# <a name="c-preserve-comments-during-preprocessing"></a>/C (Zachowaj komentarze podczas przetwarzania wstępnego)

Zachowuje komentarze podczas przetwarzania wstępnego.

## <a name="syntax"></a>Składnia

```
/C
```

## <a name="remarks"></a>Uwagi

Ta opcja kompilatora wymaga opcji **/e**, **/p**lub **/EP** .

Poniższy przykład kodu wyświetli komentarz do kodu źródłowego.

```cpp
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

1. Otwórz okno dialogowe **strony właściwości** projektu. Aby uzyskać szczegółowe informacje, zobacz [ C++ Ustawianie właściwości kompilatora i Build w programie Visual Studio](../working-with-project-properties.md).

1. Kliknij folder **C/C++**  .

1. Kliknij stronę właściwości **preprocesora** .

1. Zmodyfikuj właściwość **Zachowaj Komentarze** .

### <a name="to-set-this-compiler-option-programmatically"></a>Aby programowo ustawić tę opcję kompilatora

- Zobacz <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.KeepComments%2A>.

## <a name="see-also"></a>Zobacz także

[Opcje kompilatora MSVC](compiler-options.md)<br/>
[Składnia wiersza polecenia kompilatora MSVC](compiler-command-line-syntax.md)<br/>
[/E (Przetwarzaj wstępnie do stdout)](e-preprocess-to-stdout.md)<br/>
[/P (Przetwarzaj wstępnie do pliku)](p-preprocess-to-a-file.md)<br/>
[/EP (Wstępnie przetwórz do stdout bez dyrektyw #line)](ep-preprocess-to-stdout-without-hash-line-directives.md)
