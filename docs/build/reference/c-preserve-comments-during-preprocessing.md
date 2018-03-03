---
title: "-C (Zachowaj komentarze podczas przetwarzania wstępnego) | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- VC.Project.VCCLCompilerTool.KeepComments
- /c
- VC.Project.VCCLWCECompilerTool.KeepComments
dev_langs:
- C++
helpviewer_keywords:
- comments, not stripping during preprocessing
- preserve comments during preprocessing
- -c compiler option [C++]
- c compiler option [C++]
- /c compiler option [C++]
ms.assetid: 944567ca-16bc-4728-befe-d414a7787f26
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 6d27e6ed0f6a2ff6e6f63bc1b87522fb598953c2
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="c-preserve-comments-during-preprocessing"></a>/C (Zachowaj komentarze podczas przetwarzania wstępnego)
Zachowanie komentarzy podczas przetwarzania wstępnego.  
  
## <a name="syntax"></a>Składnia  
  
```  
/C  
```  
  
## <a name="remarks"></a>Uwagi  
 Ta opcja kompilatora wymaga **/E**, **/P**, lub **/EP** opcji.  
  
 Poniższy przykładowy kod wyświetli komentarz do kodu źródłowego.  
  
```  
// C_compiler_option.cpp  
// compile with: /E /C /c  
int i;   // a variable  
```  
  
 W tym przykładzie powoduje wygenerowanie następujących danych wyjściowych.  
  
```  
#line 1 "C_compiler_option.cpp"  
int i;   // a variable  
```  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Aby ustawić tę opcję kompilatora w środowisku programowania Visual Studio  
  
1.  Otwórz projekt **strony właściwości** okno dialogowe. Aby uzyskać więcej informacji, zobacz [Praca z właściwościami projektu](../../ide/working-with-project-properties.md).  
  
2.  Kliknij przycisk **C/C++** folderu.  
  
3.  Kliknij przycisk **preprocesora** strony właściwości.  
  
4.  Modyfikowanie **Zachowaj komentarze** właściwości.  
  
### <a name="to-set-this-compiler-option-programmatically"></a>Aby programowo ustawić tę opcję kompilatora  
  
-   Zobacz <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.KeepComments%2A>.  
  
## <a name="see-also"></a>Zobacz też  
 [Opcje kompilatora](../../build/reference/compiler-options.md)   
 [Ustawianie opcji kompilatora](../../build/reference/setting-compiler-options.md)   
 [/E (Przetwarzaj wstępnie do stdout)](../../build/reference/e-preprocess-to-stdout.md)   
 [/P (Przetwarzaj wstępnie do pliku)](../../build/reference/p-preprocess-to-a-file.md)   
 [/EP (Wstępnie przetwórz do stdout bez dyrektyw #line)](../../build/reference/ep-preprocess-to-stdout-without-hash-line-directives.md)