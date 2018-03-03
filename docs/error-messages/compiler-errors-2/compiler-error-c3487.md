---
title: "Błąd kompilatora C3487 | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C3487
dev_langs:
- C++
helpviewer_keywords:
- C3487
ms.assetid: 39bda474-4418-4a79-98bf-2b22fa92eaaa
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 566f130e3d65826feecc02afae0cc1a7db335efe
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-error-c3487"></a>Błąd kompilatora C3487
"typ zwracany": zwraca wszystkie wyrażenia muszą być ustalane do tego samego typu: poprzednio był "typ zwracany"  
  
 Wyrażenie lambda musi określić jej typu zwracanego, chyba że zawiera on pojedyncza instrukcja return. Jeśli wyrażenie lambda zawiera wiele instrukcji "return", ich muszą mieć tego samego typu.  
  
### <a name="to-correct-this-error"></a>Aby poprawić ten błąd  
  
-   Określ końcowy typ zwracany dla lambda. Sprawdź, czy wszystkie zwraca z lambda są tego samego typu, lub można niejawnie przekonwertować na typ zwracany.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład generuje C3487, ponieważ typy zwracane wyrażenie lambda nie są zgodne:  
  
```  
// C3487.cpp  
// Compile by using: cl /c /W4 C3487.cpp  
  
int* test(int* pi) {  
   // To fix the error, uncomment the trailing return type below  
   auto odd_pointer = [=]() /* -> int* */ {  
      if (*pi % 2)   
         return pi;  
      return nullptr; // C3487 - nullptr is not an int* type  
   };  
   return odd_pointer();  
}  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Wyrażenia lambda](../../cpp/lambda-expressions-in-cpp.md)