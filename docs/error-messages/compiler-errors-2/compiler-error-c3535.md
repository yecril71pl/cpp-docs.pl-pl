---
title: "C3535 błąd kompilatora | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C3535
dev_langs:
- C++
helpviewer_keywords:
- C3535
ms.assetid: 24449c98-f681-484d-a00b-32533dca3a88
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 5797d644ec13ed89bad3ddcda23be109df067b03
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-error-c3535"></a>C3535 błąd kompilatora
Nie można ustalić typu "type1" z "type2".  
  
 Typ zmiennej zadeklarowanej przez `auto` — słowo kluczowe nie można wywnioskować typu wyrażenia inicjowania. Na przykład ten błąd występuje, jeśli wynikiem obliczenia wyrażenia inicjowania jest `void`, który nie jest typem.  
  
### <a name="to-correct-this-error"></a>Aby poprawić ten błąd  
  
1.  Sprawdź, czy typ wyrażenia inicjowania nie jest `void`.  
  
2.  Upewnij się, że deklaracja nie jest wskaźnikiem do typu podstawowych. Aby uzyskać więcej informacji, zobacz [podstawowych typów](../../cpp/fundamental-types-cpp.md).  
  
3.  Upewnij się, że, jeśli deklaracja jest wskaźnikiem do typu, wyrażenie inicjowania jest typem wskaźnika.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład zwraca C3535, ponieważ inicjowanie wyrażenie ma `void`.  
  
```  
// C3535a.cpp  
// Compile with /Zc:auto  
void f(){}  
int main()  
{  
   auto x = f();   //C3535  
   return 0;  
}  
```  
  
## <a name="example"></a>Przykład  
 Poniższy przykład zwraca C3535, ponieważ instrukcja deklaruje zmienną `x` jako wskaźnik wnioskowanym typem, ale typ inicjatora wyrażenie jest dwa razy. W rezultacie kompilator nie można wywnioskować typu zmiennej.  
  
```  
// C3535b.cpp  
// Compile with /Zc:auto  
int main()  
{  
   auto* x = 123.0;   // C3535  
   return 0;  
}  
```  
  
## <a name="example"></a>Przykład  
 Poniższy przykład zwraca C3535, ponieważ zmienna `p` deklaruje wskaźnik do wnioskowanym typem, ale wyrażenie inicjowania nie jest typem wskaźnika.  
  
```  
// C3535c.cpp  
// Compile with /Zc:auto  
class A { };  
A x;  
auto *p = x;  // C3535  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Auto — słowo kluczowe](../../cpp/auto-keyword.md)   
 [Typy podstawowe](../../cpp/fundamental-types-cpp.md)