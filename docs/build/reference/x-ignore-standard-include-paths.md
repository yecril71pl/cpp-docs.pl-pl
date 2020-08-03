---
title: /X (Ignoruj standardowe ścieżki dołączanych plików)
ms.date: 07/31/2020
f1_keywords:
- /x
- VC.Project.VCCLCompilerTool.OVERWRITEStandardIncludePath
- VC.Project.VCCLWCECompilerTool.OVERWRITEStandardIncludePath
- VC.Project.VCCLCompilerTool.IgnoreStandardIncludePath
helpviewer_keywords:
- /X compiler option [C++]
- include files, ignore standard path
- -X compiler option [C++]
- include directories, ignore standard
- X compiler option
- Ignore Standard Include Paths compiler option
ms.assetid: 16bdf2cc-c8dc-46e4-bdcc-f3caeba5e1ef
ms.openlocfilehash: 652feeb200b7106aaca1ed7264f1e25c088a3dab
ms.sourcegitcommit: f2a135d69a2a8ef1777da60c53d58fe06980c997
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/03/2020
ms.locfileid: "87520411"
---
# <a name="x-ignore-standard-include-paths"></a>`/X`(Ignoruj standardowe ścieżki dołączane)

Uniemożliwia kompilatorowi wyszukiwanie plików dołączanych w katalogach określonych w ścieżce i zawiera zmienne środowiskowe.

## <a name="syntax"></a>Składnia

> **`/X`**

## <a name="remarks"></a>Uwagi

Możesz użyć tej opcji z opcją [ `/I` (Dodatkowe katalogi dołączane)](i-additional-include-directories.md) , aby określić alternatywną ścieżkę do standardowych plików dołączanych.

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Aby ustawić tę opcję kompilatora w środowisku programowania Visual Studio

1. Otwórz okno dialogowe **strony właściwości** projektu. Aby uzyskać szczegółowe informacje, zobacz [Ustawianie kompilatora C++ i właściwości kompilacji w programie Visual Studio](../working-with-project-properties.md).

1. Wybierz **Configuration Properties**  >  stronę właściwości konfiguracji preprocesora**C/C++**  >  **Preprocessor** .

1. Zmodyfikuj właściwość **Ignorowanie standardowej ścieżki dołączania** .

### <a name="to-set-this-compiler-option-programmatically"></a>Aby programowo ustawić tę opcję kompilatora

- Zobacz: <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.IgnoreStandardIncludePath%2A>.

## <a name="example"></a>Przykład

W poniższym poleceniu **`/X`** nakazuje kompilatorowi ignorowanie lokalizacji określonych przez ścieżkę i uwzględnianie zmiennych środowiskowych, a **`/I`** także określa katalog, w którym mają być wyszukiwane pliki dołączane:

```cmd
CL /X /I \ALT\INCLUDE MAIN.C
```

## <a name="see-also"></a>Zobacz także

[Opcje kompilatora MSVC](compiler-options.md)<br/>
[Składnia wiersza polecenia kompilatora MSVC](compiler-command-line-syntax.md)
