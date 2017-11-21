---
title: "C2955 błąd kompilatora | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 03/28/2017
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C2955
dev_langs: C++
helpviewer_keywords: C2955
ms.assetid: 77709fb6-d69b-46fd-a62f-e8564563d01b
caps.latest.revision: "15"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: af3f53545aa70e738f14c902a7a75afc48275b57
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-error-c2955"></a>C2955 błąd kompilatora
"identyfikator": użycie szablonu klasy lub alias ogólny wymaga szablonu lub listy argumentów ogólnych  
  
 Szablon klasy lub klas ogólnych nie można użyć jako identyfikatora bez szablonu lub listy argumentów ogólnych.  
  
 Aby uzyskać więcej informacji, zobacz [szablonów klas](../../cpp/class-templates.md).  
  
 Poniższy przykład generuje C2955 i pokazuje, jak rozwiązywanie problemu:  
  
```  
// C2955.cpp  
// compile with: /c  
template<class T>   
class X {};  
  
X x1;   // C2955  
X<int> x2;   // OK - this is how to fix it.  
```  
  
 C2955 może również wystąpić podczas próby definicji wiersza funkcja zadeklarowana w szablonie klasy:  
  
```  
// C2955_b.cpp  
// compile with: /c  
template <class T>  
class CT {  
public:  
   void CTFunc();  
   void CTFunc2();  
};  
  
void CT::CTFunc() {}   // C2955  
  
// OK - this is how to fix it  
template <class T>  
void CT<T>::CTFunc2() {}  
  
```  
  
 C2955 może również wystąpić, gdy użycie typów ogólnych:  
  
```  
// C2955_c.cpp  
// compile with: /clr  
generic <class T>   
ref struct GC {   
   T t;  
};  
  
int main() {  
   GC^ g;   // C2955  
   GC <int>^ g;  
}  
```

## <a name="example"></a>Przykład
**Visual Studio 2017 lub nowszy:** kompilator prawidłowo diagnozuje brakuje listy argumentów szablonu, gdy szablon zostanie wyświetlony na liście parametrów szablonu (na przykład jako część domyślnego argumentu szablonu lub parametr szablonu bez typu). Poniższy kod kompiluje w programie Visual Studio 2015, ale powoduje błąd w programie Visual Studio 2017 r.

```
template <class T> class ListNode;
template <class T> using ListNodeMember = ListNode<T> T::*;
template <class T, ListNodeMember M> class ListHead; // C2955: 'ListNodeMember': use of alias 
                                                     // template requires template argument list

// correct:  template <class T, ListNodeMember<T> M> class ListHead;
```
