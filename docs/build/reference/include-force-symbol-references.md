---
title: -INCLUDE (Wymuszaj odwołania do symboli) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- /include
- VC.Project.VCLinkerTool.ForceSymbolReferences
dev_langs:
- C++
helpviewer_keywords:
- INCLUDE linker option
- force symbol references linker option
- symbol references linker force
- /INCLUDE linker option
- symbols, add to symbol table
- -INCLUDE linker option
ms.assetid: 4a039677-360a-480f-bd0b-448e239b449c
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: cfe65344e41b98841c3a4e7bca72b762197510b8
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
---
# <a name="include-force-symbol-references"></a>/INCLUDE (Wymuszaj odwołania do symboli)
```  
/INCLUDE:symbol  
```  
  
## <a name="remarks"></a>Uwagi  
 gdzie:  
  
 `symbol`  
 Określa symbol ma zostać dodany do tabeli symboli.  
  
## <a name="remarks"></a>Uwagi  
 Opcja/include informuje konsolidator, aby dodał określony symbol do tabeli symboli.  
  
 Aby określić wiele symboli, wpisz przecinka (,), średnikiem (;) lub odstęp między nazwami symbolu. W wierszu polecenia, określić/include:`symbol` raz dla każdego symbolu.  
  
 Usuwa konsolidator `symbol` , dodając obiekt, który zawiera definicję symbolu do programu. Ta funkcja jest przydatna przy tym obiektu biblioteki, które w przeciwnym razie nie będzie można połączyć z programem.  
  
 Określanie symbol z tą opcją zastąpienia usunięcie tego symbolu przez [/OPT:REF](../../build/reference/opt-optimizations.md).  
  
### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Aby ustawić tę opcję konsolidatora w środowisku programowania Visual Studio  
  
1.  Otwórz projekt **strony właściwości** okno dialogowe. Aby uzyskać więcej informacji, zobacz [Ustawianie właściwości projektu Visual C++](../../ide/working-with-project-properties.md).  
  
2.  Kliknij przycisk **konsolidatora** folderu.  
  
3.  Kliknij przycisk **dane wejściowe** strony właściwości.  
  
4.  Modyfikowanie **Wymuś odwołania do symboli** właściwości.  
  
### <a name="to-set-this-linker-option-programmatically"></a>Aby programowo ustawić tę opcję konsolidatora  
  
-   Zobacz <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.ForceSymbolReferences%2A>.  
  
## <a name="see-also"></a>Zobacz też  
 [Ustawianie opcji konsolidatora](../../build/reference/setting-linker-options.md)   
 [Opcje konsolidatora](../../build/reference/linker-options.md)