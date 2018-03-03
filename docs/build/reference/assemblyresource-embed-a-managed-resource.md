---
title: "-ASSEMBLYRESOURCE (Osadź zarządzany zasób) | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- VC.Project.VCLinkerTool.EmbedManagedResourceFile
- /ASSEMBLYRESOURCE
dev_langs:
- C++
helpviewer_keywords:
- ASSEMBLYRESOURCE linker option
- assemblies [C++]
- -ASSEMBLYRESOURCE linker option
- assemblies [C++], linking resource files
- /ASSEMBLYRESOURCE linker option
ms.assetid: 0ce6e1fb-921b-4b1b-a59c-d35388d789f2
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: ed8fd2b127a828eb8279671817cc4f099ae528c6
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="assemblyresource-embed-a-managed-resource"></a>/ASSEMBLYRESOURCE (Osadź zarządzany zasób)
```  
/ASSEMBLYRESOURCE:filename[,[name][,PRIVATE]]  
```  
  
## <a name="parameters"></a>Parametry  
 *Nazwa pliku*  
 Zarządzany zasób, do którego ma zostać osadzony w tym zestawie.  
  
 *Nazwa*  
 Opcjonalny. Nazwa logiczna zasobu; Nazwa używana do załadowania zasobu. Wartość domyślna to nazwa pliku.  
  
 Opcjonalnie można określić, czy ten plik powinien być prywatna w manifeście zestawu. Domyślnie *nazwa* jest publiczny w zestawie.  
  
## <a name="remarks"></a>Uwagi  
 Opcja/assemblyresource do osadzenia zasobu w zestawie.  
  
 Zasoby są publicznie udostępniane w zestawie, gdy utworzone za pomocą konsolidator. Konsolidator nie pozwalają na zmiany nazwy zasobu w zestawie.  
  
 Jeśli *filename* jest utworzony, na przykład w pliku zasobu (.resources) .NET Framework [Generator pliku zasobów (Resgen.exe)](/dotnet/framework/tools/resgen-exe-resource-file-generator) lub w środowisku programistycznym, jest dostępny z elementami członkowskimi w **System.Resources** przestrzeni nazw (zobacz [System.Resources.ResourceManager](https://msdn.microsoft.com/en-us/library/system.resources.resourcemanager.aspx) Aby uzyskać więcej informacji). Inne zasoby, można użyć **GetManifestResource** \* metod w **System.Reflection.Assembly** klasę, aby uzyskać dostęp do zasobu w czasie wykonywania.  
  
 Inne opcje konsolidatora, które mają wpływ na generowanie zestawów są:  
  
-   [/ ASSEMBLYDEBUG](../../build/reference/assemblydebug-add-debuggableattribute.md)  
  
-   [/ ASSEMBLYLINKRESOURCE](../../build/reference/assemblylinkresource-link-to-dotnet-framework-resource.md)  
  
-   [/ ASSEMBLYMODULE](../../build/reference/assemblymodule-add-a-msil-module-to-the-assembly.md)  
  
-   [/ DELAYSIGN](../../build/reference/delaysign-partially-sign-an-assembly.md)  
  
-   [/ KEYFILE](../../build/reference/keyfile-specify-key-or-key-pair-to-sign-an-assembly.md)  
  
-   [/ KEYCONTAINER.](../../build/reference/keycontainer-specify-a-key-container-to-sign-an-assembly.md)  
  
-   [/ NOASSEMBLY](../../build/reference/noassembly-create-a-msil-module.md)  
  
### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Aby ustawić tę opcję konsolidatora w środowisku programowania Visual Studio  
  
1.  Otwórz projekt **strony właściwości** okno dialogowe. Aby uzyskać więcej informacji, zobacz [Ustawianie właściwości projektu Visual C++](../../ide/working-with-project-properties.md).  
  
2.  Kliknij przycisk **konsolidatora** folderu.  
  
3.  Kliknij przycisk **dane wejściowe** strony właściwości.  
  
4.  Modyfikowanie **Osadź plik zasobu zarządzanego** właściwości.  
  
### <a name="to-set-this-linker-option-programmatically"></a>Aby programowo ustawić tę opcję konsolidatora  
  
1.  Zobacz <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.EmbedManagedResourceFile%2A>.  
  
## <a name="see-also"></a>Zobacz też  
 [Ustawianie opcji konsolidatora](../../build/reference/setting-linker-options.md)   
 [Opcje konsolidatora](../../build/reference/linker-options.md)