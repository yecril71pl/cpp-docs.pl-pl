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
ms.openlocfilehash: 58f55811f5d2bb81bc77da38a87c35bae91ce6cb
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81320520"
---
# <a name="fr-fr-create-sbr-file"></a>/FR, /Fr (Utwórz plik .Sbr)

Tworzy pliki .sbr.

## <a name="syntax"></a>Składnia

```
/FR[pathname[\filename]]
/Fr[pathname[\filename]]
```

## <a name="remarks"></a>Uwagi

> [!WARNING]
> Mimo że BSCMAKE jest nadal zainstalowany w programie Visual Studio, nie jest już używany przez IDE. Od programu Visual Studio 2008 informacje o przeglądaniu i symbolach są automatycznie przechowywane w pliku sdf programu SQL Server w folderze rozwiązania.

Podczas procesu kompilacji narzędzie microsoft browse information file maintenance utility (BSCMAKE) używa tych plików do utworzenia pliku . BSC, który służy do wyświetlania informacji przeglądania.

**/FR** tworzy plik .sbr z pełnymi informacjami symbolicznymi.

**/Fr** tworzy plik .sbr bez informacji o zmiennych lokalnych.

Jeśli nie określisz, `filename`plik .sbr otrzyma taką samą nazwę podstawową jak plik źródłowy.

**/Fr** jest przestarzały; zamiast tego użyj **/FR.** Aby uzyskać więcej informacji, zobacz Przestarzałe i usunięte opcje kompilatora w [opcjach kompilatora wymienionych według kategorii](compiler-options-listed-by-category.md).

> [!NOTE]
> Nie należy zmieniać rozszerzenia .sbr. BSCMAKE wymaga, aby pliki pośredniczące miały to rozszerzenie.

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Aby ustawić tę opcję kompilatora w środowisku programowania Visual Studio

1. Otwórz okno dialogowe **Strony właściwości** projektu. Aby uzyskać szczegółowe informacje, zobacz [Ustawianie kompilatora języka C++ i właściwości kompilacji w programie Visual Studio.](../working-with-project-properties.md)

1. W okienku nawigacji wybierz stronę właściwości **C/C++**, **Przeglądaj informacje.**

1. Zmodyfikuj **plik informacji przeglądania** lub włącz funkcję **Przeglądaj informacje.**

### <a name="to-set-this-compiler-option-programmatically"></a>Aby programowo ustawić tę opcję kompilatora

- Zobacz <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.BrowseInformation%2A> <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.BrowseInformationFile%2A>i .

## <a name="see-also"></a>Zobacz też

[Plik wyjściowy (/F), opcje](output-file-f-options.md)<br/>
[Opcje kompilatora MSVC](compiler-options.md)<br/>
[Składnia wiersza polecenia kompilatora MSVC](compiler-command-line-syntax.md)<br/>
[Określanie nazwy ścieżki](specifying-the-pathname.md)
