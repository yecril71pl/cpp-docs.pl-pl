---
title: /X (Ignoruj standardowe ścieżki dołączanych plików)
ms.date: 07/18/2019
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
ms.openlocfilehash: 16f903b98d69472fe1a33b084fe6393ecf9ec001
ms.sourcegitcommit: 0867d648e0955ebad7260b5fbebfd6cd4d58f3c7
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/19/2019
ms.locfileid: "68341052"
---
# <a name="x-ignore-standard-include-paths"></a>/X (Ignoruj standardowe ścieżki dołączanych plików)

Uniemożliwia kompilatorowi wyszukiwanie plików dołączanych w katalogach określonych w ścieżce i zawiera zmienne środowiskowe.

## <a name="syntax"></a>Składnia

```
/X
```

## <a name="remarks"></a>Uwagi

Tej opcji można użyć z opcją [/i (Dodatkowe katalogi dołączane)](i-additional-include-directories.md) ( **/i**`directory`).

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Aby ustawić tę opcję kompilatora w środowisku programowania Visual Studio

1. Otwórz okno dialogowe **strony właściwości** projektu. Aby uzyskać szczegółowe informacje, zobacz [ C++ Ustawianie właściwości kompilatora i Build w programie Visual Studio](../working-with-project-properties.md).

1. Kliknij folder **C/C++**  .

1. Kliknij stronę  właściwości preprocesora.

1. Zmodyfikuj właściwość **Ignorowanie standardowej ścieżki** dołączania.

### <a name="to-set-this-compiler-option-programmatically"></a>Aby programowo ustawić tę opcję kompilatora

- Zobacz <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.IgnoreStandardIncludePath%2A>.

## <a name="example"></a>Przykład

W poniższym poleceniu `/X` instruuje kompilator do ignorowania lokalizacji określonych przez ścieżkę i zawiera zmienne środowiskowe i `/I` określa katalog, w którym mają być wyszukiwane pliki dołączane:

```
CL /X /I \ALT\INCLUDE MAIN.C
```

## <a name="see-also"></a>Zobacz także

[Opcje kompilatora MSVC](compiler-options.md)<br/>
[Składnia wiersza polecenia kompilatora MSVC](compiler-command-line-syntax.md)
