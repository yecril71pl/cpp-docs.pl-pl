---
title: "-OUT (nazwa pliku wyjściowego) | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- VC.Project.VCLinkerTool.OutputFile
- /out
dev_langs:
- C++
helpviewer_keywords:
- output files, name linker option
- -OUT linker option
- OUT linker option
- /OUT C++ linker option
- linker [C++], output files
ms.assetid: 976210a4-e51f-4cfb-af5e-c16344455834
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 2a548e21e6bb485a326a2a9e34c6f47d968bbb6f
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="out-output-file-name"></a>/OUT (Nazwa pliku wyjściowego)
```  
/OUT:filename  
```  
  
## <a name="remarks"></a>Uwagi  
 gdzie:  
  
 *Nazwa pliku*  
 Określone przez użytkownika nazwa pliku wyjściowego. Zastępuje ona nazwę domyślną.  
  
## <a name="remarks"></a>Uwagi  
 Opcja/out przesłania domyślną nazwę i lokalizację programu tworzonego przez konsolidatora.  
  
 Domyślnie konsolidator tworzy nazwę pliku przy użyciu nazwy podstawowej pierwszy określonego pliku .obj i odpowiednie rozszerzenie (.exe lub .dll).  
  
 Tę opcję domyślną nazwę podstawową dla biblioteki .mapfile lub importu. Aby uzyskać więcej informacji, zobacz [Generowanie Mapfile](../../build/reference/map-generate-mapfile.md) (/ MAP) i [/IMPLIB](../../build/reference/implib-name-import-library.md).  
  
### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Aby ustawić tę opcję konsolidatora w środowisku programowania Visual Studio  
  
1.  Otwórz projekt **strony właściwości** okno dialogowe. Aby uzyskać więcej informacji, zobacz [Ustawianie właściwości projektu Visual C++](../../ide/working-with-project-properties.md).  
  
2.  Kliknij przycisk **konsolidatora** folderu.  
  
3.  Kliknij przycisk **ogólne** strony właściwości.  
  
4.  Modyfikowanie **pliku wyjściowego** właściwości.  
  
### <a name="to-set-this-linker-option-programmatically"></a>Aby programowo ustawić tę opcję konsolidatora  
  
-   Zobacz <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.OutputFile%2A>.  
  
## <a name="see-also"></a>Zobacz też  
 [Ustawianie opcji konsolidatora](../../build/reference/setting-linker-options.md)   
 [Opcje konsolidatora](../../build/reference/linker-options.md)