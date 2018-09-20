---
title: -U, -u (Usuń definicje symboli) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- VC.Project.VCCLCompilerTool.UndefinePreprocessorDefinitions
- VC.Project.VCCLWCECompilerTool.UndefinePreprocessorDefinitions
- VC.Project.VCCLCompilerTool.UndefineAllPreprocessorDefinitions
- /u
- VC.Project.VCCLWCECompilerTool.UndefineAllPreprocessorDefinitions
dev_langs:
- C++
helpviewer_keywords:
- -U compiler option [C++]
- Undefine Symbols compiler option
- /U compiler option [C++]
- U compiler option [C++]
ms.assetid: 7bc0474f-6d1f-419b-807d-0d8816763b2a
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: a32106dd9802643a827f8a3e97298f389d31d3b4
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/19/2018
ms.locfileid: "46430673"
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
|_CHAR_UNSIGNED|Domyślny typ char nie został podpisany. Zdefiniowane kiedy [/j.](../../build/reference/j-default-char-type-is-unsigned.md) określono opcję.|
|_CPPRTTI|Zdefiniowane dla kodu skompilowanego za pomocą [GR](../../build/reference/gr-enable-run-time-type-information.md) opcji.|
|_CPPUNWIND|Zdefiniowane dla kodu skompilowanego za pomocą [/ehsc](../../build/reference/eh-exception-handling-model.md) opcji.|
|_DLL|Zdefiniowane kiedy [/MD](../../build/reference/md-mt-ld-use-run-time-library.md) określono opcję.|
|_M_IX86|Domyślnie, określony do 600 dla x86 elementów docelowych.|
|_MSC_VER|Aby uzyskać więcej informacji, zobacz [wstępnie zdefiniowane makra](../../preprocessor/predefined-macros.md).|
|_WIN32|Zdefiniowane dla aplikacji WIN32. Zawsze jest zdefiniowana.|
|_MT|Zdefiniowane kiedy [/MD lub/MT](../../build/reference/md-mt-ld-use-run-time-library.md) określono opcję.|

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Aby ustawić tę opcję kompilatora w środowisku programowania Visual Studio

1. Otwórz projekt **stron właściwości** okno dialogowe. Aby uzyskać więcej informacji, zobacz [Praca z właściwościami projektu](../../ide/working-with-project-properties.md).

1. Kliknij przycisk **C/C++** folderu.

1. Kliknij przycisk **zaawansowane** stronę właściwości.

1. Modyfikowanie **Usuń definicje preprocesora** lub **Usuń wszystkie definicje preprocesora** właściwości.

### <a name="to-set-this-compiler-option-programmatically"></a>Aby programowo ustawić tę opcję kompilatora

- Zobacz <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.UndefineAllPreprocessorDefinitions%2A> lub <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.UndefinePreprocessorDefinitions%2A>.

## <a name="see-also"></a>Zobacz też

[Opcje kompilatora](../../build/reference/compiler-options.md)<br/>
[Ustawianie opcji kompilatora](../../build/reference/setting-compiler-options.md)<br/>
[/J (Domyślny typ char nie jest podpisany)](../../build/reference/j-default-char-type-is-unsigned.md)<br/>
[/GR (Włącz informacje typu Run/Time)](../../build/reference/gr-enable-run-time-type-information.md)<br/>
[/EH (Model obsługi wyjątku)](../../build/reference/eh-exception-handling-model.md)<br/>
[/MD, /MT, /LD (Korzystaj z bibliotek wykonawczych)](../../build/reference/md-mt-ld-use-run-time-library.md)