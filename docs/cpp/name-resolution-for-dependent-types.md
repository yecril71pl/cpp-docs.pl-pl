---
title: Rozpoznawanie nazw dla typów zależnych | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
ms.assetid: 34066bb4-0c79-4fd8-bda7-539a60a277ab
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: ad833d0fb4309ed4fed0eba4c162c9d6d46bf95d
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2018
ms.locfileid: "42588220"
---
# <a name="name-resolution-for-dependent-types"></a>Rozpoznawanie nazwy dla typów zależnych
Użyj **typename** dla kwalifikowanych nazw w definicjach szablonów, aby poinformować kompilator, że dany kwalifikowana nazwa identyfikuje typ. Aby uzyskać więcej informacji, zobacz [typename](../cpp/typename.md).  
  
```cpp  
// template_name_resolution1.cpp  
#include <stdio.h>  
template <class T> class X  
{  
public:  
   void f(typename T::myType* mt) {}  
};  
  
class Yarg  
{  
public:  
   struct myType { };  
};  
  
int main()  
{  
   X<Yarg> x;  
   x.f(new Yarg::myType());  
   printf("Name resolved by using typename keyword.");  
}  
```  
  
```Output  
Name resolved by using typename keyword.  
```  
  
 Wyszukiwanie nazw dla nazwy zależne sprawdza nazwy w kontekście definicji szablonu — w poniższym przykładzie spowoduje znalezienie tego kontekstu `myFunction(char)`— i obiekt context Tworzenie wystąpienia szablonu. W poniższym przykładzie zostanie utworzone wystąpienie szablonu w głównym; w związku z tym `MyNamespace::myFunction` jest widoczna od momentu utworzenia wystąpienia i jest wybrany jako lepsze dopasowanie. Jeśli `MyNamespace::myFunction` zostały zmienione, `myFunction(char)` czy zamiast tego wywoływany.  
  
 Wszystkie nazwy są rozpoznawane tak, jakby były one nazwy zależne. Niemniej jednak zaleca się korzystać z w pełni kwalifikowane nazwy, jeśli możliwych konfliktów.  
  
```cpp  
// template_name_resolution2.cpp  
// compile with: /EHsc  
#include <iostream>  
using namespace std;  
  
void myFunction(char)  
{  
   cout << "Char myFunction" << endl;  
}  
  
template <class T> class Class1  
{  
public:  
   Class1(T i)  
   {  
      // If replaced with myFunction(1), myFunction(char)  
      // will be called  
      myFunction(i);  
}  
};  
  
namespace MyNamespace  
{  
   void myFunction(int)  
   {  
      cout << "Int MyNamespace::myFunction" << endl;  
   }  
};  
  
using namespace MyNamespace;  
  
int main()  
{  
   Class1<int>* c1 = new Class1<int>(100);  
}  
```  
  
### <a name="output"></a>Dane wyjściowe  
  
```Output  
Int MyNamespace::myFunction  
```  
  
### <a name="template-disambiguation"></a>Uściślanie szablonu  
 Program Visual Studio 2012 wymusza C ++ 98/03/11 standardowych zasad na Uściślanie za pomocą słowa kluczowego "szablon". W poniższym przykładzie Visual C++ 2010 będzie akceptować niezgodnych wierszy i zgodnych wierszy.  Program Visual Studio 2012 akceptuje tylko zgodnych wierszy.  
  
```cpp  
#include <iostream>  
#include <ostream>  
#include <typeinfo>  
using namespace std;  
  
template <typename T> struct Allocator {  
    template <typename U> struct Rebind {  
        typedef Allocator<U> Other;  
    };  
};  
  
template <typename X, typename AY> struct Container {  
    #if defined(NONCONFORMANT)  
        typedef typename AY::Rebind<X>::Other AX; // nonconformant  
    #elif defined(CONFORMANT)  
        typedef typename AY::template Rebind<X>::Other AX; // conformant  
    #else  
        #error Define NONCONFORMANT or CONFORMANT.  
    #endif  
};  
  
int main() {  
    cout << typeid(Container<int, Allocator<float>>::AX).name() << endl;  
}  
```  
  
 Zgodność z zasadami uściślania jest wymagana, ponieważ domyślnie C++ założono, że `AY::Rebind` nie jest szablonem, i dlatego kompilator interpretuje następujące "`<`" jako mniej-niż. Ma poinformować, że `Rebind` jest szablonem, dzięki czemu można poprawnie przeanalizować "`<`" jako nawias ostry.  
  
## <a name="see-also"></a>Zobacz także  
 [Rozpoznawanie nazw](../cpp/templates-and-name-resolution.md)