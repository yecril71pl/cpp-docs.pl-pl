---
title: "-KEYCONTAINER (Określ klucz kontenera, aby podpisać zestaw) | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- VC.Project.VCLinkerTool.KeyContainer
- /keycontainer
dev_langs: C++
helpviewer_keywords:
- KEYCONTAINER linker option
- /KEYCONTAINER linker option
- -KEYCONTAINER linker option
ms.assetid: 94882d12-b77a-49c7-96d0-18a31aee001e
caps.latest.revision: "12"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: f0e1f31e85c23b32bee1b8b968bbec65ee82beb9
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="keycontainer-specify-a-key-container-to-sign-an-assembly"></a>/KEYCONTAINER (Określ klucz kontenera, aby podpisać zestaw)
```  
/KEYCONTAINER:name  
```  
  
## <a name="remarks"></a>Uwagi  
 w przypadku gdy  
  
 *Nazwa*  
 Kontener, który zawiera klucz. Umieść ciąg w podwójny cudzysłów ("") zawiera spację.  
  
## <a name="remarks"></a>Uwagi  
 Konsolidator tworzy podpisanych zestawów wstawianie klucza publicznego do manifestu zestawu i podpisywania z kluczem prywatnym zestawie końcowym. Aby wygenerować plik klucza, wpisz [sn -k](/dotnet/framework/tools/sn-exe-strong-name-tool) *filename* w wierszu polecenia. **SN -i** instaluje pary kluczy do kontenera.  
  
 Jeśli kompilacji z [/LN](../../build/reference/ln-create-msil-module.md), nazwa pliku klucza jest przechowywany w module i włączyć do zestawu, który jest tworzony podczas kompilowania zestawu, który zawiera jawnego odwołania do modułu, za pośrednictwem [#using](../../preprocessor/hash-using-directive-cpp.md), lub podczas łączenia z [/assemblymodule](../../build/reference/assemblymodule-add-a-msil-module-to-the-assembly.md).  
  
 Można również przekazać do kompilatora z informacjami szyfrowania [/KeyFile](../../build/reference/keyfile-specify-key-or-key-pair-to-sign-an-assembly.md). Użyj [/DelaySign](../../build/reference/delaysign-partially-sign-an-assembly.md) Jeśli chcesz częściowo podpisanych zestawów. Zobacz [silnych nazwach (podpisywanie zestawów) (C + +/ CLI)](../../dotnet/strong-name-assemblies-assembly-signing-cpp-cli.md) Aby uzyskać więcej informacji na temat podpisywania zestawu.  
  
 Inne opcje konsolidatora, które mają wpływ na generowanie zestawów są:  
  
-   [/ ASSEMBLYDEBUG](../../build/reference/assemblydebug-add-debuggableattribute.md)  
  
-   [/ ASSEMBLYLINKRESOURCE](../../build/reference/assemblylinkresource-link-to-dotnet-framework-resource.md)  
  
-   [/ ASSEMBLYMODULE](../../build/reference/assemblymodule-add-a-msil-module-to-the-assembly.md)  
  
-   [/ ASSEMBLYRESOURCE](../../build/reference/assemblyresource-embed-a-managed-resource.md)  
  
-   [/ NOASSEMBLY](../../build/reference/noassembly-create-a-msil-module.md)  
  
### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Aby ustawić tę opcję konsolidatora w środowisku programowania Visual Studio  
  
1.  Otwórz projekt **strony właściwości** okno dialogowe. Aby uzyskać więcej informacji, zobacz [Ustawianie właściwości projektu Visual C++](../../ide/working-with-project-properties.md).  
  
2.  Kliknij przycisk **konsolidatora** folderu.  
  
3.  Kliknij przycisk **wiersza polecenia** strony właściwości.  
  
4.  Typ opcji do **dodatkowe opcje** pole.  
  
### <a name="to-set-this-linker-option-programmatically"></a>Aby programowo ustawić tę opcję konsolidatora  
  
-   Zobacz <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.AdditionalOptions%2A>.  
  
## <a name="see-also"></a>Zobacz też  
 [Ustawianie opcji konsolidatora](../../build/reference/setting-linker-options.md)   
 [Opcje konsolidatora](../../build/reference/linker-options.md)