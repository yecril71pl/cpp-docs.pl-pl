---
title: -SWAPRUN (Załaduj dane wyjściowe konsolidatora do pliku Swap) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- VC.Project.VCLinkerTool.SwapRunFromNet
- /swaprun
- VC.Project.VCLinkerTool.SwapRunFromCD
dev_langs:
- C++
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
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 1867eb55f9ebcaba2d29f7b9b4b2f44a68164390
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/17/2018
ms.locfileid: "45717499"
---
# <a name="swaprun-load-linker-output-to-swap-file"></a>/SWAPRUN (Załaduj pliki wyjściowe konsolidatora do pliku Swap)

```
/SWAPRUN:{NET|CD}
```

## <a name="remarks"></a>Uwagi

Opcja/swaprun informuje system operacyjny do pierwszego kopiowania konsolidatora dane wyjściowe do pliku wymiany, a następnie uruchomił obraz stamtąd. Jest to funkcja systemu Windows NT 4.0 (i nowszych).

Jeśli sieć jest określona, system operacyjny najpierw skopiować obraz binarny z sieci do pliku wymiany i załadować je stamtąd. Ta opcja jest przydatna do uruchamiania aplikacji za pośrednictwem sieci. Gdy dysk CD zostanie określony, system operacyjny skopiuje obraz na dysku wymiennym do pliku stronicowania, a następnie ładowania ich.

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Aby ustawić tę opcję konsolidatora w środowisku programowania Visual Studio

1. Otwórz projekt **stron właściwości** okno dialogowe. Aby uzyskać więcej informacji, zobacz [ustawienie właściwości projektu Visual C++](../../ide/working-with-project-properties.md).

1. Kliknij przycisk **konsolidatora** folderu.

1. Kliknij przycisk **systemu** stronę właściwości.

1. Zmodyfikuj jedną z następujących właściwości:

   - **Wymienne uruchamianie z dysku CD**

   - **Wymienne uruchamianie z sieci**

### <a name="to-set-this-linker-option-programmatically"></a>Aby programowo ustawić tę opcję konsolidatora

1. Zobacz <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.SwapRunFromCD%2A> i <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.SwapRunFromNet%2A> właściwości.

## <a name="see-also"></a>Zobacz też

[Ustawianie opcji konsolidatora](../../build/reference/setting-linker-options.md)<br/>
[Opcje konsolidatora](../../build/reference/linker-options.md)