---
title: C2472 błąd kompilatora | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2472
dev_langs:
- C++
helpviewer_keywords:
- C2472
ms.assetid: 3b36bcdc-2ba5-4357-ab88-7545ba0551cd
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: d89a6d6b10fa76c7fbf1bf11c4ebe2ecff5f98ba
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
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
 [/clr (Kompilacja środowiska uruchomieniowego języka wspólnego)](../../build/reference/clr-common-language-runtime-compilation.md)