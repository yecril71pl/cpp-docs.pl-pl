---
title: -LARGEADDRESSAWARE (Obsługa dużych adresów) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- VC.Project.VCLinkerTool.LargeAddressAware
- /largeaddressaware
dev_langs:
- C++
helpviewer_keywords:
- LARGEADDRESSAWARE linker option
- -LARGEADDRESSAWARE linker option
- /LARGEADDRESSAWARE linker option
ms.assetid: a29756c8-e893-47a9-9750-1f0d25359385
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 4f81424c49c5d67713cf478f69701c52504cfa8c
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
---
# <a name="largeaddressaware-handle-large-addresses"></a>/LARGEADDRESSAWARE (Obsługa dużych adresów)
```  
/LARGEADDRESSAWARE[:NO]  
```  
  
## <a name="remarks"></a>Uwagi  
 Opcja/largeaddressaware informuje konsolidator, że aplikacja może obsługiwać adresy większe niż 2 gigabajty. W kompilatory 64-bitowych ta opcja jest włączona domyślnie. W kompilatory 32-bitowe: no jest włączona, jeśli opcja/largeaddressaware nie jest określona inaczej w linii konsolidatora.  
  
 Jeśli aplikacja został połączony z/largeaddressaware, DUMPBIN [/HEADERS](../../build/reference/headers.md) spowoduje wyświetlenie informacji w tym celu.  
  
### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Aby ustawić tę opcję konsolidatora w środowisku programowania Visual Studio  
  
1.  Otwórz projekt **strony właściwości** okno dialogowe. Aby uzyskać więcej informacji, zobacz [Ustawianie właściwości projektu Visual C++](../../ide/working-with-project-properties.md).  
  
2.  Kliknij przycisk **konsolidatora** folderu.  
  
3.  Kliknij przycisk **systemu** strony właściwości.  
  
4.  Modyfikowanie **Włącz duże adresy** właściwości.  
  
### <a name="to-set-this-linker-option-programmatically"></a>Aby programowo ustawić tę opcję konsolidatora  
  
-   Zobacz <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.LargeAddressAware%2A>.  
  
## <a name="see-also"></a>Zobacz też  
 [Ustawianie opcji konsolidatora](../../build/reference/setting-linker-options.md)   
 [Opcje konsolidatora](../../build/reference/linker-options.md)