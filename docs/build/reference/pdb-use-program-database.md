---
title: "-PDB (Użyj bazy danych programu) | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- /pdb
- VC.Project.VCLinkerTool.ProgramDatabaseFile
dev_langs: C++
helpviewer_keywords:
- -PDB linker option
- /PDB linker option
- PDB linker option
- PDB files, creating
- .pdb files, creating
ms.assetid: d23db0ce-10cb-427a-bc60-d6b2a852723d
caps.latest.revision: "8"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 0ea27dd7106e8490e9ba8ec9eacdcbbb02d33036
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
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