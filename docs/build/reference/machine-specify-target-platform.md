---
title: "-MACHINE (Określ platformę docelową) | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- VC.Project.VCLinkerTool.TargetMachine
- /machine
dev_langs: C++
helpviewer_keywords:
- mapfiles, creating linker
- target platform
- -MACHINE linker option
- /MACHINE linker option
- MACHINE linker option
ms.assetid: 8d41bf4b-7e53-4ab9-9085-d852b08d31c2
caps.latest.revision: "11"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: edc3f4dc590ed5a8a763a4289fc5e15d8529e313
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="machine-specify-target-platform"></a>/MACHINE (Określ platformę docelową)
```  
/MACHINE:{ARM|EBC|X64|X86}  
```  
  
## <a name="remarks"></a>Uwagi  
 Opcja/Machine Określa docelową platformę dla programu.  
  
 Zwykle nie trzeba określić opcję/Machine. ŁĄCZE wnioskuje typ maszyny z plików .obj. Jednak w niektórych sytuacjach łącze nie można ustalić typu maszyny i problemy [narzędzi konsolidatora LNK1113 błąd](../../error-messages/tool-errors/linker-tools-error-lnk1113.md). Jeśli takie wystąpienie błędu, należy określić/Machine.  
  
### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Aby ustawić tę opcję konsolidatora w środowisku programowania Visual Studio  
  
1.  Otwórz projekt **strony właściwości** okno dialogowe. Aby uzyskać więcej informacji, zobacz [Ustawianie właściwości projektu Visual C++](../../ide/working-with-project-properties.md).  
  
2.  Kliknij przycisk **konsolidatora** folderu.  
  
3.  Kliknij przycisk **zaawansowane** strony właściwości.  
  
4.  Modyfikowanie **maszyny docelowej** właściwości.  
  
### <a name="to-set-this-linker-option-programmatically"></a>Aby programowo ustawić tę opcję konsolidatora  
  
1.  Zobacz <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.TargetMachine%2A>.  
  
## <a name="see-also"></a>Zobacz też  
 [Ustawianie opcji konsolidatora](../../build/reference/setting-linker-options.md)   
 [Opcje konsolidatora](../../build/reference/linker-options.md)