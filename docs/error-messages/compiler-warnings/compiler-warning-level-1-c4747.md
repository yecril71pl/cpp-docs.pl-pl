---
title: "Kompilatora (poziom 1) ostrzeżenie C4747 | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C4747
dev_langs: C++
helpviewer_keywords: C4747
ms.assetid: af37befd-ba1f-4bdc-96e1-a953f7a2ad9c
caps.latest.revision: "10"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 23c0598c97bf0f2ab05169cb7bf72b9efd5a3f7c
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-warning-level-1-c4747"></a>Kompilator C4747 ostrzegawcze (poziom 1)
Wywołanie zarządzanego entrypoint: kodu zarządzanego nie mogą być uruchamiane w obszarze blokady modułu ładującego, włączając punktu wejścia biblioteki DLL i wywołania osiągnięte z punktu wejścia biblioteki DLL  
  
 Kompilator znaleziono skompilowane do MSIL (prawdopodobne) punkt wejścia biblioteki DLL.  Ze względu na potencjalne problemy podczas ładowania biblioteki DLL została skompilowana którego punkt wejścia do MSIL jest zalecane z kompilowanie biblioteki DLL funkcję punktu wejścia do MSIL.  
  
 Aby uzyskać więcej informacji, zobacz [inicjowanie zestawów mieszanych](../../dotnet/initialization-of-mixed-assemblies.md) i [błąd narzędzi konsolidatora LNK1306](../../error-messages/tool-errors/linker-tools-error-lnk1306.md).  
  
### <a name="to-correct-this-error"></a>Aby poprawić ten błąd  
  
1.  Nie Kompiluj moduł **/CLR**.  
  
2.  Oznacz funkcję punktu wejścia z `#pragma unmanaged`.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład generuje C4747.  
  
```  
// C4747.cpp  
// compile with: /clr /c /W1  
// C4747 expected  
#include <windows.h>  
  
// Uncomment the following line to resolve.  
// #pragma unmanaged  
  
BOOL WINAPI DllMain(HANDLE hInstance, ULONG Command, LPVOID Reserved) {  
   return TRUE;  
};  
```