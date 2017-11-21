---
title: "-KEYFILE (Określ klucz lub parę kluczy, aby podpisać zestaw) | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- /keyfile
- VC.Project.VCLinkerTool.KeyFile
dev_langs: C++
helpviewer_keywords:
- /KEYFILE linker option
- -KEYFILE linker option
- KEYFILE linker option
ms.assetid: 9b71f8c0-541c-4fe5-a0c7-9364f42ecb06
caps.latest.revision: "12"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 6a061abf3a8f16bdd38a8b41a3b97a5f4ba1a885
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="keyfile-specify-key-or-key-pair-to-sign-an-assembly"></a>/KEYFILE (Określ klucz lub parę kluczy, aby podpisać zestaw)
```  
/KEYFILE:filename  
```  
  
## <a name="remarks"></a>Uwagi  
 gdzie:  
  
 *Nazwa pliku*  
 Plik, który zawiera klucz. Umieść ciąg w podwójny cudzysłów ("") zawiera spację.  
  
## <a name="remarks"></a>Uwagi  
 Konsolidator wstawia klucz publiczny w manifeście zestawu i podpisuje następnie zestawie końcowym z kluczem prywatnym. Aby wygenerować plik klucza, wpisz [sn -k](/dotnet/framework/tools/sn-exe-strong-name-tool) *filename* w wierszu polecenia. Podpisem zestawu jest nazywany ma silnej nazwy.  
  
 Jeśli kompilacji z [/LN](../../build/reference/ln-create-msil-module.md), nazwa pliku klucza jest przechowywany w module i włączyć do zestawu, który jest tworzony podczas kompilowania zestawu, który zawiera jawnego odwołania do modułu, za pośrednictwem [#using](../../preprocessor/hash-using-directive-cpp.md), lub podczas łączenia z [/assemblymodule](../../build/reference/assemblymodule-add-a-msil-module-to-the-assembly.md).  
  
 Można również przekazać dane szyfrowania do konsolidacji z [/KeyContainer](../../build/reference/keycontainer-specify-a-key-container-to-sign-an-assembly.md). Użyj [/DelaySign](../../build/reference/delaysign-partially-sign-an-assembly.md) Jeśli chcesz częściowo podpisanych zestawów. Zobacz [silnych nazwach (podpisywanie zestawów) (C + +/ CLI)](../../dotnet/strong-name-assemblies-assembly-signing-cpp-cli.md) Aby uzyskać więcej informacji na temat podpisywania zestawu.  
  
 W przypadku obu **/KeyFile** i **/KeyContainer** podano (przez opcję wiersza polecenia lub przez atrybut niestandardowy), konsolidator próbują używać najpierw kontener kluczy. Jeśli który zakończy się powodzeniem, zestaw jest podpisany z informacjami w kontenerze kluczy. Jeśli konsolidator nie może znaleźć kontener kluczy, spróbuje plik określony z/KeyFile. Jeśli który zakończy się powodzeniem, zestaw jest podpisany za pomocą informacji w pliku klucza i informacje o kluczu zostaną zainstalowane w kontenerze kluczy (podobnie jak sn -i), aby w następnej kompilacji, kontener kluczy będzie nieprawidłowa.  
  
 Należy pamiętać, że plik klucza może zawierać tylko klucz publiczny.  
  
 Zobacz [tworzenie i zestawy Using Strong-Named](/dotnet/framework/app-domains/create-and-use-strong-named-assemblies) Aby uzyskać więcej informacji na temat podpisywania zestawu.  
  
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