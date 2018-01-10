---
title: "-Od (Wyłącz (Debuguj)) | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: /od
dev_langs: C++
helpviewer_keywords:
- no optimizations
- fast compiling
- /Od compiler option [C++]
- disable optimizations
- Od compiler option [C++]
- -Od compiler option [C++]
- disable (debug) compiler option [C++]
ms.assetid: b1ac31b7-e086-4eeb-be5e-488f7513f5f5
caps.latest.revision: "13"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 0956493184f6c2322bc6838049472e90ad0c1985
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="od-disable-debug"></a>/Od (Wyłącz (Debuguj))
Wyłącza wszystkie optymalizacje w programie i szybkości kompilacji.  
  
## <a name="syntax"></a>Składnia  
  
```  
/Od  
```  
  
## <a name="remarks"></a>Uwagi  
 Ta opcja jest domyślnie. Ponieważ **/Od** pomija przepływu kodu takie rozwiązanie upraszcza proces debugowania. Aby uzyskać więcej informacji o opcjach kompilatora debugowania, zobacz [/z7, / zi, /ZI (Format informacji debugowania)](../../build/reference/z7-zi-zi-debug-information-format.md).  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Aby ustawić tę opcję kompilatora w środowisku programowania Visual Studio  
  
1.  Otwórz projekt **strony właściwości** okno dialogowe. Aby uzyskać więcej informacji, zobacz [Praca z właściwościami projektu](../../ide/working-with-project-properties.md).  
  
2.  Kliknij przycisk **C/C++** folderu.  
  
3.  Kliknij przycisk **optymalizacji** strony właściwości.  
  
4.  Modyfikowanie **optymalizacji** właściwości.  
  
### <a name="to-set-this-compiler-option-programmatically"></a>Aby programowo ustawić tę opcję kompilatora  
  
-   Zobacz <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.Optimization%2A>.  
  
## <a name="see-also"></a>Zobacz też  
 [/O opcje (Optymalizuj kod)](../../build/reference/o-options-optimize-code.md)   
 [Opcje kompilatora](../../build/reference/compiler-options.md)   
 [Ustawianie opcji kompilatora](../../build/reference/setting-compiler-options.md)   
 [/ Z7, / zi, /ZI (Format informacji o debugowaniu)](../../build/reference/z7-zi-zi-debug-information-format.md)