---
title: "-IDLOUT (nazwij wyjściowe pliki MIDL) | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- /idlout
- VC.Project.VCLinkerTool.MergedIDLBaseFileName
dev_langs:
- C++
helpviewer_keywords:
- MIDL, output file names
- .idl files, path
- MIDL
- /IDLOUT linker option
- IDL files, path
- -IDLOUT linker option
- IDLOUT linker option
ms.assetid: 10d00a6a-85b4-4de1-8732-e422c6931509
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 8f9f798c31fc4b492565c3406f0cb26251a208d4
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="idlout-name-midl-output-files"></a>/IDLOUT (Nazwij wyjściowe pliki MIDL)
```  
/IDLOUT:[path\]filename  
```  
  
## <a name="parameters"></a>Parametry  
 *Ścieżka*  
 Specyfikacja ścieżką bezwzględną ani względną. Określ ścieżkę, ma wpływ na lokalizację pliku .idl; wszystkie inne pliki są umieszczane w katalogu projektu.  
  
 *Nazwa pliku*  
 Określa nazwę pliku .idl utworzony przez kompilator MIDL. Przyjęto, że nie rozszerzenie pliku; Określ *filename*.idl, jeśli chcesz, aby rozszerzenie .idl.  
  
## <a name="remarks"></a>Uwagi  
 Opcja/idlout Określa nazwę i rozszerzenie pliku .idl.  
  
 Kompilator MIDL jest wywoływana przez konsolidator Visual C++ w trakcie łączenia projektów, które mają [modułu](../../windows/module-cpp.md) atrybutu.  
  
 / IDLOUT określa również nazw plików, innych plików wyjściowych skojarzono kompilatora MIDL:  
  
-   *Nazwa pliku*.tlb  
  
-   *Nazwa pliku*_p.c  
  
-   *Nazwa pliku*_i.c  
  
-   *Nazwa pliku*.h  
  
 *Nazwa pliku* jest parametrem, który jest przekazywany do/idlout. Jeśli [/tlbout](../../build/reference/tlbout-name-dot-tlb-file.md) określono pliku .tlb pobierze nazwy z/tlbout *filename*.  
  
 Jeśli określisz/idlout ani/tlbout konsolidator utworzy vc70.tlb, vc70.idl vc70_p.c, vc70_i.c i vc70.h.  
  
### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Aby ustawić tę opcję konsolidatora w środowisku programowania Visual Studio  
  
1.  Otwórz projekt **strony właściwości** okno dialogowe. Aby uzyskać więcej informacji, zobacz [Ustawianie właściwości projektu Visual C++](../../ide/working-with-project-properties.md).  
  
2.  Kliknij przycisk **konsolidatora** folderu.  
  
3.  Kliknij przycisk **osadzonych IDL** strony właściwości.  
  
4.  Modyfikowanie **scalania nazwa pliku IDL Base** właściwości.  
  
### <a name="to-set-this-linker-option-programmatically"></a>Aby programowo ustawić tę opcję konsolidatora  
  
-   Zobacz <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.MergedIDLBaseFileName%2A>.  
  
## <a name="see-also"></a>Zobacz też  
 [Ustawianie opcji konsolidatora](../../build/reference/setting-linker-options.md)   
 [Opcje konsolidatora](../../build/reference/linker-options.md)   
 [/ IGNOREIDL (nie Przetwarzaj atrybutów w MIDL)](../../build/reference/ignoreidl-don-t-process-attributes-into-midl.md)   
 [/ MIDL (Określ opcje wiersza polecenia MIDL)](../../build/reference/midl-specify-midl-command-line-options.md)   
 [Kompilowanie programu opartego na atrybutach](../../windows/building-an-attributed-program.md)