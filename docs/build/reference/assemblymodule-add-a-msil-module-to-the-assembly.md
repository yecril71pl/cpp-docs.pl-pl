---
title: "-ASSEMBLYMODULE (Dodaj moduł MSIL do zestawu) | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- /assemblymodule
- VC.Project.VCLinkerTool.AddModuleNamesToAssembly
dev_langs:
- C++
helpviewer_keywords:
- ASSEMBLYMODULE linker option
- assemblies [C++], adding modules to
- assemblies [C++]
- /ASSEMBLYMODULE linker option
- -ASSEMBLYMODULE linker option
ms.assetid: 67357da8-e4b6-49fd-932c-329a5777f143
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: efe45bd6a3225f50e1f842c6d247aae9626302a3
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="assemblymodule-add-a-msil-module-to-the-assembly"></a>/ASSEMBLYMODULE (Dodaj moduł MSIL do zestawu)
```  
/ASSEMBLYMODULE:filename  
```  
  
## <a name="remarks"></a>Uwagi  
 gdzie:  
  
 *Nazwa pliku*  
 Moduł, który chcesz uwzględnić w tym zestawie.  
  
## <a name="remarks"></a>Uwagi  
 Opcja/assemblymodule pozwala dodać odwołania modułu do zestawu. Informacje o typie w module nie będzie dostępne dla programu zestawu, który został dodany odwołania do modułu. Jednak informacje o typie w module będzie dostępny dla dowolnego programu, który odwołuje się do zestawu.  
  
 Użyj [#using](../../preprocessor/hash-using-directive-cpp.md) do dodania odwołania modułu do zestawu i udostępnia informacje o typie modułu dla programu zestawu.  
  
 Na przykład rozważmy następujący scenariusz:  
  
1.  Utwórz moduł z [/LN](../../build/reference/ln-create-msil-module.md).  
  
2.  Użyj/assemblymodule z innego projektu, aby uwzględnić modułu w bieżącej kompilacji, co spowoduje utworzenie zestawu. Ten projekt nie zostanie wprowadzone odniesienie moduł `#using`.  
  
3.  Teraz żadnego projektu, który odwołuje się do tego zestawu można również użyć typów z modułu.  
  
 Inne opcje konsolidatora, które mają wpływ na generowanie zestawów są:  
  
-   [/ ASSEMBLYDEBUG](../../build/reference/assemblydebug-add-debuggableattribute.md)  
  
-   [/ ASSEMBLYLINKRESOURCE](../../build/reference/assemblylinkresource-link-to-dotnet-framework-resource.md)  
  
-   [/ ASSEMBLYRESOURCE](../../build/reference/assemblyresource-embed-a-managed-resource.md)  
  
-   [/ DELAYSIGN](../../build/reference/delaysign-partially-sign-an-assembly.md)  
  
-   [/ NOASSEMBLY](../../build/reference/noassembly-create-a-msil-module.md)  
  
-   [/ KEYFILE](../../build/reference/keyfile-specify-key-or-key-pair-to-sign-an-assembly.md)  
  
-   [/ KEYCONTAINER.](../../build/reference/keycontainer-specify-a-key-container-to-sign-an-assembly.md)  
  
 Konsolidatora Visual C++ akceptuje modułu .netmodule pliki jako dane wejściowe i będzie utworzony przez konsolidator plik wyjściowy zestawu lub moduł .netmodule z ma zależności środowiska wykonawczego na żadnym z modułów .netmodule, że dane wejściowe do konsolidatora.  Aby uzyskać więcej informacji, zobacz [modułu .netmodule pliki jako dane wejściowe konsolidatora](../../build/reference/netmodule-files-as-linker-input.md).  
  
### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Aby ustawić tę opcję konsolidatora w środowisku programowania Visual Studio  
  
1.  Otwórz projekt **strony właściwości** okno dialogowe. Aby uzyskać więcej informacji, zobacz [Ustawianie właściwości projektu Visual C++](../../ide/working-with-project-properties.md).  
  
2.  Kliknij przycisk **konsolidatora** folderu.  
  
3.  Kliknij przycisk **dane wejściowe** strony właściwości.  
  
4.  Modyfikowanie **Dodaj moduł do zestawu** właściwości.  
  
### <a name="to-set-this-linker-option-programmatically"></a>Aby programowo ustawić tę opcję konsolidatora  
  
-   Zobacz <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.AddModuleNamesToAssembly%2A>.  
  
## <a name="see-also"></a>Zobacz też  
 [Ustawianie opcji konsolidatora](../../build/reference/setting-linker-options.md)   
 [Opcje konsolidatora](../../build/reference/linker-options.md)