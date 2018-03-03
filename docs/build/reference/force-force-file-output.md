---
title: "-FORCE (Wymuszaj produkt wyjściowy pliku) | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- VC.Project.VCLinkerTool.ForceLink
- /force
dev_langs:
- C++
helpviewer_keywords:
- FORCE linker option
- file output in linker
- /FORCE linker option
- -FORCE linker option
ms.assetid: b1e9a218-a5eb-4e60-a4a4-65b4be15e5da
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 8ec19beec52a217df1237de41d0bd81ab447a56d
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="force-force-file-output"></a>/FORCE (Wymuszaj produkt wyjściowy pliku)
```  
/FORCE:[MULTIPLE|UNRESOLVED]  
```  
  
## <a name="remarks"></a>Uwagi  
 Opcja/Force informuje konsolidator, aby utworzył plik .exe prawidłowy lub biblioteki DLL nawet, jeśli symbol jest odwołania, a nie zdefiniowano lub wielokrotnie zdefiniowane.  
  
 Opcja/Force może zająć opcjonalny argument:  
  
-   Użyj /FORCE:MULTIPLE, aby utworzyć plik wyjściowy, czy Konsolidacja znajduje więcej niż jedną definicję symbolu.  
  
-   Użyj opcji/Force: UNRESOLVED, aby utworzyć plik wyjściowy, czy Konsolidacja znajdzie Niezdefiniowany symbol. / FORCE: NIEROZPOZNANY jest ignorowana, jeśli symbol punktu wejścia nie został rozpoznany.  
  
 / FORCE bez argumentów oznacza zarówno wielokrotne, nierozwiązany.  
  
 Plik utworzony przy użyciu tej opcji może nie działać zgodnie z oczekiwaniami. Konsolidator nie będzie łącz stopniowo, gdy określona jest opcja/Force.  
  
 Jeśli moduł został skompilowany przy **/CLR**, **/FORCE** nie utworzy obrazie.  
  
### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Aby ustawić tę opcję konsolidatora w środowisku programowania Visual Studio  
  
1.  Otwórz projekt **strony właściwości** okno dialogowe. Aby uzyskać więcej informacji, zobacz [Ustawianie właściwości projektu Visual C++](../../ide/working-with-project-properties.md).  
  
2.  Kliknij przycisk **konsolidatora** folderu.  
  
3.  Kliknij przycisk **wiersza polecenia** strony właściwości.  
  
4.  Typ opcji do **dodatkowe opcje** pole.  
  
### <a name="to-set-this-linker-option-programmatically"></a>Aby programowo ustawić tę opcję konsolidatora  
  
-   Zobacz <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.AdditionalOptions%2A>.  
  
## <a name="see-also"></a>Zobacz też  
 [Ustawianie opcji konsolidatora](../../build/reference/setting-linker-options.md)   
 [Opcje konsolidatora](../../build/reference/linker-options.md)