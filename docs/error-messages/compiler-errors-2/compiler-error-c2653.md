---
title: "C2653 błąd kompilatora | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/16/2017
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C2653
dev_langs: C++
helpviewer_keywords: C2653
ms.assetid: 3f49e731-affd-43a0-a8d0-181db7650bc3
caps.latest.revision: "9"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 8b2cca7e855256e9caf5a72e6f8b4a6e2924eca6
ms.sourcegitcommit: 78f3f8208d49b7c1d87f4240f4a1496b7c29333e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/17/2017
---
# <a name="compiler-error-c2653"></a>C2653 błąd kompilatora
'Identyfikator': nie jest nazwą klasy lub przestrzeni nazw  
  
Składnia wymaga klasy, struktury, Unii lub przestrzeni nazw.  
  
Poniższy przykład generuje C2653:  
  
```cpp  
// C2653.cpp  
// compile with: /c  
class yy {  
   void func1(int i);  
};  
  
void xx::func1(int m) {}   // C2653  
void yy::func1(int m) {}   // OK  
```  
  
C2653 jest także możliwe, jeśli próby zdefiniowania *złożone przestrzeni nazw*, przestrzeni nazw, która zawiera jedną lub więcej nazw zagnieżdżone w zakresie przestrzeni nazw, w przypadku korzystania z wersji programu Visual C++ przed Visual Studio 2015 Update 3. Złożone przestrzeni nazw, definicje nie są dozwolone w języku C++ przed C ++ 17. Począwszy od programu Visual C++ 2015 wersji 15,5 cala kompilator obsługuje definicje złożone przestrzeń nazw podczas [/std:c ++ 17](../../build/reference/std-specify-language-standard-version.md) określono opcję kompilatora:  
```cpp  
// C2653b.cpp  
namespace a::b {int i;}   // C2653 prior to Visual C++ 2015 Update 3,  
                          // C2429 thereafter. Use /std:c++17 to fix (or /std:c++latest in 15.3)
namespace a {  
   namespace b {  
      int i;  
   }  
}  
  
int main() {  
   a::b::i = 2;  
}  
```  

W Visual Studio 2017 15 ustęp 3, wersja /std:c ++ najnowsze przełącznik jest wymagany.
