---
title: Ustawianie opcji kompilatora | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- compiler options, setting
- cl.exe compiler, setting options
ms.assetid: 4b079f5b-0017-4124-aad6-0d2b58e427e0
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: dbbc7111ceae2353e8bc9820ead319556ce0016b
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="setting-compiler-options"></a>Ustawianie opcji kompilatora
Opcje kompilatora C i C++ można ustawić w środowisku programistycznym lub w wierszu polecenia.  
  
## <a name="in-the-development-environment"></a>W środowisku programistycznym  
 Można ustawić opcje kompilatora dla każdego projektu w jego **strony właściwości** okno dialogowe. W okienku po lewej stronie wybierz **właściwości konfiguracji**, **C/C++** , a następnie wybierz kategorię — opcja kompilatora. Temat dla każdej opcji kompilatora opisuje, jak ją można ustawić i gdzie występuje w środowisku programistycznym. Zobacz [— opcje kompilatora](../../build/reference/compiler-options.md) pełną listę.  
  
## <a name="outside-the-development-environment"></a>Poza środowiskiem programistycznym  
 Można ustawić opcje kompilatora (CL.exe):  
  
-   [W wierszu polecenia](../../build/reference/compiler-command-line-syntax.md)  
  
-   [W plikach polecenia](../../build/reference/cl-command-files.md)  
  
-   [W zmiennej środowiskowej CL](../../build/reference/cl-environment-variables.md)  
  
 Opcje określone w zmiennej środowiskowej CL są używane za każdym razem, gdy wywołuje się CL. Jeśli plik poleceń jest podany w zmiennej środowiskowej CL lub w wierszu polecenia, używane są opcje określone w pliku poleceń. W przeciwieństwie do wiersza polecenia lub zmiennej środowiskowej CL, plik poleceń pozwala na używanie wielu wierszy opcji i nazw plików.  
  
 Opcje kompilatora są przetwarzane „od lewej do prawej,” a w przypadku wykrycia konfliktu pierwszeństwo ma ostatnia opcja (najdalej po prawej stronie). Zmienna środowiskowa CL jest przetwarzana przed wierszem polecenia, więc w każdym konflikcie między CL i wierszem polecenia ten ostatni ma pierwszeństwo.  
  
## <a name="additional-compiler-topics"></a>Tematy dodatkowe kompilatora  
  
-   [Szybka kompilacja](../../build/reference/fast-compilation.md)  
  
-   [CL wywołuje konsolidator](../../build/reference/cl-invokes-the-linker.md)  
  
## <a name="see-also"></a>Zobacz też  
 [Odwołanie kompilacji C/C++](../../build/reference/c-cpp-building-reference.md)   
 [Opcje kompilatora](../../build/reference/compiler-options.md)