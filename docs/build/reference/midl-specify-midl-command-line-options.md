---
title: -MIDL (Określ opcje wiersza polecenia MIDL) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
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
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 7b3f20fddd657d1e5e57caf65ecc8e2c52afbf12
ms.sourcegitcommit: e9ce38decc9f986edab5543de3464b11ebccb123
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/13/2018
ms.locfileid: "42466039"
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
 Wszystkie opcje konwersji w pliku IDL z plikiem TLB musi być podany w `file`; Nie można określić opcje wiersza polecenia MIDL w wierszu polecenia konsolidatora. Jeśli /MIDL nie zostanie określony, kompilator MIDL zostanie wywołany za pomocą tylko nazwę pliku IDL i inne opcje.  
  
 Ten plik powinien zawierać jedną opcję wiersza polecenia MIDL na wiersz.  
  
### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Aby ustawić tę opcję konsolidatora w środowisku programowania Visual Studio  
  
1.  Otwórz projekt **stron właściwości** okno dialogowe. Aby uzyskać więcej informacji, zobacz [ustawienie właściwości projektu Visual C++](../../ide/working-with-project-properties.md).  
  
2.  Kliknij przycisk **konsolidatora** folderu.  
  
3.  Kliknij przycisk **osadzone IDL** stronę właściwości.  
  
4.  Modyfikowanie **polecenia MIDL** właściwości.  
  
### <a name="to-set-this-linker-option-programmatically"></a>Aby programowo ustawić tę opcję konsolidatora  
  
-   Zobacz <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.MidlCommandFile%2A>.  
  
## <a name="see-also"></a>Zobacz też  
 [Ustawianie opcji konsolidatora](../../build/reference/setting-linker-options.md)   
 [Opcje konsolidatora](../../build/reference/linker-options.md)   
 [/ IDLOUT (nazwij wyjściowe pliki MIDL)](../../build/reference/idlout-name-midl-output-files.md)   
 [/ IGNOREIDL (nie Przetwarzaj atrybutów w MIDL)](../../build/reference/ignoreidl-don-t-process-attributes-into-midl.md)   
 [/ TLBOUT (nazwa. Plik TLB)](../../build/reference/tlbout-name-dot-tlb-file.md)   
 [Kompilowanie programu opartego na atrybutach](../../windows/building-an-attributed-program.md)