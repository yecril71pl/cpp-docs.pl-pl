---
title: /X (Ignoruj standardowe ścieżki dołączanych plików)
ms.date: 11/04/2016
f1_keywords:
- /x
- VC.Project.VCCLCompilerTool.OVERWRITEStandardIncludePath
- VC.Project.VCCLWCECompilerTool.OVERWRITEStandardIncludePath
helpviewer_keywords:
- /X compiler option [C++]
- include files, ignore standard path
- -X compiler option [C++]
- include directories, ignore standard
- X compiler option
- Ignore Standard Include Paths compiler option
ms.assetid: 16bdf2cc-c8dc-46e4-bdcc-f3caeba5e1ef
ms.openlocfilehash: dba7e49880307002a3dee983264e93666adfef17
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62316317"
---
# <a name="x-ignore-standard-include-paths"></a>/X (Ignoruj standardowe ścieżki dołączanych plików)

Zabezpiecza kompilator przed wyszukiwaniem dołączonych plików w katalogach określonych w zmiennych środowiskowych PATH lub INCLUDE.

## <a name="syntax"></a>Składnia

```
/X
```

## <a name="remarks"></a>Uwagi

Można użyć tej opcji z [/I (dodatkowe katalogi dołączenia)](i-additional-include-directories.md) (**/I**`directory`) opcji.

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Aby ustawić tę opcję kompilatora w środowisku programowania Visual Studio

1. Otwórz projekt **stron właściwości** okno dialogowe. Aby uzyskać więcej informacji, zobacz [kompilatora i tworzenia właściwości ustaw C++ w programie Visual Studio](../working-with-project-properties.md).

1. Kliknij przycisk **C/C++** folderu.

1. Kliknij przycisk **preprocesora** stronę właściwości.

1. Modyfikowanie **Ignoruj standardową ścieżkę obejmują** właściwości.

### <a name="to-set-this-compiler-option-programmatically"></a>Aby programowo ustawić tę opcję kompilatora

- Zobacz <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.IgnoreStandardIncludePath%2A>.

## <a name="example"></a>Przykład

W poniższym poleceniu `/X` informuje kompilator, aby zignorować lokalizacjach, określonych przez zmienne środowiskowe PATH lub INCLUDE i `/I` Określa katalog, w którym znajdują się pliki dołączane:

```
CL /X /I \ALT\INCLUDE MAIN.C
```

## <a name="see-also"></a>Zobacz także

[Opcje kompilatora MSVC](compiler-options.md)<br/>
[Składnia wiersza polecenia kompilatora MSVC](compiler-command-line-syntax.md)
