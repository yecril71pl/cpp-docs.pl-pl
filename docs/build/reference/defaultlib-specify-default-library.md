---
title: "-DEFAULTLIB (określ bibliotekę domyślną) | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- VC.Project.VCLinkerTool.DefaultLibraries
- /defaultlib
dev_langs: C++
helpviewer_keywords:
- -DEFAULTLIB linker option
- DEFAULTLIB linker option
- /DEFAULTLIB linker option
- libraries, adding to list of
ms.assetid: 6af7ff49-c170-4a13-97e2-2b9ae2de20c9
caps.latest.revision: "9"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 40fe07543dd9dc65d93cc9f79504f5fd324204dd
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
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