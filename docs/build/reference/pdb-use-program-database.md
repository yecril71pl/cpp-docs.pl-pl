---
title: -PDB (Użyj bazy danych programu) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- /pdb
- VC.Project.VCLinkerTool.ProgramDatabaseFile
dev_langs:
- C++
helpviewer_keywords:
- -PDB linker option
- /PDB linker option
- PDB linker option
- PDB files, creating
- .pdb files, creating
ms.assetid: d23db0ce-10cb-427a-bc60-d6b2a852723d
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 776d23c0c0c7ce392b1ff0d7a989c3c5503129b8
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
---
# <a name="pdb-use-program-database"></a>/PDB (Korzystaj z bazy danych programu)
```  
/PDB:filename  
```  
  
## <a name="remarks"></a>Uwagi  
 gdzie:  
  
 *Nazwa pliku*  
 Określone przez użytkownika nazwa bazy danych programu (PDB) tworzonego przez konsolidatora. Zastępuje ona nazwę domyślną.  
  
## <a name="remarks"></a>Uwagi  
 Domyślnie gdy [/DEBUG](../../build/reference/debug-generate-debug-info.md) jest określona, konsolidator tworzy bazę danych programu (PDB) zawierający informacje o debugowaniu. Domyślna nazwa pliku PDB ma podstawowej nazwy programu i rozszerzenia .pdb.  
  
 Użyj/PDB:*filename* do określenia nazwy pliku PDB. Jeśli nie określono opcji/debug, opcja/PDB jest ignorowana.  
  
 Może to być plik PDB maksymalnie 2GB.  
  
 Aby uzyskać więcej informacji, zobacz [.pdb, pliki jako dane wejściowe konsolidatora](../../build/reference/dot-pdb-files-as-linker-input.md).  
  
### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Aby ustawić tę opcję konsolidatora w środowisku programowania Visual Studio  
  
1.  Otwórz projekt **strony właściwości** okno dialogowe. Aby uzyskać więcej informacji, zobacz [Ustawianie właściwości projektu Visual C++](../../ide/working-with-project-properties.md).  
  
2.  Kliknij przycisk **konsolidatora** folderu.  
  
3.  Kliknij przycisk **debugowania** strony właściwości.  
  
4.  Modyfikowanie **Generuj plik bazy danych programu** właściwości.  
  
### <a name="to-set-this-linker-option-programmatically"></a>Aby programowo ustawić tę opcję konsolidatora  
  
-   Zobacz <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.ProgramDatabaseFile%2A>.  
  
## <a name="see-also"></a>Zobacz też  
 [Ustawianie opcji konsolidatora](../../build/reference/setting-linker-options.md)   
 [Opcje konsolidatora](../../build/reference/linker-options.md)