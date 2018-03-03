---
title: "-VERBOSE (Drukuj komunikaty o postępie) | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- /verbose
- VC.Project.VCLinkerTool.ShowProgress
dev_langs:
- C++
helpviewer_keywords:
- -VERBOSE linker option
- linking [C++], session progress information
- Print Progress Messages linker option
- linker [C++], output dependency information
- /VERBOSE linker option
- dependencies [C++], dependency information in linker output
- VERBOSE linker option
ms.assetid: 9c347d98-4c37-4724-a39e-0983934693ab
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 76ead441a8dc7ec65a6966371b83d42c47c897c9
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="verbose-print-progress-messages"></a>/VERBOSE (Drukuj komunikaty o postępie)
```  
/VERBOSE[:{ICF|INCR|LIB|REF|SAFESEH|UNUSEDLIBS}]  
```  
  
## <a name="remarks"></a>Uwagi  
 Konsolidator wysyła informacje o postępie sesji połączeń do **dane wyjściowe** okna. W wierszu polecenia informacje są wysyłane na wyjście standardowe i mogą zostać przekierowane do pliku.  
  
|Opcja|Opis|  
|------------|-----------------|  
|/ VERBOSE|Wyświetla szczegółowe informacje o procesie łączenia.|  
|/ VERBOSE: ICF|Wyświetlanie informacji o działaniu konsolidatora, będącą wynikiem użycia [/OPT: ICF](../../build/reference/opt-optimizations.md).|  
|/ VERBOSE: INCR|Wyświetla informacje o procesie konsolidowania przyrostowego.|  
|/ VERBOSE: LIB|Komunikaty o postępie Wyświetla wskazujące tylko bibliotek przeszukiwane.<br /><br /> Wyświetlane informacje obejmują proces wyszukiwania biblioteki i listy nazwy biblioteki i obiekt (z pełną ścieżką), rozpoznane symbol z biblioteki i listę obiektów, które odwołują się do symbolu.|  
|/ VERBOSE: REF|Wyświetla informacje o działaniu konsolidatora, będącą wynikiem użycia [/OPT:REF](../../build/reference/opt-optimizations.md).|  
|/ VERBOSE: SAFESEH|Wyświetla informacje dotyczące modułów, które nie są zgodne z bezpiecznym wyjątek podczas obsługi [opcja/SAFESEH](../../build/reference/safeseh-image-has-safe-exception-handlers.md) nie jest określona.|  
|/ VERBOSE: UNUSEDLIBS|Wyświetla informacje o plikach wszystkie biblioteki, które nie są używane podczas tworzenia obrazu.|  
  
### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Aby ustawić tę opcję konsolidatora w środowisku programowania Visual Studio  
  
1.  Otwórz projekt **strony właściwości** okno dialogowe. Aby uzyskać więcej informacji, zobacz [Ustawianie właściwości projektu Visual C++](../../ide/working-with-project-properties.md).  
  
2.  Rozwiń węzeł **konsolidatora** folderu.  
  
3.  Wybierz **wiersza polecenia** strony właściwości.  
  
4.  Dodaj opcję **dodatkowe opcje** pole.  
  
### <a name="to-set-this-linker-option-programmatically"></a>Aby programowo ustawić tę opcję konsolidatora  
  
-   Zobacz <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.ShowProgress%2A>.  
  
## <a name="see-also"></a>Zobacz też  
 [Ustawianie opcji konsolidatora](../../build/reference/setting-linker-options.md)   
 [Opcje konsolidatora](../../build/reference/linker-options.md)