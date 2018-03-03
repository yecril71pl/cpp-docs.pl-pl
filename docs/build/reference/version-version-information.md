---
title: -VERSION (informacje o wersji) | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- VC.Project.VCLinkerTool.Version
- /version
dev_langs:
- C++
helpviewer_keywords:
- -VERSION linker option
- Version Information linker option
- version numbers, specifying in .exe
- /VERSION linker option
- VERSION linker option
ms.assetid: b86d0e86-dca6-4316-aee2-d863ccb9f223
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: aeb8d2845c5e8daa931e354b149fc1c35b37fbd7
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="version-version-information"></a>/VERSION (Informacje o wersji)
```  
/VERSION:major[.minor]  
```  
  
## <a name="remarks"></a>Uwagi  
 gdzie:  
  
 *główne*i *pomocnicze*  
 Numer wersji w nagłówku pliku .exe lub .dll.  
  
## <a name="remarks"></a>Uwagi  
 Opcja/Version nakazuje konsolidatorowi umieszczenie numeru wersji w nagłówku pliku .exe lub .dll. Użyj polecenia DUMPBIN [/HEADERS](../../build/reference/headers.md) aby zobaczyć pole wersji obrazu OPCJONALNYCH wartości NAGŁÓWKA, aby zobaczyć efekt opcji/Version.  
  
 *Głównych* i *pomocnicza* argumenty są liczbami dziesiętnymi z zakresu od 0 do 65 535. Wartość domyślna to wersja 0,0.  
  
 Podanych informacji o opcji/Version nie ma wpływu na informacje o wersji, który pojawia się dla aplikacji podczas przeglądania właściwości w Eksploratorze plików. Czy informacje o wersji pochodzą z pliku zasobu, który jest używany do tworzenia aplikacji. Zobacz [Edytor informacji o wersji](../../windows/version-information-editor.md) Aby uzyskać więcej informacji.  
  
 Innym sposobem Wstaw numer wersji jest z [wersji](../../build/reference/version-c-cpp.md) instrukcji definicji modułu.  
  
### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Aby ustawić tę opcję konsolidatora w środowisku programowania Visual Studio  
  
1.  Otwórz projekt **strony właściwości** okno dialogowe. Aby uzyskać więcej informacji, zobacz [Ustawianie właściwości projektu Visual C++](../../ide/working-with-project-properties.md).  
  
2.  Kliknij przycisk **konsolidatora** folderu.  
  
3.  Kliknij przycisk **ogólne** strony właściwości.  
  
4.  Modyfikowanie **wersji** właściwości.  
  
### <a name="to-set-this-linker-option-programmatically"></a>Aby programowo ustawić tę opcję konsolidatora  
  
-   Zobacz <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.Version%2A>.  
  
## <a name="see-also"></a>Zobacz też  
 [Ustawianie opcji konsolidatora](../../build/reference/setting-linker-options.md)   
 [Opcje konsolidatora](../../build/reference/linker-options.md)