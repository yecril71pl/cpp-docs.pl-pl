---
title: "-MIDL (Określ opcje wiersza polecenia MIDL) | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- /midl
- VC.Project.VCLinkerTool.MidlCommandFile
dev_langs:
- C++
helpviewer_keywords:
- -MIDL linker option
- MIDL
- /MIDL linker option
- MIDL linker option
- MIDL, command line options
ms.assetid: 22dc259e-b34c-4ed3-a380-4beb734482c1
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: f8e842f4cf0f9c52945c04739879d0132eb34171
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="midl-specify-midl-command-line-options"></a>/MIDL (Określ opcje wiersza polecenia MIDL)
```  
/MIDL:@file  
```  
  
## <a name="remarks"></a>Uwagi  
 gdzie:  
  
 `file`  
 Nazwa pliku, który zawiera [opcje wiersza polecenia MIDL](http://msdn.microsoft.com/library/windows/desktop/aa366839).  
  
## <a name="remarks"></a>Uwagi  
 Należy podać wszystkie opcje konwersji pliku IDL do pliku TLB w `file`; Nie można określić opcje wiersza polecenia MIDL w wierszu polecenia konsolidatora. Jeśli nie określono /MIDL, kompilator MIDL zostanie wywołany z nazwa pliku IDL i inne opcje.  
  
 Plik powinien zawierać jedną opcję wiersza polecenia MIDL na wiersz.  
  
### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Aby ustawić tę opcję konsolidatora w środowisku programowania Visual Studio  
  
1.  Otwórz projekt **strony właściwości** okno dialogowe. Aby uzyskać więcej informacji, zobacz [Ustawianie właściwości projektu Visual C++](../../ide/working-with-project-properties.md).  
  
2.  Kliknij przycisk **konsolidatora** folderu.  
  
3.  Kliknij przycisk **osadzonych IDL** strony właściwości.  
  
4.  Modyfikowanie **polecenia MIDL** właściwości.  
  
### <a name="to-set-this-linker-option-programmatically"></a>Aby programowo ustawić tę opcję konsolidatora  
  
-   Zobacz <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.MidlCommandFile%2A>.  
  
## <a name="see-also"></a>Zobacz też  
 [Ustawianie opcji konsolidatora](../../build/reference/setting-linker-options.md)   
 [Opcje konsolidatora](../../build/reference/linker-options.md)   
 [/ IDLOUT (nazwij wyjściowe pliki MIDL)](../../build/reference/idlout-name-midl-output-files.md)   
 [/ IGNOREIDL (nie Przetwarzaj atrybutów w MIDL)](../../build/reference/ignoreidl-don-t-process-attributes-into-midl.md)   
 [/ TLBOUT (nazwa. Plik biblioteki TLB)](../../build/reference/tlbout-name-dot-tlb-file.md)   
 [Kompilowanie programu opartego na atrybutach](../../windows/building-an-attributed-program.md)