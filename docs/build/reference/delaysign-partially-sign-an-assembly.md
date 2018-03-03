---
title: "-DELAYSIGN (częściowo Podpisz zestaw) | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- /delaysign
- VC.Project.VCLinkerTool.DelaySign
dev_langs:
- C++
helpviewer_keywords:
- /DELAYSIGN linker option
- DELAYSIGN linker option
- -DELAYSIGN linker option
ms.assetid: 15244d30-3ecb-492f-a408-ffe81f38de20
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: f67e4da2d85d94854ec0802450b41333d6577175
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="delaysign-partially-sign-an-assembly"></a>/DELAYSIGN (Częściowo podpisz zestaw)
```  
/DELAYSIGN[:NO]  
```  
  
## <a name="remarks"></a>Uwagi  
 w przypadku gdy  
  
 BRAK  
 Określa, że zestaw powinny być częściowo niepodpisana.  
  
## <a name="remarks"></a>Uwagi  
 Użyj **/DelaySign** Jeśli chcesz umieścić klucz publiczny w zestawie. Wartość domyślna to **/DelaySign: No**.  
  
 **/DelaySign** opcja nie ma znaczenia, chyba że używana z [/KeyFile](../../build/reference/keyfile-specify-key-or-key-pair-to-sign-an-assembly.md) lub [/KeyContainer](../../build/reference/keycontainer-specify-a-key-container-to-sign-an-assembly.md).  
  
 Gdy użytkownik żąda zestawem całkowicie podpisane, kompilator tworzy skrót pliku, który zawiera manifest (metadanych zestawu) i podpisuje ten skrót z kluczem prywatnym. Wynikowy podpis cyfrowy jest przechowywany w pliku, który zawiera manifest. Jeśli zestaw jest podpisywany z opóźnieniem, konsolidator nie obliczania i przechowywania podpisu, ale rezerw miejsca w pliku, aby później można dodać podpisu.  
  
 Na przykład za pomocą **/DelaySign** umożliwia tester do umieszczenia zestawu w globalnej pamięci podręcznej. Po zakończeniu testowania, można pełni podpisać zestawu przez umieszczenie klucza prywatnego w zestawie.  
  
 Zobacz [silnych nazwach (podpisywanie zestawów) (C + +/ CLI)](../../dotnet/strong-name-assemblies-assembly-signing-cpp-cli.md) i [opóźnione podpisywanie zestawu](/dotnet/framework/app-domains/delay-sign-assembly) Aby uzyskać więcej informacji na temat podpisywania zestawu.  
  
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