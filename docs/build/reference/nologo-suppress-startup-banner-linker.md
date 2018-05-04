---
title: -NOLOGO (Pomiń transparent początkowy) (konsolidator) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- VC.Project.VCLinkerTool.SuppressStartupBanner
- /nologo
dev_langs:
- C++
helpviewer_keywords:
- suppress startup banner linker option
- -NOLOGO linker option
- /NOLOGO linker option
- copyright message
- version numbers, preventing linker display
- banners, suppressing startup
- NOLOGO linker option
ms.assetid: 3b20dddd-eca6-4545-a331-9f70bf720197
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: a76e99496114c0ebdc60f81724e67dd88a482055
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
---
# <a name="nologo-suppress-startup-banner-linker"></a>/NOLOGO (Pomiń transparent początkowy) (Konsolidator)
```  
/NOLOGO  
```  
  
## <a name="remarks"></a>Uwagi  
 Opcja/nologo uniemożliwia wyświetlanie liczby praw autorskich komunikat i wersji.  
  
 Ta opcja pomija również wyświetlanie plików polecenia. Aby uzyskać więcej informacji, zobacz [pliki poleceń LINK](../../build/reference/link-command-files.md).  
  
 Domyślnie te informacje są wysyłane przez konsolidator, aby w oknie danych wyjściowych. W wierszu polecenia są wysyłane na wyjście standardowe i mogą zostać przekierowane do pliku.  
  
### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Aby ustawić tę opcję konsolidatora w środowisku programowania Visual Studio  
  
1.  Tej opcji należy używać tylko z wiersza polecenia.  
  
### <a name="to-set-this-linker-option-programmatically"></a>Aby programowo ustawić tę opcję konsolidatora  
  
1.  Nie można zmienić tej opcji konsolidatora programowo.  
  
## <a name="see-also"></a>Zobacz też  
 [Ustawianie opcji konsolidatora](../../build/reference/setting-linker-options.md)   
 [Opcje konsolidatora](../../build/reference/linker-options.md)