---
title: -NODEFAULTLIB (Ignoruj biblioteki) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- VC.Project.VCLinkerTool.OVERWRITEAllDefaultLibraries
- VC.Project.VCLinkerTool.OVERWRITEDefaultLibraryNames
- /nodefaultlib
dev_langs:
- C++
helpviewer_keywords:
- default libraries, removing
- -NODEFAULTLIB linker option
- libraries, ignore
- NODEFAULTLIB linker option
- /NODEFAULTLIB linker option
- ignore libraries linker option
ms.assetid: 7270b673-6711-468e-97a7-c2925ac2be6e
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 51caac10218d5f4d1787b2256875001ac32dc2b9
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
---
# <a name="nodefaultlib-ignore-libraries"></a>/NODEFAULTLIB (Ignoruj biblioteki)
```  
/NODEFAULTLIB[:library]   
```  
  
## <a name="remarks"></a>Uwagi  
 gdzie:  
  
 *Biblioteka*  
 Biblioteka, która ma konsolidator, aby zignorować podczas rozpoznawania odwołań zewnętrznych.  
  
## <a name="remarks"></a>Uwagi  
 Opcja/nodefaultlib informuje konsolidator, aby usunąć co najmniej jedną domyślną bibliotekę z listy bibliotek przeszukiwanych podczas rozpoznawania odwołań zewnętrznych.  
  
 Aby utworzyć plik .obj, który nie zawiera odwołania do bibliotek domyślnych, użyj [/Zl (Pomiń domyślną nazwę biblioteki)](../../build/reference/zl-omit-default-library-name.md).  
  
 Domyślnie/nodefaultlib usuwa wszystkie domyślne biblioteki z listy bibliotek przeszukiwanych podczas rozpoznawania odwołań zewnętrznych. Opcjonalny *biblioteki* parametr umożliwia usunięcie określonej biblioteki lub biblioteki z listy bibliotek wyszukiwania podczas rozpoznawania odwołań zewnętrznych. Określ jedną z opcji/nodefaultlib bibliotek, które chcesz wykluczyć.  
  
 Konsolidator usuwa odwołania do definicje zewnętrzne wyszukując najpierw w bibliotekach, które zostaną jawnie określone, a następnie w domyślnej biblioteki określona z opcją /DEFAULTLIB, a następnie w nazwie w plikach .obj biblioteki domyślne.  
  
 / NODEFAULTLIB:*biblioteki* zastępuje [/DEFAULTLIB:](../../build/reference/defaultlib-specify-default-library.md)*biblioteki* gdy taki sam *biblioteki* nazwa jest określona w obu.  
  
 Użycie opcji/nodefaultlib, na przykład do kompilacji programu bez biblioteki wykonawczej C, może być również używać [/Entry](../../build/reference/entry-entry-point-symbol.md) do określenia punktu wejścia (funkcja) w programie. Aby uzyskać więcej informacji, zobacz [Biblioteka CRT — funkcje](../../c-runtime-library/crt-library-features.md).  
  
### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Aby ustawić tę opcję konsolidatora w środowisku programowania Visual Studio  
  
1.  Otwórz projekt **strony właściwości** okno dialogowe. Aby uzyskać więcej informacji, zobacz [Ustawianie właściwości projektu Visual C++](../../ide/working-with-project-properties.md).  
  
2.  Kliknij przycisk **konsolidatora** folderu.  
  
3.  Kliknij przycisk **dane wejściowe**strony właściwości.  
  
4.  Wybierz **Ignoruj wszystkie domyślne biblioteki** właściwości lub określ listę bibliotek, aby zignorować w **Ignoruj określoną bibliotekę** właściwości. **Wiersza polecenia** strony właściwości wyświetli wpływu zmiany tych właściwości.  
  
### <a name="to-set-this-linker-option-programmatically"></a>Aby programowo ustawić tę opcję konsolidatora  
  
-   Zobacz <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.IgnoreDefaultLibraryNames%2A> i <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.IgnoreAllDefaultLibraries%2A>.  
  
## <a name="see-also"></a>Zobacz też  
 [Ustawianie opcji konsolidatora](../../build/reference/setting-linker-options.md)   
 [Opcje konsolidatora](../../build/reference/linker-options.md)