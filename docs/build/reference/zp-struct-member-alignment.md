---
title: "-Zp (wyrównanie członka struktury) | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- /zp
- VC.Project.VCCLCompilerTool.StructMemberAlignment
- VC.Project.VCCLWCECompilerTool.StructMemberAlignment
dev_langs:
- C++
helpviewer_keywords:
- Struct Member Alignment compiler option
- Zp compiler option
- /Zp compiler option [C++]
- -Zp compiler option [C++]
ms.assetid: 5242f656-ed9b-48a3-bc73-cfcf3ed2520f
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 4d387e0ab020e96afb3e2975b5c8686b668cbc10
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="zp-struct-member-alignment"></a>/Zp (Wyrównanie członka struktury)
Określa, jak elementy członkowskie struktury są pakować do pamięci i umożliwia określenie tej samej pakowania dla wszystkich elementów w module.  
  
## <a name="syntax"></a>Składnia  
  
```  
/Zp[1|2|4|8|16]  
```  
  
## <a name="remarks"></a>Uwagi  
 Po określeniu tej opcji, każdy element członkowski struktury po pierwszym jest przechowywany na rozmiar typ elementu członkowskiego lub `n`-bajtowych granicach (gdzie `n` jest 1, 2, 4, 8 lub 16), w zależności od jest mniejsza.  
  
 Dostępne wartości są opisane w poniższej tabeli.  
  
 1  
 Struktury pakietów przy 1-bajtowych granicach. Taki sam jak **/Zp**.  
  
 2  
 Struktury pakietów przy 2-bajtowych granicach.  
  
 4  
 Struktury pakietów przy 4-bajtowych granicach.  
  
 8  
 Struktury pakietów przy 8-bajtowych granicach (domyślnie).  
  
 16  
 Struktury pakietów przy 16-bajtowych granicach.  
  
 Nie należy używać tej opcji, jeśli nie ma wyraźnego związku wymagania.  
  
 Można również użyć [pakietu](../../preprocessor/pack.md) na pakowanie struktury formantu. Aby uzyskać więcej informacji na temat wyrównania zobacz:  
  
-   [Dopasuj](../../cpp/align-cpp.md)  
  
-   [Operator __alignof](../../cpp/alignof-operator.md)  
  
-   [__unaligned](../../cpp/unaligned.md)  
  
-   [Przykłady wyrównania struktury](../../build/examples-of-structure-alignment.md) (x64 określonych)  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Aby ustawić tę opcję kompilatora w środowisku programowania Visual Studio  
  
1.  Otwórz projekt **strony właściwości** okno dialogowe. Aby uzyskać więcej informacji, zobacz [Praca z właściwościami projektu](../../ide/working-with-project-properties.md).  
  
2.  Kliknij przycisk **C/C++** folderu.  
  
3.  Kliknij przycisk **generowania kodu** strony właściwości.  
  
4.  Modyfikowanie **wyrównanie członka struktury** właściwości.  
  
### <a name="to-set-this-compiler-option-programmatically"></a>Aby programowo ustawić tę opcję kompilatora  
  
-   Zobacz <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.StructMemberAlignment%2A>.  
  
## <a name="see-also"></a>Zobacz też  
 [Opcje kompilatora](../../build/reference/compiler-options.md)   
 [Ustawianie opcji kompilatora](../../build/reference/setting-compiler-options.md)