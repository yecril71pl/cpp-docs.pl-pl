---
title: "-FI (nazwa pliku wymuszonego dołączenia) | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- VC.Project.VCNMakeTool.ForcedIncludes
- VC.Project.VCCLCompilerTool.ForcedIncludeFiles
- VC.Project.VCCLWCECompilerTool.ForcedIncludeFiles
- /fi
dev_langs:
- C++
helpviewer_keywords:
- FI compiler option [C++]
- -FI compiler option [C++]
- /FI compiler option [C++]
- preprocess header file compiler option [C++]
ms.assetid: 07e79577-8152-4df9-a64c-aae08c603397
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 3b2003ab35bf76a8ac3e70288576af821a6c8e6d
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="fi-name-forced-include-file"></a>/FI (Nazwa pliku wymuszonego dołączenia)
Powoduje, że preprocesora do przetworzenia określonego pliku nagłówka.  
  
## <a name="syntax"></a>Składnia  
  
```  
/FI[ ]pathname  
```  
  
## <a name="remarks"></a>Uwagi  
 Ta opcja działa tak samo jak określenie podwójny cudzysłów w pliku `#include` dyrektywy w pierwszym wierszu pliku źródłowego, co określona w wierszu polecenia, w zmiennej środowiskowej CL lub w pliku poleceń. Jeśli używasz wielu **/FI** opcje plików znajdują się w kolejności, są przetwarzane przez CL.  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Aby ustawić tę opcję kompilatora w środowisku programowania Visual Studio  
  
1.  Otwórz projekt **strony właściwości** okno dialogowe. Aby uzyskać więcej informacji, zobacz [Praca z właściwościami projektu](../../ide/working-with-project-properties.md).  
  
2.  Kliknij przycisk **C/C++** folderu.  
  
3.  Kliknij przycisk **zaawansowane** strony właściwości.  
  
4.  Modyfikowanie **życie obejmuje** właściwości.  
  
### <a name="to-set-this-compiler-option-programmatically"></a>Aby programowo ustawić tę opcję kompilatora  
  
-   Zobacz <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.ForcedIncludeFiles%2A>.  
  
## <a name="see-also"></a>Zobacz też  
 [Plik wyjściowy (/ F) opcje](../../build/reference/output-file-f-options.md)   
 [Opcje kompilatora](../../build/reference/compiler-options.md)   
 [Ustawianie opcji kompilatora](../../build/reference/setting-compiler-options.md)   
 [Określanie nazwy ścieżki](../../build/reference/specifying-the-pathname.md)