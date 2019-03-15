---
title: /FR, /Fr (Utwórz plik .Sbr)
ms.date: 11/04/2016
f1_keywords:
- VC.Project.VCCLWCECompilerTool.BrowseInformation
- VC.Project.VCCLCompilerTool.BrowseInformation
- /fr
- VC.Project.VCCLCompilerTool.BrowseInformationFile
- VC.Project.VCCLWCECompilerTool.BrowseInformationFile
helpviewer_keywords:
- /FR compiler option [C++]
- -FR compiler option [C++]
- FR compiler option [C++]
- symbolic browser information
ms.assetid: 3fd8f88b-3924-4feb-9393-287036a28896
ms.openlocfilehash: a75a9d143012dee7946591d708921d6734b2acda
ms.sourcegitcommit: 8105b7003b89b73b4359644ff4281e1595352dda
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2019
ms.locfileid: "57811878"
---
# <a name="fr-fr-create-sbr-file"></a>/FR, /Fr (Utwórz plik .Sbr)

Tworzy pliki .sbr.

## <a name="syntax"></a>Składnia

```
/FR[pathname[\filename]]
/Fr[pathname[\filename]]
```

## <a name="remarks"></a>Uwagi

Podczas procesu kompilacji Microsoft Przeglądaj informacje o pliku konserwacji Utility (BSCMAKE) używa do tworzenia tych plików. Plik BSC służy do wyświetlania informacji o przeglądaniu.

**/FR** tworzy plik SBR z pełne symboliczne informacje.

**/FR** tworzy plik .sbr bez informacji o zmiennych lokalnych.

Jeśli nie określisz `filename`, plik .sbr pobiera tej samej nazwie podstawowej co plik źródłowy.

**/FR** jest przestarzały; użyj **/FR** zamiast tego. Aby uzyskać więcej informacji, zobacz uznane za przestarzałe i usunąć — opcje kompilatora w [opcje kompilatora wymienione według kategorii](compiler-options-listed-by-category.md).

> [!NOTE]
>  Nie zmieniaj rozszerzenia .sbr. BSCMAKE wymaga pośrednie pliki, aby mieć tego rozszerzenia.

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Aby ustawić tę opcję kompilatora w środowisku programowania Visual Studio

1. Otwórz projekt **stron właściwości** okno dialogowe. Aby uzyskać więcej informacji, zobacz [kompilatora i tworzenia właściwości ustaw C++ w programie Visual Studio](../working-with-project-properties.md).

1. W okienku nawigacji wybierz **C/C++**, **informacji o przeglądaniu** stronę właściwości.

1. Modyfikowanie **Przeglądaj pliku z informacjami o** lub **Włącz informacji o przeglądaniu** właściwości.

### <a name="to-set-this-compiler-option-programmatically"></a>Aby programowo ustawić tę opcję kompilatora

- Zobacz <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.BrowseInformation%2A> i <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.BrowseInformationFile%2A>.

## <a name="see-also"></a>Zobacz także

[Plik wyjściowy (/F), opcje](output-file-f-options.md)<br/>
[MSVC Compiler Options](compiler-options.md)<br/>
[Składnia wiersza polecenia kompilatora MSVC](compiler-command-line-syntax.md)<br/>
[Określanie nazwy ścieżki](specifying-the-pathname.md)
