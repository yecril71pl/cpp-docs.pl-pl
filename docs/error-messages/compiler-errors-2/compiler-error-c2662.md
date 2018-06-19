---
title: C2662 błąd kompilatora | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2662
dev_langs:
- C++
helpviewer_keywords:
- C2662
ms.assetid: e172c2a4-f29e-4034-8232-e7dc6f83689f
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: d4e5f40fcc93739cabd2d5bd73bac6cce2332323
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33235350"
---
# <a name="compiler-error-c2662"></a>C2662 błąd kompilatora
"Funkcja": nie można konwertować wskaźnika "this" z "type1" na "type2"  
  
 Nie można przekonwertować kompilator `this` wskaźnika z `type1` do `type2`.  
  
 Ten błąd może być spowodowany przez wywołanie niż`const` funkcji członkowskiej na `const` obiektu.  Możliwe rozwiązania:  
  
-   Usuń `const` z deklaracji obiektu.  
  
-   Dodaj `const` do funkcji członkowskiej.  
  
 Poniższy przykład generuje C2662:  
  
```  
// C2662.cpp  
class C {  
public:  
   void func1();  
   void func2() const{}  
} const c;  
  
int main() {  
   c.func1();   // C2662  
   c.func2();   // OK  
}  
```  
  
 Podczas kompilowania za pomocą **/CLR**, nie można wywołać funkcję w `const` lub `volatile` kwalifikowanego typu zarządzanego. Nie można zadeklarować stałej funkcji członkowskiej klasy zarządzanej klasy, więc nie można wywołać metody dla const zarządzanych obiektów.  
  
```  
// C2662_b.cpp  
// compile with: /c /clr  
ref struct M {  
   property M^ Type {  
      M^ get() { return this; }  
   }  
  
   void operator=(const M %m) {  
      M ^ prop = m.Type;   // C2662  
   }  
};  
  
ref struct N {  
   property N^ Type {  
      N^ get() { return this; }  
   }  
  
   void operator=(N % n) {  
      N ^ prop = n.Type;   // OK  
   }  
};  
```  
  
 Poniższy przykład generuje C2662:  
  
```  
// C2662_c.cpp  
// compile with: /c  
// C2662 expected  
typedef int ISXVD;  
typedef unsigned char BYTE;  
  
class LXBASE {  
protected:  
    BYTE *m_rgb;  
};  
  
class LXISXVD:LXBASE {  
public:  
   // Delete the following line to resolve.  
   ISXVD *PMin() { return (ISXVD *)m_rgb; }  
  
   ISXVD *PMin2() const { return (ISXVD *)m_rgb; };   // OK  
};  
  
void F(const LXISXVD *plxisxvd, int iDim) {  
   ISXVD isxvd;  
   // Delete the following line to resolve.  
   isxvd = plxisxvd->PMin()[iDim];  
  
   isxvd = plxisxvd->PMin2()[iDim];    
}  
```