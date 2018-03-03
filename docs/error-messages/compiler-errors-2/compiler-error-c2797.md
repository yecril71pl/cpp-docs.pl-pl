---
title: "Błąd kompilatora C2797 | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C2797
dev_langs:
- C++
helpviewer_keywords:
- C2797
ms.assetid: 9fb26d35-eb5c-46fc-9ff5-756fba5bdaff
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 0c8fd31905eb92db8ad2e3af941772584f6f64ce
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-error-c2797"></a>Błąd kompilatora C2797
(Przestarzałe) Inicjalizacja listy wewnątrz listy inicjatorów elementu członkowskiego lub inicjator elementu członkowskiego danych niestatycznych nie jest zaimplementowana.  
  
 To ostrzeżenie jest przestarzała w programie Visual Studio 2015. W programie Visual Studio 2013 i wcześniejszych wersji kompilatora Visual C++ nie implementuje Inicjalizacja listy wewnątrz listy inicjatorów elementu członkowskiego lub inicjator elementu członkowskiego danych niestatycznych. Przed Visual Studio 2013 Update 3 zostało to dyskretnie przekształcone na wywołanie funkcji, która może spowodować wygenerowanie złego kodu. Program Visual Studio 2013 Update 3 raportuje ten błąd.  
  
 W tym przykładzie generuje C2797:  
  
```  
#include <vector>  
struct S {  
    S() : v1{1} {} // C2797, VS2013 RTM incorrectly calls 'vector(size_type)'  
  
    std::vector<int> v1;  
    std::vector<int> v2{1, 2}; // C2797, VS2013 RTM incorrectly calls 'vector(size_type, const int &)'  
};  
  
```  
  
 W tym przykładzie również generuje C2797:  
  
```  
struct S1 {  
    int i;  
};  
  
struct S2 {  
    S2() : s1{0} {} // C2797, VS2013 RTM interprets as S2() : s1(0) {} causing C2664  
    S1 s1;  
    S1 s2{0}; // C2797, VS2013 RTM interprets as S1 s2 = S1(0); causing C2664  
};  
  
```  
  
 Aby rozwiązać ten problem, można użyć jawna konstrukcja wewnętrzny list. Na przykład:  
  
```  
#include <vector>  
typedef std::vector<int> Vector;  
struct S {  
    S() : v1(Vector{1}) {}  
  
    Vector v1;  
    Vector v2 = Vector{1, 2};  
};  
  
```  
  
 Jeśli nie wymagają Inicjalizacja listy:  
  
```  
struct S {  
    S() : s1("") {}  
  
    std::string s1;  
    std::string s2 = std::string("");  
};  
  
```  
  
 (Kompilator programu Visual Studio 2013 robi to niejawnie przed Visual Studio 2013 Update 3.)