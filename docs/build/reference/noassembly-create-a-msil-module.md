---
title: "-NOASSEMBLY (Utwórz moduł MSIL) | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- /NOASSEMBLY
- VC.Project.VCLinkerTool.TurnOffAssemblyGeneration
dev_langs: C++
helpviewer_keywords:
- assemblies [C++]
- -NOASSEMBLY linker option
- /NOASSEMBLY linker option
- NOASSEMBLY linker option
- assemblies [C++], not creating an assembly
ms.assetid: 3cea4e70-f451-4395-a626-1930b1b127fe
caps.latest.revision: "11"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: a8bbb816ebedcb82b198a70532fdacb80b74bf8a
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="noassembly-create-a-msil-module"></a>/NOASSEMBLY (Utwórz moduł MSIL)
```  
/NOASSEMBLY  
```  
  
## <a name="remarks"></a>Uwagi  
 Opcja/noassembly informuje konsolidator, aby utworzyć obraz dla bieżącego pliku wyjściowego bez zestawu .NET Framework. Plik wyjściowy MSIL bez manifest zestawu nosi nazwę modułu.  
  
 Domyślnie jest tworzony zestawu. Można również użyć [/LN (Utwórz moduł MSIL)](../../build/reference/ln-create-msil-module.md) opcję kompilatora, aby utworzyć moduł.  
  
 Inne opcje konsolidatora, które mają wpływ na generowanie zestawów są:  
  
-   [/ ASSEMBLYDEBUG](../../build/reference/assemblydebug-add-debuggableattribute.md)  
  
-   [/ ASSEMBLYLINKRESOURCE](../../build/reference/assemblylinkresource-link-to-dotnet-framework-resource.md)  
  
-   [/ ASSEMBLYMODULE](../../build/reference/assemblymodule-add-a-msil-module-to-the-assembly.md)  
  
-   [/ ASSEMBLYRESOURCE](../../build/reference/assemblyresource-embed-a-managed-resource.md)  
  
-   [/ DELAYSIGN](../../build/reference/delaysign-partially-sign-an-assembly.md)  
  
-   [/ KEYFILE](../../build/reference/keyfile-specify-key-or-key-pair-to-sign-an-assembly.md)  
  
-   [/ KEYCONTAINER.](../../build/reference/keycontainer-specify-a-key-container-to-sign-an-assembly.md)  
  
### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Aby ustawić tę opcję konsolidatora w środowisku programowania Visual Studio  
  
1.  Otwórz projekt **strony właściwości** okno dialogowe. Aby uzyskać więcej informacji, zobacz [Ustawianie właściwości projektu Visual C++](../../ide/working-with-project-properties.md).  
  
2.  Kliknij przycisk **konsolidatora** folderu.  
  
3.  Kliknij przycisk **zaawansowane** strony właściwości.  
  
4.  Modyfikowanie **włączyć wyłącz generowanie zestawów** właściwości.  
  
### <a name="to-set-this-linker-option-programmatically"></a>Aby programowo ustawić tę opcję konsolidatora  
  
-   Zobacz <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.TurnOffAssemblyGeneration%2A>.  
  
## <a name="see-also"></a>Zobacz też  
 [Ustawianie opcji konsolidatora](../../build/reference/setting-linker-options.md)   
 [Opcje konsolidatora](../../build/reference/linker-options.md)