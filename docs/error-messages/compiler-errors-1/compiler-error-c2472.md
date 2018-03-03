---
title: "C2472 błąd kompilatora | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- C2472
dev_langs:
- C++
helpviewer_keywords:
- C2472
ms.assetid: 3b36bcdc-2ba5-4357-ab88-7545ba0551cd
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 5267f20aaed4ebf1c320d3d960684376e29814ad
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-error-c2472"></a>C2472 błąd kompilatora
"Funkcja" nie można wygenerować w zarządzanym kodzie: "komunikatu"; Kompiluj z/CLR aby wygenerować mieszany obraz  
  
 Ten błąd wystąpi, gdy typy nie są obsługiwane przez kod zarządzany są używane w środowisku czystego środowiska uruchomieniowego (języka wspólnego CLR) języka wspólnego. Kompiluj z użyciem **/CLR** Aby rozwiązać problem.  
  
 **/CLR: pure** i **/CLR: Safe** — opcje kompilatora zostały uznane za przestarzałe w programie Visual Studio 2015.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład generuje C2472.  
  
```  
// C2472.cpp  
// compile with: /clr:pure  
// C2472 expected  
  
#include <cstdlib>  
  
int main()  
{  
   int * __ptr32 p32;  
   int * __ptr64 p64;  
  
   p32 = (int * __ptr32)malloc(4);  
   p64 = p32;  
}  
```  
  
## <a name="see-also"></a>Zobacz też  
 [/ CLR (kompilacja języka wspólnego środowiska wykonawczego)](../../build/reference/clr-common-language-runtime-compilation.md)