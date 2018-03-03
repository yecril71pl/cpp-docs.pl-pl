---
title: "-WINMDFILE (Określ plik winmd) | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- VC.Project.VCLinkerTool.GenerateWindowsMetadataFile
dev_langs:
- C++
ms.assetid: 062b41b3-14d6-432c-a361-fdb66e918931
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 153e5c0bd42b6fdba59e309483f25f09b86fe9fa
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="winmdfile-specify-winmd-file"></a>/WINMDFILE (określ plik winmd)
Określa nazwę pliku dla pliku wyjściowego metadane środowiska wykonawczego systemu Windows (.winmd), który jest generowany przez [/WINMD](../../build/reference/winmd-generate-windows-metadata.md) — opcja konsolidatora.  
  
```  
/WINMDFILE:filename  
```  
  
## <a name="remarks"></a>Uwagi  
 Użyj wartości określonej w `filename` do przesłaniania domyślnej nazwy pliku winmd (`binaryname`winmd). Zwróć uwagę, że nie dodawaj "winmd" do `filename`.  Jeśli wiele wartości nie są wyświetlane na **/WINMDFILE** wiersza polecenia, pierwszeństwo ma ostatnio.  
  
### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Aby ustawić tę opcję konsolidatora w środowisku programowania Visual Studio  
  
1.  Otwórz projekt **strony właściwości** okno dialogowe. Aby uzyskać więcej informacji, zobacz [Praca z właściwościami projektu](../../ide/working-with-project-properties.md).  
  
2.  Wybierz **konsolidatora** folderu.  
  
3.  Wybierz **metadanych systemu Windows** strony właściwości.  
  
4.  W **pliku metadanych systemu Windows** wprowadź lokalizację pliku.  
  
## <a name="see-also"></a>Zobacz też  
 [/ WINMD (Generuj metadane systemu Windows)](../../build/reference/winmd-generate-windows-metadata.md)   
 [Ustawianie opcji konsolidatora](../../build/reference/setting-linker-options.md)   
 [Opcje konsolidatora](../../build/reference/linker-options.md)