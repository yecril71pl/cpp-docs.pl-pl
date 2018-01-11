---
title: "-SWAPRUN (Załaduj dane wyjściowe konsolidatora do pliku Swap) | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- VC.Project.VCLinkerTool.SwapRunFromNet
- /swaprun
- VC.Project.VCLinkerTool.SwapRunFromCD
dev_langs: C++
helpviewer_keywords:
- -SWAPRUN linker option
- files [C++], LINK
- LINK tool [C++], output
- linker [C++], copying output to swap file
- swap file for linker output
- output files, linker
- /SWAPRUN linker option
- SWAPRUN linker option
ms.assetid: 4a1e7f46-4399-4161-8dfc-d6a71beaf683
caps.latest.revision: "8"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: a3b6829a20e80ab8548460205169e1cd258694e0
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="swaprun-load-linker-output-to-swap-file"></a>/SWAPRUN (Załaduj pliki wyjściowe konsolidatora do pliku Swap)
```  
/SWAPRUN:{NET|CD}  
```  
  
## <a name="remarks"></a>Uwagi  
 Opcja/swaprun informuje system operacyjny, aby najpierw skopiował konsolidatora dane wyjściowe do pliku wymiany, a następnie uruchomił obraz stamtąd. Jest to funkcja systemu Windows NT 4.0 (i nowszych).  
  
 Jeżeli określono sieć, system operacyjny najpierw skopiować obraz binarny z sieci do pliku wymiany i załadować je stamtąd. Ta opcja jest przydatna do uruchamiania aplikacji za pośrednictwem sieci. Jeśli dysk CD zostanie określony, system operacyjny skopiuje obraz na dysku wymiennym do pliku stronicowania, a następnie ładowania ich.  
  
### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Aby ustawić tę opcję konsolidatora w środowisku programowania Visual Studio  
  
1.  Otwórz projekt **strony właściwości** okno dialogowe. Aby uzyskać więcej informacji, zobacz [Ustawianie właściwości projektu Visual C++](../../ide/working-with-project-properties.md).  
  
2.  Kliknij przycisk **konsolidatora** folderu.  
  
3.  Kliknij przycisk **systemu** strony właściwości.  
  
4.  Zmień jedną z następujących właściwości:  
  
    -   **Wymienne uruchamianie z dysku CD**  
  
    -   **Wymienne uruchamianie z sieci**  
  
### <a name="to-set-this-linker-option-programmatically"></a>Aby programowo ustawić tę opcję konsolidatora  
  
1.  Zobacz <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.SwapRunFromCD%2A> i <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.SwapRunFromNet%2A> właściwości.  
  
## <a name="see-also"></a>Zobacz też  
 [Ustawianie opcji konsolidatora](../../build/reference/setting-linker-options.md)   
 [Opcje konsolidatora](../../build/reference/linker-options.md)