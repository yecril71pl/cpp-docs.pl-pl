---
title: -FR, -Fr (Utwórz. Plik SBR) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- VC.Project.VCCLWCECompilerTool.BrowseInformation
- VC.Project.VCCLCompilerTool.BrowseInformation
- /fr
- VC.Project.VCCLCompilerTool.BrowseInformationFile
- VC.Project.VCCLWCECompilerTool.BrowseInformationFile
dev_langs:
- C++
helpviewer_keywords:
- /FR compiler option [C++]
- -FR compiler option [C++]
- FR compiler option [C++]
- symbolic browser information
ms.assetid: 3fd8f88b-3924-4feb-9393-287036a28896
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: a5691a87f7350c7816e8ddb58d5591e16cc18189
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/17/2018
ms.locfileid: "45709614"
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

**/FR** jest przestarzały; użyj **/FR** zamiast tego. Aby uzyskać więcej informacji, zobacz uznane za przestarzałe i usunąć — opcje kompilatora w [opcje kompilatora wymienione według kategorii](../../build/reference/compiler-options-listed-by-category.md).

> [!NOTE]
>  Nie zmieniaj rozszerzenia .sbr. BSCMAKE wymaga pośrednie pliki, aby mieć tego rozszerzenia.

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Aby ustawić tę opcję kompilatora w środowisku programowania Visual Studio

1. Otwórz projekt **stron właściwości** okno dialogowe. Aby uzyskać więcej informacji, zobacz [Praca z właściwościami projektu](../../ide/working-with-project-properties.md).

1. W okienku nawigacji wybierz **C/C++**, **informacji o przeglądaniu** stronę właściwości.

1. Modyfikowanie **Przeglądaj pliku z informacjami o** lub **Włącz informacji o przeglądaniu** właściwości.

### <a name="to-set-this-compiler-option-programmatically"></a>Aby programowo ustawić tę opcję kompilatora

- Zobacz <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.BrowseInformation%2A> i <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.BrowseInformationFile%2A>.

## <a name="see-also"></a>Zobacz też

[Plik wyjściowy (/ F) opcje](../../build/reference/output-file-f-options.md)
[opcje kompilatora](../../build/reference/compiler-options.md)<br/>
[Ustawianie opcji kompilatora](../../build/reference/setting-compiler-options.md)<br/>
[Określanie nazwy ścieżki](../../build/reference/specifying-the-pathname.md)