---
title: -FR, -Fr (Tworzenie. Plik SBR) | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- VC.Project.VCCLWCECompilerTool.BrowseInformation
- VC.Project.VCCLCompilerTool.BrowseInformation
- /fr
- VC.Project.VCCLCompilerTool.BrowseInformationFile
- VC.Project.VCCLWCECompilerTool.BrowseInformationFile
dev_langs: C++
helpviewer_keywords:
- /FR compiler option [C++]
- -FR compiler option [C++]
- FR compiler option [C++]
- symbolic browser information
ms.assetid: 3fd8f88b-3924-4feb-9393-287036a28896
caps.latest.revision: "18"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 911ab24407f74391186568df58f5111253c41cae
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
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