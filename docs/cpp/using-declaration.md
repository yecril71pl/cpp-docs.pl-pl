---
title: "za pomocą deklaracji | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- using declaration
- declaring namespaces, unqualified names in namespaces
- declarations [C++], using-declaration
- namespaces [C++], unqualified names in
- using keyword [C++]
- declarations [C++], namespaces
ms.assetid: 4184e2b1-3adc-408e-b5f3-0b3f8b554723
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: c6bf39dfdb4f59bcf54ce1ddd5174f1e3a55e3a0
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="using-declaration"></a>użycie — deklaracja
Za pomocą deklaracji wprowadza nazwę do regionu deklaratywne, w którym za pomocą deklaracji jest wyświetlana.  
  
## <a name="syntax"></a>Składnia  
  
```  
using [typename] nested-name-specifier unqualified-id ;  
using declarator-list ;  
```  
  
### <a name="parameters"></a>Parametry
  
*zagnieżdżone — nazwa — Specyfikator*  
    Sekwencja przestrzeni nazw, klasy lub wyliczenia nazw i operatory rozpoznawania zakresu (:), został przerwany przez operator rozpoznawania zakresów. Operator rozpoznawania pojedynczy zakres może służyć do wprowadzenia nazwy z globalnej przestrzeni nazw. Słowo kluczowe `typename` jest opcjonalna i może być używany do rozpoznania nazwy zależne przy wprowadzaniu szablonu klasy z klasy podstawowej.  
  
*niekwalifikowane identyfikator*  
    Niekwalifikowane identyfikator wyrażenia, które mogą być identyfikatora, nazwy przeciążonego operatora, zdefiniowane przez użytkownika literałów operatora lub konwersji nazwę funkcji, nazwa destruktora klasy lub listę nazw i argument szablonu.  
  
*Lista deklarator*  
    Rozdzielana przecinkami lista [`typename`] *zagnieżdżone name specyfikator* *niekwalifikowane identyfikator* deklaratorów, a następnie opcjonalnie wielokropkiem.
    
