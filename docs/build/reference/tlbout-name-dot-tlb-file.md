---
title: -TLBOUT (nazwa. Plik biblioteki TLB) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- VC.Project.VCLinkerTool.TypeLibraryFile
- /tlbout
dev_langs:
- C++
helpviewer_keywords:
- tlb files, renaming
- TLBOUT linker option
- /TLBOUT linker option
- .tlb files, renaming
- -TLBOUT linker option
ms.assetid: 0df6d078-2e48-46c9-a1a5-02674d85dce8
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 1cc4103c387fe7a3dae68b642c10e326b361c54a
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
ms.locfileid: "32376855"
---
# <a name="tlbout-name-tlb-file"></a>/TLBOUT (Nazywanie pliku .TLB)
```  
/TLBOUT:[path\]filename  
```  
  
## <a name="remarks"></a>Uwagi  
 gdzie:  
  
 *Ścieżka*  
 Specyfikacja ścieżką bezwzględną ani względną, na którym ma zostać utworzony pliku .tlb.  
  
 *Nazwa pliku*  
 Określa nazwę pliku .tlb utworzony przez kompilator MIDL. Przyjęto, że nie rozszerzenie pliku; Określ *filename*.tlb, jeśli chcesz, aby rozszerzenie .tlb.  
  
## <a name="remarks"></a>Uwagi  
 Opcja/tlbout Określa nazwę i rozszerzenie pliku .tlb.  
  
 Kompilator MIDL jest wywoływana przez konsolidator Visual C++ w trakcie łączenia projektów, które mają [modułu](../../windows/module-cpp.md) atrybutu.  
  
 Jeśli nie określono/tlbout, pliku .tlb otrzyma nazwy z [/idlout](../../build/reference/idlout-name-midl-output-files.md) *filename*. Jeśli nie określono/idlout, pliku .tlb zostanie wywołana metoda vc70.tlb.  
  
### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Aby ustawić tę opcję konsolidatora w środowisku programowania Visual Studio  
  
1.  Otwórz projekt **strony właściwości** okno dialogowe. Aby uzyskać więcej informacji, zobacz [Ustawianie właściwości projektu Visual C++](../../ide/working-with-project-properties.md).  
  
2.  Kliknij przycisk **konsolidatora** folderu.  
  
3.  Kliknij przycisk **osadzonych IDL** strony właściwości.  
  
4.  Modyfikowanie **biblioteki typów** właściwości.  
  
### <a name="to-set-this-linker-option-programmatically"></a>Aby programowo ustawić tę opcję konsolidatora  
  
1.  Zobacz <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.TypeLibraryFile%2A>.  
  
## <a name="see-also"></a>Zobacz też  
 [Ustawianie opcji konsolidatora](../../build/reference/setting-linker-options.md)   
 [Opcje konsolidatora](../../build/reference/linker-options.md)   
 [/ IGNOREIDL (nie Przetwarzaj atrybutów w MIDL)](../../build/reference/ignoreidl-don-t-process-attributes-into-midl.md)   
 [/ MIDL (Określ opcje wiersza polecenia MIDL)](../../build/reference/midl-specify-midl-command-line-options.md)   
 [Kompilowanie programu opartego na atrybutach](../../windows/building-an-attributed-program.md)