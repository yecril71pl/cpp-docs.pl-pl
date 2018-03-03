---
title: "-DELAYLOAD (Opóźnij importowanie ładowania) | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- /delayload
- VC.Project.VCLinkerTool.DelayLoadDLLS
dev_langs:
- C++
helpviewer_keywords:
- DELAYLOAD linker option
- -DELAYLOAD linker option
- /DELAYLOAD linker option
- delayed loading of DLLs, /DELAYLOAD option
ms.assetid: 39ea0f1e-5c01-450f-9c75-2d9761ff9b28
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 4fd524e72125408c6a88bea83272e18a7ef9b78d
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="delayload-delay-load-import"></a>/DELAYLOAD (Opóźnij importowanie ładowania)
```  
/DELAYLOAD:dllname  
```  
  
## <a name="parameters"></a>Parametry  
 `dllname`  
 Nazwa biblioteki DLL, który ma zostać opóźnienia ładowania.  
  
## <a name="remarks"></a>Uwagi  
 Opcja/delayload powoduje, że biblioteki DLL, która jest określona przez `dllname` można załadować wyłącznie przy pierwszym wywołaniu przez program do funkcji w tej bibliotece DLL. Aby uzyskać więcej informacji, zobacz [Obsługa konsolidatora dla bibliotek DLL Delay-Loaded](../../build/reference/linker-support-for-delay-loaded-dlls.md). Tę opcję wiele razy umożliwia określić dowolną liczbę bibliotek DLL, wybierz polecenie. Należy użyć Delayimp.lib podczas łączenia z programem lub można zaimplementować własnej funkcji Pomocnik załadować z opóźnieniem.  
  
 [/DELAY](../../build/reference/delay-delay-load-import-settings.md) opcja określa powiązania i Trwa ładowanie opcji dla każdej biblioteki DLL załadowanych z opóźnieniem.  
  
### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Aby ustawić tę opcję konsolidatora w środowisku programowania Visual Studio  
  
1.  Otwórz projekt **strony właściwości** okno dialogowe. Aby uzyskać więcej informacji, zobacz [Praca z właściwościami projektu](../../ide/working-with-project-properties.md).  
  
2.  W **konsolidatora** folderu, wybierz opcję **dane wejściowe** strony właściwości.  
  
3.  Modyfikowanie **bibliotek DLL załadowanych z opóźnieniem** właściwości.  
  
### <a name="to-set-this-linker-option-programmatically"></a>Aby programowo ustawić tę opcję konsolidatora  
  
-   Zobacz <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.DelayLoadDLLs%2A>.  
  
## <a name="see-also"></a>Zobacz też  
 [Ustawianie opcji konsolidatora](../../build/reference/setting-linker-options.md)   
 [Opcje konsolidatora](../../build/reference/linker-options.md)