## <a name="remarks"></a>Uwagi  
A za pomocą deklaracji wprowadza nazwą niekwalifikowaną jako synonim dla jednostki zadeklarowany w innym miejscu. Umożliwia on nazwę jednego z określonych przestrzeni nazw, aby można używać bez jawna Kwalifikacja w regionie deklaracji, w których występuje. Jest to contrast do [dyrektywa using](../cpp/namespaces-cpp.md#using_directives), co pozwala *wszystkie* nazwy w przestrzeni nazw, aby bez kwalifikacji można używać. `using` — Słowo kluczowe służy także do [aliasów typów](../cpp/aliases-and-typedefs-cpp.md).  
  
## <a name="example"></a>Przykład  
 A za pomocą deklaracji mogą być używane w definicji klasy.  
  
```cpp  
// using_declaration1.cpp  
#include <stdio.h>  
class B {  
public:  
   void f(char) {  
      printf_s("In B::f()\n");  
   }  
  
   void g(char) {  
      printf_s("In B::g()\n");  
   }  
};  
  
class D : B {  
public:  
   using B::f;    // B::f(char) is now visible as D::f(char)  
   using B::g;    // B::g(char) is now visible as D::g(char)  
   void f(int) {  
      printf_s("In D::f()\n");  
      f('c');     // Invokes B::f(char) instead of recursing  
   }  
  
   void g(int) {  
      printf_s("In D::g()\n");  
      g('c');     // Invokes B::g(char) instead of recursing  
   }  
};  
  
int main() {  
   D myD;  
   myD.f(1);  
   myD.g('a');  
}  
```  
  
```Output  
In D::f()  
In B::f()  
In B::g()  
```  
  
## <a name="example"></a>Przykład  
W przypadku zastosowania do deklaruje elementu członkowskiego using deklaracji musi odwoływać się do elementu członkowskiego klasy podstawowej.  
  
```cpp  
// using_declaration2.cpp  
#include <stdio.h>  
  
class B {  
public:  
   void f(char) {  
      printf_s("In B::f()\n");  
   }  
  
   void g(char) {  
      printf_s("In B::g()\n");  
   }  
};  
  
class C {  
public:  
   int g();  
};  
  
class D2 : public B {  
public:  
   using B::f;   // ok: B is a base of D2  
   // using C::g;   // error: C isn't a base of D2  
};  
  
int main() {  
   D2 MyD2;  
   MyD2.f('a');  
}  
```  
  
```Output  
In B::f()  
```  
  
## <a name="example"></a>Przykład  
Zadeklarowane elementy członkowskie przy użyciu using deklaracja może odwoływać się przy użyciu jawna kwalifikacja. `::` Prefiks, który odwołuje się do globalnej przestrzeni nazw.  
  
```cpp  
// using_declaration3.cpp  
#include <stdio.h>  
  
void f() {  
   printf_s("In f\n");  
}  
  
namespace A {  
   void g() {  
      printf_s("In A::g\n");  
   }  
}  
  
namespace X {  
   using ::f;   // global f is also visible as X::f  
   using A::g;   // A's g is now visible as X::g 
}  
  
void h() {  
   printf_s("In h\n");  
   X::f();   // calls ::f  
   X::g();   // calls A::g  
}  
  
int main() {  
   h();  
}  
```  
  
```Output  
In h  
In f  
In A::g  
```  
  
## <a name="example"></a>Przykład  
Korzystając z zgłoszenia, synonim utworzone przez deklaracja odnosi się tylko do definicji, które są prawidłowe w punkcie za pomocą deklaracji. Definicje dodany do przestrzeni nazw, po użyciu deklaracji nie są prawidłowe synonimy.  
  
Zdefiniowane przez nazwę `using` deklaracja jest aliasu dla jego oryginalną nazwę. Nie dotyczy tego typu, połączenie lub inne atrybuty oryginalnej deklaracji.  
  
```cpp  
// post_declaration_namespace_additions.cpp  
// compile with: /c  
namespace A {  
   void f(int) {}  
}  
  
using A::f;   // f is a synonym for A::f(int) only  
  
namespace A {  
   void f(char) {}  
}  
  
void f() {  
   f('a');   // refers to A::f(int), even though A::f(char) exists  
}  
  
void b() {  
   using A::f;   // refers to A::f(int) AND A::f(char)  
   f('a');   // calls A::f(char);  
}  
```  
  
## <a name="example"></a>Przykład  
W odniesieniu do funkcji w przestrzeni nazw, jeśli zestaw deklaracje lokalne i użyciem deklaracji w odniesieniu do jednej nazwy są podane w regionie deklaratywne, musi wszystkie odnoszą się do tej samej jednostki lub musi wszystkie odnoszą się do funkcji.  
  
```cpp  
// functions_in_namespaces1.cpp  
// C2874 expected  
namespace B {  
    int i;  
    void f(int);  
    void f(double);  
}  
  
void g() {  
    int i;  
    using B::i;   // error: i declared twice  
    void f(char);  
    using B::f;   // ok: each f is a function  
}  
```  
  
 W powyższym przykładzie `using B::i` instrukcja powoduje drugiej `int i` podawane w `g()` funkcji. `using B::f` Instrukcji nie powoduje konfliktu z `f(char)` działać, ponieważ wynikające z nazwy funkcji `B::f` mają różne typy parametrów.  
  
## <a name="example"></a>Przykład  
 Deklaracji funkcji lokalnej nie może mieć taką samą nazwę i typ jako funkcja wprowadzone za pomocą deklaracji. Na przykład:  
  
```cpp  
// functions_in_namespaces2.cpp  
// C2668 expected  
namespace B {  
    void f(int);  
    void f(double);  
}  
  
namespace C {  
    void f(int);  
    void f(double);  
    void f(char);  
}  
  
void h() {  
    using B::f;          // introduces B::f(int) and B::f(double)  
    using C::f;          // C::f(int), C::f(double), and C::f(char)  
    f('h');              // calls C::f(char)  
    f(1);                // C2668 ambiguous: B::f(int) or C::f(int)?  
    void f(int);         // C2883 conflicts with B::f(int) and C::f(int)  
}  
```  
  
## <a name="example"></a>Przykład  
 Względem dziedziczenia korzystając z deklaracji wprowadza nazwę z klasy podstawowej w zakresie klasy pochodnej, funkcje Członkowskie w funkcjach wirtualnego elementu członkowskiego klasy pochodnej zastąpienie z tymi samymi typami nazwy i argument w klasie podstawowej.  
  
```cpp  
// using_declaration_inheritance1.cpp  
#include <stdio.h>  
struct B {  
   virtual void f(int) {  
      printf_s("In B::f(int)\n");  
   }  
  
   virtual void f(char) {  
      printf_s("In B::f(char)\n");  
   }  
  
   void g(int) {  
      printf_s("In B::g\n");  
   }  
  
   void h(int);  
};  
  
struct D : B {  
   using B::f;  
   void f(int) {   // ok: D::f(int) overrides B::f(int)  
      printf_s("In D::f(int)\n");  
   }  
  
   using B::g;  
   void g(char) {   // ok: there is no B::g(char)  
      printf_s("In D::g(char)\n");  
   }  
  
   using B::h;  
   void h(int) {}   // Note: D::h(int) hides non-virtual B::h(int)  
};  
  
void f(D* pd) {  
   pd->f(1);     // calls D::f(int)  
   pd->f('a');   // calls B::f(char)  
   pd->g(1);     // calls B::g(int)  
   pd->g('a');   // calls D::g(char)  
}  
  
int main() {  
   D * myd = new D();  
   f(myd);  
}  
```  
  
```Output  
In D::f(int)  
In B::f(char)  
In B::g  
In D::g(char)  
```  
  
## <a name="example"></a>Przykład  
Wszystkie wystąpienia nazwy wspomnianego używającego deklaracji muszą być dostępne. W szczególności, jeśli Klasa pochodna używa używającego deklaracji można uzyskać dostępu do elementu członkowskiego klasy podstawowej, nazwę elementu członkowskiego musi być dostępna. Jeśli nazwa jest funkcja przeciążonego elementu członkowskiego, a następnie wszystkich funkcji o nazwie muszą być dostępne.  
  
Aby uzyskać więcej informacji o ułatwieniach dostępu elementów członkowskich, zobacz [kontroli dostępu do elementu członkowskiego](../cpp/member-access-control-cpp.md).  
  
```cpp  
// using_declaration_inheritance2.cpp  
// C2876 expected  
class A {  
private:  
   void f(char);  
public:  
   void f(int);  
protected:  
   void g();  
};  
  
class B : public A {  
   using A::f;   // C2876: A::f(char) is inaccessible  
public:  
   using A::g;   // B::g is a public synonym for A::g  
};  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Przestrzenie nazw](../cpp/namespaces-cpp.md)   
 [Słowa kluczowe](../cpp/keywords-cpp.md)