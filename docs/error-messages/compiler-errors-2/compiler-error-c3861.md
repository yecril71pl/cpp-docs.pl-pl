---
title: "C3861 błąd kompilatora | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C3861
dev_langs:
- C++
helpviewer_keywords:
- C3861
ms.assetid: 0a1eee30-b3db-41b1-b1e5-35949c3924d7
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 82656822d408be4b2fc085abe8a007469c822a65
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-error-c3861"></a>C3861 błąd kompilatora

> "*identyfikator*": nie odnaleziono identyfikatora  
  
Kompilator nie może rozpoznać odwołania do identyfikatora, nawet za pomocą wyszukiwania zależnego od argumentów.  
  
Aby naprawić ten błąd, porównaj użycie *identyfikator* do zgłoszenia identyfikator wielkość liter i pisowni. Sprawdź, czy [zakres rozpoznawania operatory](../../cpp/scope-resolution-operator.md) i przestrzeni nazw [przy użyciu dyrektyw](../../cpp/namespaces-cpp.md#using_directives) jest używana poprawnie. Jeśli identyfikator jest zadeklarowany w pliku nagłówka, należy sprawdzić, czy przed odwołuje się identyfikator znajduje się nagłówka. Jeśli identyfikator ma być widoczne na zewnątrz, upewnij się, że jest on zadeklarowany w dowolnym plik źródłowy, który korzysta z niego. Sprawdź również, że identyfikator deklaracji lub definicji nie jest wykluczone przez [dyrektywy warunkowej kompilacji](../../preprocessor/hash-if-hash-elif-hash-else-and-hash-endif-directives-c-cpp.md). 

Zmiany, aby usunąć przestarzałe funkcje z C biblioteki wykonawczej programu Visual Studio 2015 może spowodować C3861. Aby rozwiązać ten problem, usuń odwołania do tych funkcji lub zastąpić je ich bezpiecznych rozwiązań alternatywnych, jeśli istnieje. Aby uzyskać więcej informacji, zobacz [przestarzałe funkcje](../../c-runtime-library/obsolete-functions.md).  

Jeśli błąd C3861 pojawia się po zakończeniu migracji projektu ze starszych wersji kompilatora, mogą mieć problemy związane z obsługiwanych wersji systemu Windows. Visual C++ nie obsługuje już docelowy system operacyjny Windows 95, Windows 98, Windows ME, Windows NT lub Windows 2000. Jeśli Twoje makra WINVER i _WIN32_WINNT są przypisane do jednej z tych wersji systemu Windows, należy zmodyfikować makra. Aby uzyskać więcej informacji, zobacz [modyfikowanie WINVER i _WIN32_WINNT](../../porting/modifying-winver-and-win32-winnt.md).
  
## <a name="example"></a>Przykład  

Poniższy przykład generuje C3861, ponieważ nie zdefiniowano identyfikatora.  
  
```cpp  
// C3861.cpp  
void f2(){}  
int main() {  
   f();    // C3861  
   f2();   // OK  
}  
```  
  
## <a name="example"></a>Przykład  

Poniższy przykład generuje C3861, ponieważ identyfikator jest tylko widoczne w zakresie pliku jego definicji, o ile nie jest zadeklarowany w innych plikach źródłowych, które go używają.  
  
```cpp  
// C3861_a1.cpp
// Compile with: cl /EHsc /W4 C3861_a1.cpp C3861_a2.cpp  
#include <iostream>
// Uncomment the following line to fix:
// int f();  // declaration makes external function visible
int main() {  
   std::cout << f() << std::endl;    // C3861
}  
```  
  
```cpp  
// C3861_a2.cpp  
int f() {  // declared and defined here
   return 42;  
}
```  
  
## <a name="example"></a>Przykład  

Klasy wyjątków w standardowej bibliotece C++ wymagają `std` przestrzeni nazw.  
  
```cpp  
// C3861_b.cpp  
// compile with: /EHsc  
#include <iostream>  
int main() {  
   try {  
      throw exception("Exception");   // C3861  
      // try the following line instead  
      // throw std::exception("Exception");  
   }  
   catch (...) {  
      std::cout << "caught an exception" << std::endl;  
   }  
}  
```  
## <a name="example"></a>Przykład  

Przestarzałe funkcje zostały usunięte z biblioteki CRT.  
  
```cpp  
// C3861_c.cpp  
#include <stdio.h>  
int main() {  
   char line[21]; // room for 20 chars + '\0'  
   gets( line );  // C3861  
   // Use gets_s instead.  
   printf( "The line entered was: %s\n", line );  
}  
```
Poniższy przykład generuje C3767, ponieważ kompilator nie można użyć argumentu zależnych wyszukiwania dla FriendFunc:  
  
```  
namespace N {  
   class C {  
      friend void FriendFunc() {}  
      friend void AnotherFriendFunc(C* c) {}  
   };  
}  
  
int main() {  
   using namespace N;  
   FriendFunc();   // C3861 error  
   C* pC = new C();  
   AnotherFriendFunc(pC);   // found via argument-dependent lookup  
}  
```  
  
Aby naprawić błąd, deklarowanie friend w zakresie klasy i zdefiniuj je w zakresie przestrzeni nazw:  
  

Klasa MyClass {  
   int m_private;  
   Friend void func();  
};  
  
{void func()  
   MyClass s;  
   s.m_private = 0;  
}  
  
int main() {  
   FUNC();  
}  