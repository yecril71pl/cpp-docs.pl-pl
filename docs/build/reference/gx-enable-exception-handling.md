---
title: "-GX (Włącz obsługę wyjątków) | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- /gx
dev_langs:
- C++
helpviewer_keywords:
- exception handling, enabling
- /GX compiler option [C++]
- -GX compiler option [C++]
- cl.exe compiler, exception handling
- enable exception handling compiler option [C++]
- GX compiler option [C++]
ms.assetid: 933b43ba-de77-4ff8-a48b-7074de90bc1c
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 3013b4233621e63de0230e088dfc10ff65a5705d
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="gx-enable-exception-handling"></a>/GX (Włącz obsługę wyjątków)
Przestarzałe. Umożliwia synchroniczne wyjątków przy założeniu, że funkcje zadeklarowana przy użyciu `extern "C"` nigdy nie zgłaszają wyjątków.  
  
## <a name="syntax"></a>Składnia  
  
```  
/GX  
```  
  
## <a name="remarks"></a>Uwagi  
 **/GX** jest przestarzały. Użyj odpowiednikiem [/ehsc](../../build/reference/eh-exception-handling-model.md) zamiast tego należy. Listę opcji kompilatora przestarzałe, zobacz **uznane za przestarzałe i usunąć — opcje kompilatora** sekcji [kompilatora opcje rozbiciu na kategorie](../../build/reference/compiler-options-listed-by-category.md).  
  
 Domyślnie **/ehsc**, odpowiednik **/GX**, są włączone podczas kompilowania przy użyciu środowiska programistycznego Visual Studio. Podczas korzystania z narzędzi wiersza polecenia, nie obsługi wyjątków jest określona. Jest to równoważne z **/GX-**.  
  
 Aby uzyskać więcej informacji, zobacz [Obsługa wyjątków języka C++](../../cpp/cpp-exception-handling.md).  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Aby ustawić tę opcję kompilatora w środowisku programowania Visual Studio  
  
1.  Otwórz projekt **strony właściwości** okno dialogowe. Aby uzyskać więcej informacji, zobacz [Praca z właściwościami projektu](../../ide/working-with-project-properties.md).  
  
2.  W okienku nawigacji wybierz **właściwości konfiguracji**, **C/C++**, **wiersza polecenia**.  
  
3.  Typ opcji kompilatora w **dodatkowe opcje** pole.  
  
### <a name="to-set-this-compiler-option-programmatically"></a>Aby programowo ustawić tę opcję kompilatora  
  
-   Zobacz <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>.  
  
## <a name="see-also"></a>Zobacz też  
 [Opcje kompilatora](../../build/reference/compiler-options.md)   
 [Ustawianie opcji kompilatora](../../build/reference/setting-compiler-options.md)   
 [/EH (Model obsługi wyjątku)](../../build/reference/eh-exception-handling-model.md)