---
title: "-PDBSTRIPPED (Usuń symbole prywatne) | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- /pdbstripped
- VC.Project.VCLinkerTool.StripPrivateSymbols
dev_langs: C++
helpviewer_keywords:
- /PDBSTRIPPED linker option
- -PDBSTRIPPED linker option
- .pdb files, stripping private symbols
- PDB files, stripping private symbols
- PDBSTRIPPED linker option
ms.assetid: 9b9e0070-6a13-4142-8180-19c003fbbd55
caps.latest.revision: "8"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 73288ef6bf6881d946e4ec4bdd94e9b85cc0e81a
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="pdbstripped-strip-private-symbols"></a>/PDBSTRIPPED (Usuń symbole prywatne)
```  
/PDBSTRIPPED:pdb_file_name  
```  
  
## <a name="remarks"></a>Uwagi  
 gdzie:  
  
 *pdb_file_name*  
 Określone przez użytkownika nazwa pozbawionego włókien bazę danych programu (PDB) tworzonego przez konsolidatora.  
  
## <a name="remarks"></a>Uwagi  
 Opcja/pdbstripped tworzy drugi plik bazy danych (PDB) programu podczas tworzenia Twojej obraz programu przy użyciu opcji kompilatora lub konsolidatora opcje, które generują plik PDB ([/DEBUG](../../build/reference/debug-generate-debug-info.md), [/z7](../../build/reference/z7-zi-zi-debug-information-format.md), /Zd lub /Zi). Ten drugi plik PDB pomija symbole, których nie należy wysłać do klientów. Drugi plik PDB będzie zawierać tylko:  
  
-   Symbole publiczne  
  
-   Lista plików obiektów oraz części pliku wykonywalnego, do którego przyczyniają się  
  
-   Ramki wskaźnika optymalizacji (FPO) używane do przechodzenia w stosie debugowania rekordów  
  
 Pozbawionego włókien plik PDB nie zawiera:  
  
-   Informacje o typie  
  
-   Informacje o numerach wierszy  
  
-   Symbole CodeView pliku dla obiektów, takich jak funkcje, zmienne lokalne i dane statyczne  
  
 Pełny plik PDB będzie nadal generowane, gdy używasz/pdbstripped.  
  
 Jeśli nie utworzysz plik PDB, / pdbstripped zostanie zignorowany.  
  
### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Aby ustawić tę opcję konsolidatora w środowisku programowania Visual Studio  
  
1.  Otwórz projekt **strony właściwości** okno dialogowe. Aby uzyskać więcej informacji, zobacz [Ustawianie właściwości projektu Visual C++](../../ide/working-with-project-properties.md).  
  
2.  Kliknij przycisk **konsolidatora** folderu.  
  
3.  Kliknij przycisk **debugowania** strony właściwości.  
  
4.  Modyfikowanie **Usuń symbole prywatne** właściwości.  
  
### <a name="to-set-this-linker-option-programmatically"></a>Aby programowo ustawić tę opcję konsolidatora  
  
-   Zobacz <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.StripPrivateSymbols%2A>.  
  
## <a name="see-also"></a>Zobacz też  
 [Ustawianie opcji konsolidatora](../../build/reference/setting-linker-options.md)   
 [Opcje konsolidatora](../../build/reference/linker-options.md)