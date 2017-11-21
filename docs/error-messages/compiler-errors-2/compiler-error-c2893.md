---
title: "C2893 błąd kompilatora | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C2893
dev_langs: C++
helpviewer_keywords: C2893
ms.assetid: ec0cbe43-005d-45da-8742-aaeb9b81d28e
caps.latest.revision: "12"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 6ad558968720a13b95fecc6860df5826b47874aa
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-error-c2893"></a>C2893 błąd kompilatora
Nie powiodła się specjalizacja szablonu funkcji "Nazwa szablonu"  
  
 Kompilator nie powiodło się specjalizacja szablonu funkcji. Może istnieć wiele przyczyn tego błędu.  
  
 Ogólnie rzecz biorąc sposób, aby rozwiązać problem C2893 jest Przejrzyj podpisu funkcji i upewnij się, że można utworzyć wystąpienia każdego typu.  
  
## <a name="example"></a>Przykład  
 C2893 występuje, ponieważ `f`w parametr szablonu `T` jest ustalona jako `std::map<int,int>`, ale `std::map<int,int>` ma elementu członkowskiego `data_type` (`T::data_type` nie można utworzyć wystąpienia z `T = std::map<int,int>`.). Poniższy przykład generuje C2893.  
  
```  
// C2893.cpp  
// compile with: /c /EHsc  
#include<map>  
using namespace std;  
class MyClass {};  
  
template<class T>   
inline typename T::data_type  
// try the following line instead  
// inline typename  T::mapped_type  
f(T const& p1, MyClass const& p2);  
  
template<class T>  
void bar(T const& p1) {  
    MyClass r;  
    f(p1,r);   // C2893  
}  
  
int main() {  
   map<int,int> m;  
   bar(m);  
}  
```