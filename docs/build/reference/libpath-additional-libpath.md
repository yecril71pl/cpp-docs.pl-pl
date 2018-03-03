---
title: -LIBPATH (dodatkowa Libpath) | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
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
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 452158c2767ec4f0bf30a88df17b7c01496e24e7
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
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