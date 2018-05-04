---
title: -DEFAULTLIB (określ bibliotekę domyślną) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- VC.Project.VCLinkerTool.DefaultLibraries
- /defaultlib
dev_langs:
- C++
helpviewer_keywords:
- -DEFAULTLIB linker option
- DEFAULTLIB linker option
- /DEFAULTLIB linker option
- libraries, adding to list of
ms.assetid: 6af7ff49-c170-4a13-97e2-2b9ae2de20c9
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: e48db05ea50917a09e618c782d86dace73a1bf7e
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
---
# <a name="defaultlib-specify-default-library"></a>/DEFAULTLIB (Określ bibliotekę domyślną)
```  
/DEFAULTLIB:library  
```  
  
## <a name="remarks"></a>Uwagi  
 gdzie:  
  
 *Biblioteka*  
 Nazwa biblioteki do przeszukania podczas rozpoznawania odwołań zewnętrznych.  
  
## <a name="remarks"></a>Uwagi  
 Opcja /DEFAULTLIB doda *biblioteki* do listy bibliotek podczas rozpoznawania odwołań wyszukiwania łącza. Po libraries określonych w wierszu polecenia, a przed biblioteki domyślne o nazwie w plikach .obj przeszukiwany jest określony za pomocą /DEFAULTLIB biblioteki.  
  
 [Ignoruj wszystkie domyślne biblioteki](../../build/reference/nodefaultlib-ignore-libraries.md) (/ NODEFAULTLIB) opcja przesłania /DEFAULTLIB:*biblioteki*. [Ignoruj biblioteki](../../build/reference/nodefaultlib-ignore-libraries.md) (/ NODEFAULTLIB:*biblioteki*) opcja przesłania /DEFAULTLIB:*biblioteki* gdy taki sam *biblioteki* jest nazwa określony w obu.  
  
### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Aby ustawić tę opcję konsolidatora w środowisku programowania Visual Studio  
  
-   Ta opcja konsolidatora nie jest dostępny w środowisku programowania Visual Studio. Aby dodać biblioteki do fazy łącza, użyj **dodatkowe zależności** właściwość z **dane wejściowe** strony właściwości.  
  
### <a name="to-set-this-linker-option-programmatically"></a>Aby programowo ustawić tę opcję konsolidatora  
  
-   Zobacz <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.AdditionalOptions%2A>.  
  
## <a name="see-also"></a>Zobacz też  
 [Ustawianie opcji konsolidatora](../../build/reference/setting-linker-options.md)   
 [Opcje konsolidatora](../../build/reference/linker-options.md)