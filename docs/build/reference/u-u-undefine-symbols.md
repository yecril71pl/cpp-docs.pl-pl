---
title: /U, /u (Usuń definicje symboli)
ms.date: 11/04/2016
f1_keywords:
- VC.Project.VCCLCompilerTool.UndefinePreprocessorDefinitions
- VC.Project.VCCLWCECompilerTool.UndefinePreprocessorDefinitions
- VC.Project.VCCLCompilerTool.UndefineAllPreprocessorDefinitions
- /u
- VC.Project.VCCLWCECompilerTool.UndefineAllPreprocessorDefinitions
helpviewer_keywords:
- -U compiler option [C++]
- Undefine Symbols compiler option
- /U compiler option [C++]
- U compiler option [C++]
ms.assetid: 7bc0474f-6d1f-419b-807d-0d8816763b2a
ms.openlocfilehash: bfc03ebd5c900bf8bf81b4a50eed02111baf85ee
ms.sourcegitcommit: 8105b7003b89b73b4359644ff4281e1595352dda
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2019
ms.locfileid: "57822494"
---
# <a name="u-u-undefine-symbols"></a>/U, /u (Usuń definicje symboli)

**/U** — opcja kompilatora jedno anulowanie definicji preprocesora określonego symbolu. **/U** — opcja kompilatora jedno anulowanie definicji symboli specyficzne dla firmy Microsoft, które definiuje kompilator.

## <a name="syntax"></a>Składnia

```
/U[ ]symbol
/u
```

## <a name="arguments"></a>Argumenty

*Symbol*<br/>
Symbol preprocesora aby Usuń.

## <a name="remarks"></a>Uwagi

Ani **/U** lub **/u** opcji odwrócić definiowanie symbolu, który został utworzony przy użyciu **#define** dyrektywy.

**/U** odwrócić definiowanie symbolu, który został uprzednio zdefiniowany przy użyciu opcji **/D** opcji.

Domyślnie kompilator definiuje następujące symbole specyficzne dla firmy Microsoft.

|Symbol|Funkcja|
|------------|--------------|
|_CHAR_UNSIGNED|Domyślny typ char nie został podpisany. Zdefiniowane kiedy [/j.](j-default-char-type-is-unsigned.md) określono opcję.|
|_CPPRTTI|Zdefiniowane dla kodu skompilowanego za pomocą [GR](gr-enable-run-time-type-information.md) opcji.|
|_CPPUNWIND|Zdefiniowane dla kodu skompilowanego za pomocą [/ehsc](eh-exception-handling-model.md) opcji.|
|_DLL|Zdefiniowane kiedy [/MD](md-mt-ld-use-run-time-library.md) określono opcję.|
|_M_IX86|Domyślnie, określony do 600 dla x86 elementów docelowych.|
|_MSC_VER|Aby uzyskać więcej informacji, zobacz [wstępnie zdefiniowane makra](../../preprocessor/predefined-macros.md).|
|_WIN32|Zdefiniowane dla aplikacji WIN32. Zawsze jest zdefiniowana.|
|_MT|Zdefiniowane kiedy [/MD lub/MT](md-mt-ld-use-run-time-library.md) określono opcję.|

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Aby ustawić tę opcję kompilatora w środowisku programowania Visual Studio

1. Otwórz projekt **stron właściwości** okno dialogowe. Aby uzyskać więcej informacji, zobacz [kompilatora i tworzenia właściwości ustaw C++ w programie Visual Studio](../working-with-project-properties.md).

1. Kliknij przycisk **C/C++** folderu.

1. Kliknij przycisk **zaawansowane** stronę właściwości.

1. Modyfikowanie **Usuń definicje preprocesora** lub **Usuń wszystkie definicje preprocesora** właściwości.

### <a name="to-set-this-compiler-option-programmatically"></a>Aby programowo ustawić tę opcję kompilatora

- Zobacz <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.UndefineAllPreprocessorDefinitions%2A> lub <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.UndefinePreprocessorDefinitions%2A>.

## <a name="see-also"></a>Zobacz także

[MSVC Compiler Options](compiler-options.md)<br/>
[Składnia wiersza polecenia kompilatora MSVC](compiler-command-line-syntax.md)<br/>
[/J (Domyślny typ char nie jest podpisany)](j-default-char-type-is-unsigned.md)<br/>
[/GR (Włącz informacje typu Run/Time)](gr-enable-run-time-type-information.md)<br/>
[/EH (Model obsługi wyjątku)](eh-exception-handling-model.md)<br/>
[/MD, /MT, /LD (Korzystaj z bibliotek wykonawczych)](md-mt-ld-use-run-time-library.md)
