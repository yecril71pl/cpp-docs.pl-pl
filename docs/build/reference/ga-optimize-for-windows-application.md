---
title: -GA (Optymalizuj dla aplikacji systemu Windows) | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- VC.Project.VCCLCompilerTool.OptimizeForWindowsApplication
- /ga
dev_langs: C++
helpviewer_keywords:
- /GA compiler option [C++]
- GA compiler option [C++]
- -GA compiler option [C++]
- Optimize for Windows compiler options
ms.assetid: be97323e-15a0-4836-862c-95980b51926a
caps.latest.revision: "10"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 611704120ec99280e0701e06e0e4bd45c95330d4
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="ga-optimize-for-windows-application"></a>/GA (Optymalizuj dla aplikacji systemu Windows)
Wyniki w bardziej wydajny kodu dla pliku .exe do uzyskiwania dostępu do zmiennych lokalny magazyn wątków (TLS).  
  
## <a name="syntax"></a>Składnia  
  
```  
/GA  
```  
  
## <a name="remarks"></a>Uwagi  
 **/GA** szybkość dostępu do danych jest zadeklarowany z [__declspec(thread)](../../cpp/declspec.md) w programie opartych na systemie Windows. Gdy ta opcja jest ustawiona, [__tls_index](http://msdn.microsoft.com/library/windows/desktop/ms686749) makro jest wartość równa 0.  
  
 Przy użyciu **/GA** dla biblioteki DLL może spowodować wygenerowanie złego kodu.  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Aby ustawić tę opcję kompilatora w środowisku programowania Visual Studio  
  
1.  Otwórz projekt **strony właściwości** okno dialogowe. Aby uzyskać więcej informacji, zobacz [Praca z właściwościami projektu](../../ide/working-with-project-properties.md).  
  
2.  Kliknij przycisk **C/C++** folderu.  
  
3.  Kliknij przycisk **wiersza polecenia** strony właściwości.  
  
4.  Typ opcji kompilatora w **dodatkowe opcje** pole.  
  
### <a name="to-set-this-compiler-option-programmatically"></a>Aby programowo ustawić tę opcję kompilatora  
  
-   Zobacz <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>.  
  
## <a name="see-also"></a>Zobacz też  
 [Opcje kompilatora](../../build/reference/compiler-options.md)   
 [Ustawianie opcji kompilatora](../../build/reference/setting-compiler-options.md)