---
title: "-WINMDDELAYSIGN (Podpisz częściowo winmd) | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: VC.Project.VCLinkerTool.WINMDDelaySign
dev_langs: C++
ms.assetid: 445cd602-62cb-400a-8e3a-4beb6572724d
caps.latest.revision: "7"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 18f168c9a3faf4a6bc2676e142a35ee6314db391
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="winmddelaysign-partially-sign-a-winmd"></a>/WINMDDELAYSIGN (podpisz częściowo winmd)
Umożliwia częściowe podpisywanie pliku metadanych środowiska wykonawczego systemu Windows (.winmd) poprzez umieszczenie klucza publicznego w pliku.  
  
```  
/WINMDDELAYSIGN[:NO]  
```  
  
## <a name="remarks"></a>Uwagi  
 Podobny [/DelaySign](../../build/reference/delaysign-partially-sign-an-assembly.md) — opcja konsolidatora zastosowanych do pliku winmd. Użyj **opcji/winmddelaysign** Jeśli chcesz umieścić klucz publiczny w pliku winmd. Domyślnie konsolidator działa tak, jakby **/winmddelaysign: No** określono; oznacza to, że nie podpisać plik winmd.  
  
### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Aby ustawić tę opcję konsolidatora w środowisku programowania Visual Studio  
  
1.  Otwórz projekt **strony właściwości** okno dialogowe. Aby uzyskać więcej informacji, zobacz [Praca z właściwościami projektu](../../ide/working-with-project-properties.md).  
  
2.  Wybierz **konsolidatora** folderu.  
  
3.  Wybierz **metadanych systemu Windows** strony właściwości.  
  
4.  W **znak opóźnienia metadanych systemu Windows** listy rozwijanej wybierz odpowiednią opcję.  
  
## <a name="see-also"></a>Zobacz też  
 [Ustawianie opcji konsolidatora](../../build/reference/setting-linker-options.md)   
 [Opcje konsolidatora](../../build/reference/linker-options.md)