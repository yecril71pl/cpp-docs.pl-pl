---
title: -Gy (włączenie łączenia poziomie funkcji) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-tools
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- VC.Project.VCCLCompilerTool.EnableFunctionLevelLinking
- /gy
- VC.Project.VCCLWCECompilerTool.EnableFunctionLevelLinking
dev_langs:
- C++
helpviewer_keywords:
- enable function-level linking compiler option [C++]
- COMDAT function
- Gy compiler option [C++]
- -Gy compiler option [C++]
- /Gy compiler option [C++]
- packaged functions
ms.assetid: 0d3cf14c-ed7d-4ad3-b4b6-104e56f61046
caps.latest.revision: 17
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: ebe272b12a503a310319526f53f312a033a0ee26
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="gy-enable-function-level-linking"></a>/Gy (Włączenie łączenia na poziomie funkcji)
Umożliwia kompilatorowi pakowanie indywidualnych funkcji w formę spakowanych funkcji (Comdat).  
  
## <a name="syntax"></a>Składnia  
  
```  
/Gy[-]  
```  
  
## <a name="remarks"></a>Uwagi  
 Konsolidator wymaga, aby funkcje oddzielnie umieszczone jako Comdat wykluczyć lub pojedynczych funkcji w pliku DLL lub .exe kolejność.  
  
 Opcja konsolidatora [(optymalizacje) od](../../build/reference/opt-optimizations.md) do wykluczenia nieużywane spakowanych funkcji z pliku .exe.  
  
 Opcja konsolidatora [/order (Put funkcje w kolejności)](../../build/reference/order-put-functions-in-order.md) uwzględnienie spakowanych funkcji w kolejności określonej w pliku .exe.  
  
 Wbudowane funkcje zawsze są dostarczane, jeśli są one tworzone jako wywołania (co ma miejsce, na przykład, jeśli ze śródwierszowaniem jest wyłączone lub podjąć adresu funkcji). Ponadto funkcji Członkowskich C++, zdefiniowane w deklaracji klasy automatycznie pakiecie; nie są inne funkcje, i wybranie tej opcji jest wymagany do kompilacji je jako spakowanych funkcji.  
  
> [!NOTE]
>  [/Zi](../../build/reference/z7-zi-zi-debug-information-format.md) , używane Edytuj i Kontynuuj, powoduje **/Gy** opcji.  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Aby ustawić tę opcję kompilatora w środowisku programowania Visual Studio  
  
1.  Otwórz projekt **strony właściwości** okno dialogowe. Aby uzyskać więcej informacji, zobacz [Praca z właściwościami projektu](../../ide/working-with-project-properties.md).  
  
2.  Kliknij przycisk **C/C++** folderu.  
  
3.  Kliknij przycisk **generowania kodu** strony właściwości.  
  
4.  Modyfikowanie **włączyć konsolidacje poziomu funkcji** właściwości.  
  
### <a name="to-set-this-compiler-option-programmatically"></a>Aby programowo ustawić tę opcję kompilatora  
  
-   Zobacz <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.EnableFunctionLevelLinking%2A>.  
  
## <a name="see-also"></a>Zobacz też  
 [Opcje kompilatora](../../build/reference/compiler-options.md)   
 [Ustawianie opcji kompilatora](../../build/reference/setting-compiler-options.md)