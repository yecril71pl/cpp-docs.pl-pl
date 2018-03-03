---
title: "-GR (Włącz informacje typu Run-Time) | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- /gr
- VC.Project.VCCLWCECompilerTool.RuntimeTypeInfo
- VC.Project.VCCLCompilerTool.RuntimeTypeInfo
dev_langs:
- C++
helpviewer_keywords:
- -Gr compiler option [C++]
- Gr compiler option [C++]
- RTTI compiler option
- /Gr compiler option [C++]
- enable run-time type information compiler option [C++]
ms.assetid: d1f9f850-dcec-49fd-96ef-e72d01148906
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 993465bd1666e624777e52cb1c3d3a54545589dd
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="gr-enable-run-time-type-information"></a>/GR (Włącz informacje typu Run-Time)
Dodaje kod do sprawdzania typów obiektów w czasie wykonywania.  
  
## <a name="syntax"></a>Składnia  
  
```  
/GR[-]  
```  
  
## <a name="remarks"></a>Uwagi  
 Gdy **GR** jest włączone, kompilator definiuje `_CPPRTTI` makro preprocesora. Domyślnie **GR** znajduje się na. **Czasie** wyłącza informacje typu run-time.  
  
 Użyj **GR** Jeśli kompilator statycznie nie można rozpoznać typu obiektu w kodzie. Zazwyczaj wymaga **GR** podczas używa Twój kod [dynamic_cast Operator](../../cpp/dynamic-cast-operator.md) lub [typeid](../../cpp/typeid-operator.md). Jednak **GR** zwiększa rozmiar sekcji .rdata obrazu. Jeśli nie są używane przez kod **dynamic_cast** lub **typeid**, **czasie** może powodować mniejsze obrazu.  
  
 Aby uzyskać więcej informacji o sprawdzaniu typu run-time, zobacz [informacje typu Run-Time](../../cpp/run-time-type-information.md) w *dokumentacja języka C++*.  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Aby ustawić tę opcję kompilatora w środowisku programowania Visual Studio  
  
1.  Otwórz projekt **strony właściwości** okno dialogowe. Aby uzyskać więcej informacji, zobacz [Praca z właściwościami projektu](../../ide/working-with-project-properties.md).  
  
2.  Kliknij przycisk **C/C++** folderu.  
  
3.  Kliknij przycisk **języka** strony właściwości.  
  
4.  Modyfikowanie **Włącz informacje typu Run-Time** właściwości.  
  
### <a name="to-set-this-compiler-option-programmatically"></a>Aby programowo ustawić tę opcję kompilatora  
  
-   Zobacz <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.RuntimeTypeInfo%2A>.  
  
## <a name="see-also"></a>Zobacz też  
 [Opcje kompilatora](../../build/reference/compiler-options.md)   
 [Ustawianie opcji kompilatora](../../build/reference/setting-compiler-options.md)