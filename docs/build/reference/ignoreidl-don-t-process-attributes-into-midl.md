---
title: "-IGNOREIDL (ADAM &#39; t atrybutów w MIDL) | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- VC.Project.VCLinkerTool.IgnoreEmbeddedIDL
- /ignoreidl
dev_langs: C++
helpviewer_keywords:
- IGNOREIDL linker option
- -IGNOREIDL linker option
- /IGNOREIDL linker option
ms.assetid: 29514098-6a1c-4317-af2f-1dc268972780
caps.latest.revision: "8"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: fe2f1d33f9269380bf0d914d5805cce3b0a92b90
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="ignoreidl-don39t-process-attributes-into-midl"></a>/ IGNOREIDL (ADAM &#39; t atrybutów w MIDL)
```  
/IGNOREIDL  
```  
  
## <a name="remarks"></a>Uwagi  
 Opcja/ignoreidl Określa, że jakaś [atrybuty IDL](../../windows/idl-attributes.md) źródła kodu nie powinny być przetwarzane do pliku .idl.  
  
### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Aby ustawić tę opcję konsolidatora w środowisku programowania Visual Studio  
  
1.  Otwórz projekt **strony właściwości** okno dialogowe. Aby uzyskać więcej informacji, zobacz [Ustawianie właściwości projektu Visual C++](../../ide/working-with-project-properties.md).  
  
2.  Kliknij przycisk **konsolidatora** folderu.  
  
3.  Kliknij przycisk **osadzonych IDL** strony właściwości.  
  
4.  Modyfikowanie **Ignoruj osadzonych IDL** właściwości.  
  
### <a name="to-set-this-linker-option-programmatically"></a>Aby programowo ustawić tę opcję konsolidatora  
  
-   Zobacz <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.IgnoreEmbeddedIDL%2A>.  
  
## <a name="see-also"></a>Zobacz też  
 [Ustawianie opcji konsolidatora](../../build/reference/setting-linker-options.md)   
 [Opcje konsolidatora](../../build/reference/linker-options.md)   
 [/ IDLOUT (nazwij wyjściowe pliki MIDL)](../../build/reference/idlout-name-midl-output-files.md)   
 [/ TLBOUT (nazwa. Plik biblioteki TLB)](../../build/reference/tlbout-name-dot-tlb-file.md)   
 [/ MIDL (Określ opcje wiersza polecenia MIDL)](../../build/reference/midl-specify-midl-command-line-options.md)   
 [Kompilowanie programu opartego na atrybutach](../../windows/building-an-attributed-program.md)