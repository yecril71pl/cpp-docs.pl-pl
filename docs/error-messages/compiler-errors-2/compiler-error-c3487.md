---
title: Błąd kompilatora C3487 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3487
dev_langs:
- C++
helpviewer_keywords:
- C3487
ms.assetid: 39bda474-4418-4a79-98bf-2b22fa92eaaa
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: eb30b9a2cb0b77eff0888da6c387bd3b06182721
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
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