---
title: "Określanie bibliotek DLL w celu opóźnienia ładowania | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- DELAYLOAD linker option
- delayed loading of DLLs
- delayed loading of DLLs, specifying
- /DELAYLOAD linker option
ms.assetid: 94cbecfe-7a42-40d1-a618-9f2786bac0d8
caps.latest.revision: "8"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: bfa7eb3c862c1ce5d1ed356ddd89c51ebff95860
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="specifying-dlls-to-delay-load"></a>Określanie bibliotek DLL w celu opóźnienia ładowania
Można określić, które biblioteki dll w celu opóźnienia ładowania z [/delayload](../../build/reference/delayload-delay-load-import.md):`dllname` — opcja konsolidatora. Jeśli nie planujesz używać wersji funkcji pomocnika, możesz również połączyć program delayimp.lib (w przypadku aplikacji klasycznych) lub dloadhelper.lib (dla aplikacji ze sklepu).  
  
 Poniżej przedstawiono prosty przykład biblioteki DLL ładowanych z opóźnieniem:  
  
```  
// cl t.cpp user32.lib delayimp.lib  /link /DELAYLOAD:user32.dll  
#include <windows.h>  
// uncomment these lines to remove .libs from command line  
// #pragma comment(lib, "delayimp")  
// #pragma comment(lib, "user32")  
  
int main() {  
   // user32.dll will load at this point  
   MessageBox(NULL, "Hello", "Hello", MB_OK);  
}  
```  
  
 Tworzenie wersji do debugowania projektu. Krok za pomocą kodu za pomocą debugera i zauważyć, że user32.dll jest załadowany tylko wtedy, gdy wywołanie `MessageBox`.  
  
## <a name="see-also"></a>Zobacz też  
 [Obsługa konsolidatora dla bibliotek DLL załadowanych z opóźnieniem](../../build/reference/linker-support-for-delay-loaded-dlls.md)