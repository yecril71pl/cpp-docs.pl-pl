---
title: "Błąd narzędzi konsolidatora LNK1306 | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: LNK1306
dev_langs: C++
helpviewer_keywords: LNK1306
ms.assetid: fad1df6a-0bd9-412f-b0d1-7c9bc749c584
caps.latest.revision: "11"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: d020d7ca037c737dfb03c32ff2d773730c118311
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="linker-tools-error-lnk1306"></a>Błąd narzędzi konsolidatora LNK1306  
  
> Funkcja punktu wejścia biblioteki DLL nie może być zarządzany; Kompiluj macierzysty  
  
`DllMain`Nie można skompilować do MSIL; musi być skompilowany do natywnego.  
  
Aby rozwiązać ten problem  
  
-   Skompiluj plik zawierający punkt wejścia bez **/CLR**.  
  
-   Umieść punkt wejścia w `#pragma unmanaged` sekcji.  
  
Aby uzyskać więcej informacji, zobacz:  
  
-   [/ CLR (kompilacja języka wspólnego środowiska wykonawczego)](../../build/reference/clr-common-language-runtime-compilation.md)  
  
-   [zarządzane, niezarządzane](../../preprocessor/managed-unmanaged.md)  
  
-   [Inicjalizacja zestawów mieszanych](../../dotnet/initialization-of-mixed-assemblies.md)  
  
-   [Biblioteki dll i zachowanie biblioteki wykonawczej programu Visual C++](../../build/run-time-library-behavior.md)  
  
## <a name="example"></a>Przykład  
  
Poniższy przykład generuje LNK1306.  
  
```cpp  
// LNK1306.cpp  
// compile with: /clr /link /dll /entry:NewDllMain  
// LNK1306 error expected  
#include <windows.h>  
int __stdcall NewDllMain( HINSTANCE h, ULONG ulReason, PVOID pvReserved ) {  
   return 1;  
}  
```  
  
Aby rozwiązać ten problem, nie należy używać opcji/CLR Aby skompilować ten plik, lub użyj `#pragma` dyrektywy, które mają zostać umieszczone w sekcji niezarządzane definicji punktu wejścia, jak pokazano w poniższym przykładzie:  
  
```cpp  
// LNK1306fix.cpp  
// compile with: /clr /link /dll /entry:NewDllMain  
#include <windows.h>  
#pragma managed(push, off)  
int __stdcall NewDllMain( HINSTANCE h, ULONG ulReason, PVOID pvReserved ) {  
   return 1;  
}  
#pragma managed(pop)  
```  
