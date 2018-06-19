---
title: -FR, -Fr (Tworzenie. Plik SBR) | Dokumentacja firmy Microsoft
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
ms.openlocfilehash: e6f61a3360c820a2d47d54f7c174af484079d154
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
ms.locfileid: "32374768"
---
# <a name="fr-fr-create-sbr-file"></a>/FR, /Fr (Utwórz plik .Sbr)
Tworzy pliki .sbr.  
  
## <a name="syntax"></a>Składnia  
  
```  
/FR[pathname[\filename]]  
/Fr[pathname[\filename]]  
```  
  
## <a name="remarks"></a>Uwagi  
 Podczas procesu tworzenia Microsoft przeglądanie informacji o pliku konserwacji narzędzia (BSCMAKE) używa tych plików w celu utworzenia. Plik BSC, który służy do wyświetlania informacji dotyczących przeglądarki.  
  
 **/FR** tworzy plik .sbr z pełne symboliczne informacje.  
  
 **/FR** tworzy plik .sbr bez informacji o zmiennych lokalnych.  
  
 Jeśli nie określisz `filename`, plik .sbr pobiera taką samą nazwę podstawową jak plik źródłowy.  
  
 **/FR** jest przestarzały; użyj **/FR** zamiast tego. Aby uzyskać więcej informacji, zobacz uznane za przestarzałe i usunąć — opcje kompilatora w [kompilatora opcje rozbiciu na kategorie](../../build/reference/compiler-options-listed-by-category.md).  
  
> [!NOTE]
>  Nie należy zmieniać rozszerzenia .sbr. BSCMAKE wymaga pośredniczących plików mają rozszerzenia.  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Aby ustawić tę opcję kompilatora w środowisku programowania Visual Studio  
  
1.  Otwórz projekt **strony właściwości** okno dialogowe. Aby uzyskać więcej informacji, zobacz [Praca z właściwościami projektu](../../ide/working-with-project-properties.md).  
  
2.  W okienku nawigacji wybierz **C/C++**, **informacji o przeglądaniu** strony właściwości.  
  
3.  Modyfikowanie **Przeglądaj plik informacji o** lub **włączyć informacji o przeglądaniu** właściwości.  
  
### <a name="to-set-this-compiler-option-programmatically"></a>Aby programowo ustawić tę opcję kompilatora  
  
-   Zobacz <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.BrowseInformation%2A> i <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.BrowseInformationFile%2A>.  
  
## <a name="see-also"></a>Zobacz też  
 [Plik wyjściowy (/ F) opcje](../../build/reference/output-file-f-options.md)   
 [Opcje kompilatora](../../build/reference/compiler-options.md)   
 [Ustawianie opcji kompilatora](../../build/reference/setting-compiler-options.md)   
 [Określanie nazwy ścieżki](../../build/reference/specifying-the-pathname.md)