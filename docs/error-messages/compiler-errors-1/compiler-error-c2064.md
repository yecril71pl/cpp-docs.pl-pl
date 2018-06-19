---
title: C2064 błąd kompilatora | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2064
dev_langs:
- C++
helpviewer_keywords:
- C2064
ms.assetid: 6cda05da-f437-4f50-9813-ae69538713a3
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: b3e5e21d7c33c84bb531b53c08aefbfce9dc7fd8
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33167284"
---
# <a name="compiler-error-c2064"></a>C2064 błąd kompilatora
termin nie może oszacować biorąc N argumentów funkcji  
  
 Połączenie jest nawiązywane w przypadku funkcji przy użyciu wyrażenia. Wyrażenie nie zwraca wskaźnik do funkcji, która ma określoną liczbę argumentów.  
  
 W tym przykładzie kodu podejmuje próbę wywołania nie działa jako funkcje. Poniższy przykład generuje C2064:  
  
```  
// C2064.cpp  
int i, j;  
char* p;  
void func() {  
   j = i();    // C2064, i is not a function  
   p();        // C2064, p doesn't point to a function  
}  
```  
  
 Wskaźniki do funkcji niestatycznego elementu członkowskiego należy wywołać w kontekście wystąpienia obiektu. Poniższy przykład generuje C2064 i pokazuje, jak rozwiązywanie:  
  
```  
// C2064b.cpp  
struct C {  
   void func1(){}  
   void func2(){}  
};  
  
typedef void (C::*pFunc)();  
  
int main() {  
   C c;  
   pFunc funcArray[2] = {&C::func1, &C::func2};  
   (funcArray[0])();    // C2064   
   (c.*funcArray[0])(); // OK - function called in instance context  
}  
  
```  
  
 W klasie wskaźniki funkcji Członkowskich musi również wskazać kontekst obiektu wywołującego. Poniższy przykład generuje C2064 i pokazuje, jak rozwiązywanie problemu:  
  
```  
// C2064d.cpp  
// Compile by using: cl /c /W4 C2064d.cpp  
struct C {  
   typedef void (C::*pFunc)();  
   pFunc funcArray[2];  
   void func1(){}  
   void func2(){}  
   C() {  
      funcArray[0] = &C::func1;  
      funcArray[1] = &C::func2;  
   }  
   void func3() {  
      (funcArray[0])();   // C2064  
      (this->*funcArray[0])(); // OK - called in this instance context  
   }  
};  
```