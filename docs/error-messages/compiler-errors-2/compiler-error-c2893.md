---
title: C2893 błąd kompilatora | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2893
dev_langs:
- C++
helpviewer_keywords:
- C2893
ms.assetid: ec0cbe43-005d-45da-8742-aaeb9b81d28e
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: db3b71a05ece6b79672d47699dc68e0eb5bb1f60
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33246701"
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