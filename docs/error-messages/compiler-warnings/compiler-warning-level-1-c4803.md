---
title: "Kompilatora (poziom 1) ostrzeżenie C4803 | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C4803
dev_langs: C++
helpviewer_keywords: C4803
ms.assetid: 2552f3a6-c418-49f4-98a2-a929857be658
caps.latest.revision: "9"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: b6725685e84e1c9ce0fc5c3f58f4ff163870d278
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-warning-level-1-c4803"></a>Kompilator C4803 ostrzegawcze (poziom 1)
"metoda": podniesiona metoda ma klasę magazynu inną od zdarzenia, "event"  
  
Metody zdarzenia muszą mieć tą samą klasę magazynu jako deklaracji zdarzenia. Kompilator dopasowuje metody zdarzeń, aby klasy magazynu są takie same.  
  
To ostrzeżenie może wystąpić, jeśli klasa implementująca zdarzenie z interfejsem. Kompilator nie generuje niejawnie metody wzrostu zdarzenie w interfejsie. Po zaimplementowaniu interfejsu w klasie kompilator niejawnie wygenerować metody wzrostu i metoda ta nie będzie wirtualnego, dlatego to ostrzeżenie. Aby uzyskać więcej informacji dotyczących zdarzeń, zobacz [zdarzeń](../../windows/event-cpp-component-extensions.md).  
  
Zobacz [ostrzeżenie](../../preprocessor/warning.md) pragma informacji na temat wyłączyć ostrzeżenia.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład generuje C4803.  
  
```  
// C4803.cpp  
// compile with: /clr /W1  
using namespace System;  
  
public delegate void Del();  
  
ref struct E {  
   Del ^ _pd1;  
   event Del ^ E1 {  
      void add (Del ^ pd1) {  
         _pd1 = dynamic_cast<Del ^>(Delegate::Combine(_pd1, pd1));  
      }  
  
      void remove(Del^ pd1) {  
         _pd1 = dynamic_cast<Del^> (Delegate::Remove(_pd1, pd1));  
      }  
  
      virtual void raise() {   // C4803 warning (remove virtual)  
         if (_pd1)  
            _pd1();  
      }  
   }  
  
   void func() {  
      Console::WriteLine("In E::func()");  
   }  
};  
  
int main() {  
   E ^ ep = gcnew E;  
   ep->E1 += gcnew Del(ep, &E::func);  
   ep->E1();  
   ep->E1 -= gcnew Del(ep, &E::func);  
   ep->E1();  
}  
```  
