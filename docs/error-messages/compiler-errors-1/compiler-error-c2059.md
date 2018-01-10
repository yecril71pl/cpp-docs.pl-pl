---
title: "C2059 błąd kompilatora | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C2059
dev_langs: C++
helpviewer_keywords: C2059
ms.assetid: 2be4eb39-3f37-4b32-8e8d-75835e07c78a
caps.latest.revision: "22"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: a87f9c3dbb1405463804b7abd5c94abe04a42845
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-error-c2059"></a>C2059 błąd kompilatora
Błąd składniowy: "token"  
  
 Token spowodował błąd składni.  
  
 Poniższy przykład generuje komunikat o błędzie dla wiersza, który deklaruje `j`.  
  
```  
// C2059e.cpp  
// compile with: /c  
// C2143 expected  
// Error caused by the incorrect use of '*'.  
   int j*; // C2059   
```  
  
 Aby ustalić przyczynę błędu, należy nie tylko wiersz, który znajduje się w komunikacie o błędzie, ale również wierszy powyżej. Jeśli badanie wiersze daje nie informacja o problem, spróbuj komentowania wiersza, który znajduje się w komunikacie o błędzie i prawdopodobnie kilka wierszy powyżej.  
  
 Jeśli komunikat o błędzie na symbol poniższą `typedef` zmiennej, upewnij się, że zmienna jest zdefiniowana w kodzie źródłowym.  
  
 C2059 mogą wystąpić, jeśli symbol daje w wyniku nothing, co może mieć miejsce, gdy **/D** `symbol`  **=**  jest używana do kompilowania.  
  
```  
// C2059a.cpp  
// compile with: /DTEST=  
#include <stdio.h>  
  
int main() {  
   #ifdef TEST  
      printf_s("\nTEST defined %d", TEST);   // C2059  
   #else  
      printf_s("\nTEST not defined");  
   #endif  
}  
```  
  
 Inny przypadek, w którym mogą występować C2059 jest podczas kompilowania aplikacji, która określa strukturę w domyślne argumenty dla funkcji. Wartość domyślna argumentu musi być wyrażeniem. Lista inicjalizatora — na przykład taki, który jest używany do inicjowania struktury — nie jest wyrażeniem.  Aby rozwiązać ten problem, zdefiniuj konstruktora, aby wykonać wymagane inicjowania.  
  
 Poniższy przykład generuje C2059:  
  
```  
// C2059b.cpp  
// compile with: /c  
struct ag_type {  
   int a;  
   float b;  
   // Uncomment the following line to resolve.  
   // ag_type(int aa, float bb) : a(aa), b(bb) {}   
};  
  
void func(ag_type arg = {5, 7.0});   // C2059  
void func(ag_type arg = ag_type(5, 7.0));   // OK  
```  
  
 Można również uzyskać C2059 w przypadku definiowania elementu członkowskiego szablonu klasy lub funkcji poza klasą. Aby uzyskać informacje, zobacz [artykułu bazy wiedzy 241949](http://support.microsoft.com/kb/241949).  
  
 C2059 mogą być źle sformułowane rzutowania.  
  
 Poniższy przykład generuje C2059:  
  
```  
// C2059c.cpp  
// compile with: /clr  
using namespace System;  
ref class From {};  
ref class To : public From {};  
  
int main() {  
   From^ refbase = gcnew To();  
   To^ refTo = safe_cast<To^>(From^);   // C2059  
   To^ refTo2 = safe_cast<To^>(refbase);   // OK  
}  
```  
  
 C2059 może również wystąpić, jeśli próba utworzenia nazwę przestrzeni nazw, która zawiera znak kropki.  
  
 Poniższy przykład generuje C2059:  
  
```  
// C2059d.cpp  
// compile with: /c  
namespace A.B {}   // C2059  
  
// OK  
namespace A  {  
   namespace B {}  
}  
```  
  
 C2059 może wystąpić, gdy operator, który można nazwy (`::`, `->`, i `.`) musi następować słowo kluczowe `template`, jak pokazano w poniższym przykładzie:  
  
```cpp  
template <typename T> struct Allocator {  
    template <typename U> struct Rebind {  
        typedef Allocator<U> Other;  
    };  
};  
  
template <typename X, typename AY> struct Container {  
    typedef typename AY::Rebind<X>::Other AX; // error C2059  
};  
  
```  
  
 Domyślnie C++ zakłada się, że `AY::Rebind` nie jest szablonem; w związku z tym następujące `<` jest interpretowana jako mniej-znaku.  Należy nakazuje kompilatorowi jawnie który `Rebind` jest to szablon, tak aby poprawnie może przeanalizować składni nawiasu ostrego. Aby rozwiązać ten problem, należy użyć `template` — słowo kluczowe w typie zależnym nazwy, jak pokazano poniżej:  
  
```cpp  
template <typename T> struct Allocator {  
    template <typename U> struct Rebind {  
        typedef Allocator<U> Other;  
    };  
};  
  
template <typename X, typename AY> struct Container {  
    typedef typename AY::template Rebind<X>::Other AX; // correct  
};  
  
```