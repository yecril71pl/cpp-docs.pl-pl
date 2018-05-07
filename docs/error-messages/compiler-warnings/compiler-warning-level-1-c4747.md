---
title: Kompilatora (poziom 1) ostrzeżenie C4747 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4747
dev_langs:
- C++
helpviewer_keywords:
- C4747
ms.assetid: af37befd-ba1f-4bdc-96e1-a953f7a2ad9c
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 203943f3741d07e278652a7032a6dcdcb305a384
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
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