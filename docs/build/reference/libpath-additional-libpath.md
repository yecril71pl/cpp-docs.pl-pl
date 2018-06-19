---
title: -LIBPATH (dodatkowa Libpath) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- /libpath
- VC.Project.VCLinkerTool.AdditionalLibraryDirectories
dev_langs:
- C++
helpviewer_keywords:
- LIBPATH linker option
- /LIBPATH linker option
- Additional Libpath linker option
- environment library path override
- -LIBPATH linker option
- library path linker option
ms.assetid: 7240af0b-9a3d-4d53-8169-2a92cd6958ba
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 5ccb94ad20735e81fc3d83f757cc0265cdc32169
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
ms.locfileid: "32372883"
---
# <a name="libpath-additional-libpath"></a>/LIBPATH (Dodatkowa Libpath)
```  
/LIBPATH:dir  
```  
  
## <a name="remarks"></a>Uwagi  
 gdzie:  
  
 `dir`  
 Określa ścieżkę czy konsolidator przeszuka przed przeszukuje ścieżkę określonego w opcji środowiska LIB.  
  
## <a name="remarks"></a>Uwagi  
 Opcja/libpath umożliwia zastąpienie środowiska ścieżki biblioteki. Konsolidator najpierw wyszukać w ścieżce określonej przez tę opcję, a następnie wyszukaj w ścieżce określonej w zmiennej środowiskowej LIB. Można określić tylko jeden katalog dla każdej opcji/libpath, wprowadzony. Jeśli chcesz określić więcej niż jeden katalog, należy określić wiele opcji/libpath. Konsolidator będzie wyszukiwać określone katalogi w kolejności.  
  
### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Aby ustawić tę opcję konsolidatora w środowisku programowania Visual Studio  
  
1.  Otwórz projekt **strony właściwości** okno dialogowe. Aby uzyskać więcej informacji, zobacz [Ustawianie właściwości projektu Visual C++](../../ide/working-with-project-properties.md).  
  
2.  Kliknij przycisk **konsolidatora** folderu.  
  
3.  Kliknij przycisk **ogólne** strony właściwości.  
  
4.  Modyfikowanie **dodatkowe katalogi bibliotek** właściwości.  
  
### <a name="to-set-this-linker-option-programmatically"></a>Aby programowo ustawić tę opcję konsolidatora  
  
-   Zobacz <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.AdditionalLibraryDirectories%2A>.  
  
## <a name="see-also"></a>Zobacz też  
 [Ustawianie opcji konsolidatora](../../build/reference/setting-linker-options.md)   
 [Opcje konsolidatora](../../build/reference/linker-options.md)