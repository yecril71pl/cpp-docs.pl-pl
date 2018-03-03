---
title: "-NOENTRY (Brak punktu wejścia) | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- VC.Project.VCLinkerTool.ResourceOnlyDLL
- /noentry
dev_langs:
- C++
helpviewer_keywords:
- entry points [C++], linker specifying
- -NOENTRY linker option
- resource-only DLLs [C++], creating
- NOENTRY linker option
- /NOENTRY linker option [C++]
- DLLs [C++], creating
ms.assetid: 0214dd41-35ad-43ab-b892-e636e038621a
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 5990123d809a5fdaa00e3fd44666dd3fc37c69bf
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="noentry-no-entry-point"></a>/NOENTRY (Brak punktu wejścia)
```  
/NOENTRY  
```  
  
## <a name="remarks"></a>Uwagi  
 Opcja/noentry jest wymagana do tworzenia tylko zasobów DLL, która nie zawiera kodu wykonywalnego. Aby uzyskać więcej informacji, zobacz [Tworzenie biblioteki DLL Resource-Only](../../build/creating-a-resource-only-dll.md).  
  
 Użyj tej opcji, aby zapobiegać łączeniu odwołania do `_main` w bibliotece DLL.  
  
### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Aby ustawić tę opcję konsolidatora w środowisku programowania Visual Studio  
  
1.  Otwórz projekt **strony właściwości** okno dialogowe. Aby uzyskać więcej informacji, zobacz [Ustawianie właściwości projektu Visual C++](../../ide/working-with-project-properties.md).  
  
2.  Wybierz **konsolidatora** folderu.  
  
3.  Wybierz **zaawansowane** strony właściwości.  
  
4.  Modyfikowanie **punkt wejścia nie** właściwości.  
  
### <a name="to-set-this-linker-option-programmatically"></a>Aby programowo ustawić tę opcję konsolidatora  
  
1.  Zobacz <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.ResourceOnlyDLL%2A>.  
  
## <a name="see-also"></a>Zobacz też  
 [Tworzenie biblioteki DLL tylko z zasobami](../../build/creating-a-resource-only-dll.md)   
 [Ustawianie opcji konsolidatora](../../build/reference/setting-linker-options.md)   
 [Opcje konsolidatora](../../build/reference/linker-options.md)