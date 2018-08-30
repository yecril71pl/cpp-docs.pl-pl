---
title: -ASSEMBLYRESOURCE (Osadź zarządzany zasób) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
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
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: acb7b173ffd22e65e20dcc9cceef61b2e2131c83
ms.sourcegitcommit: 9a0905c03a73c904014ec9fd3d6e59e4fa7813cd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/29/2018
ms.locfileid: "43213404"
---
# <a name="assemblyresource-embed-a-managed-resource"></a>/ASSEMBLYRESOURCE (Osadź zarządzany zasób)
```  
/ASSEMBLYRESOURCE:filename[,[name][,PRIVATE]]  
```  
  
## <a name="parameters"></a>Parametry  
 *Nazwa pliku*  
 Zarządzanego zasobu, który ma zostać osadzony w tym zestawie.  
  
 *Nazwa*  
 Opcjonalna. Nazwa logiczna zasobu; Nazwa używana do ładowania zasobów. Wartość domyślna to nazwa pliku.  
  
 Opcjonalnie można określić, jeśli plik powinien znajdować się prywatne w manifeście zestawu. Domyślnie *nazwa* jest publiczna w zestawie.  
  
## <a name="remarks"></a>Uwagi  
 Opcja linkowany do osadzenia zasobu w zestawie.  
  
 Zasoby są publiczne w zestawie, gdy utworzone za pomocą konsolidatora. Konsolidator nie pozwalają na Zmień nazwę zasobu w zestawie.  
  
 Jeśli *filename* jest plikiem zasobów (Resources) środowiska .NET Framework, utworzonym na przykład przez [Resource File Generator (Resgen.exe)](/dotnet/framework/tools/resgen-exe-resource-file-generator) lub w środowisku deweloperskim, jest dostępny za pomocą elementów członkowskich w **System.Resources** przestrzeni nazw (zobacz [System.Resources.ResourceManager](https://msdn.microsoft.com/library/system.resources.resourcemanager.aspx) Aby uzyskać więcej informacji). W przypadku wszystkich innych zasobów, użyj **GetManifestResource** \* metody **System.Reflection.Assembly** klasy, aby uzyskać dostęp do zasobu w czasie wykonywania.  
  
 Są także inne opcje konsolidatora, które mają wpływ na Generowanie zestawu:  
  
-   [/ASSEMBLYDEBUG](../../build/reference/assemblydebug-add-debuggableattribute.md)  
  
-   [/ ASSEMBLYLINKRESOURCE](../../build/reference/assemblylinkresource-link-to-dotnet-framework-resource.md)  
  
-   [/ ASSEMBLYMODULE](../../build/reference/assemblymodule-add-a-msil-module-to-the-assembly.md)  
  
-   [/ DELAYSIGN](../../build/reference/delaysign-partially-sign-an-assembly.md)  
  
-   [/ KEYFILE](../../build/reference/keyfile-specify-key-or-key-pair-to-sign-an-assembly.md)  
  
-   [/ KEYCONTAINER](../../build/reference/keycontainer-specify-a-key-container-to-sign-an-assembly.md)  
  
-   [/ NOASSEMBLY](../../build/reference/noassembly-create-a-msil-module.md)  
  
### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Aby ustawić tę opcję konsolidatora w środowisku programowania Visual Studio  
  
1.  Otwórz projekt **stron właściwości** okno dialogowe. Aby uzyskać więcej informacji, zobacz [ustawienie właściwości projektu Visual C++](../../ide/working-with-project-properties.md).  
  
2.  Kliknij przycisk **konsolidatora** folderu.  
  
3.  Kliknij przycisk **dane wejściowe** stronę właściwości.  
  
4.  Modyfikowanie **Osadź plik zasobu zarządzanego** właściwości.  
  
### <a name="to-set-this-linker-option-programmatically"></a>Aby programowo ustawić tę opcję konsolidatora  
  
1.  Zobacz <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.EmbedManagedResourceFile%2A>.  
  
## <a name="see-also"></a>Zobacz też  
 [Ustawianie opcji konsolidatora](../../build/reference/setting-linker-options.md)   
 [Opcje konsolidatora](../../build/reference/linker-options.md)