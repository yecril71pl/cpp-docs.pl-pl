---
title: "Rozpoznawanie nazw dla typów zależnych | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs: C++
ms.assetid: 34066bb4-0c79-4fd8-bda7-539a60a277ab
caps.latest.revision: "11"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 3ca2c849c7ab825dfdfa609d680851de5432f012
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="name-resolution-for-dependent-types"></a>Rozpoznawanie nazwy dla typów zależnych
Użyj **typename** dla nazwy kwalifikowane w definicji szablonu kompilator stwierdzić, że podana nazwa kwalifikowana identyfikuje typ. Aby uzyskać więcej informacji, zobacz [typename](../cpp/typename.md).  
  
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
  
 Wyszukiwanie nazwy dla nazwy zależne sprawdza, czy nazwy z kontekstu definicji szablonu — w poniższym przykładzie tego kontekstu może być `myFunction(char)`— oraz kontekst utworzenie wystąpienia szablonu. W poniższym przykładzie szablon zostanie uruchomiony w głównym; w związku z tym `MyNamespace::myFunction` jest widoczna od momentu wystąpienia i jest wybierany jako lepszym dopasowaniem. Jeśli `MyNamespace::myFunction` nazwy zostały zmienione, `myFunction(char)` czy zamiast tego wywołać.  
  
 Wszystkie nazwy są rozpoznawane, tak jakby były nazwy zależne. Niemniej jednak zalecane jest użycie w pełni kwalifikowane nazwy, jeśli wszystkie możliwe konfliktu.  
  
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
  
```  
Int MyNamespace::myFunction  
```  
  
### <a name="template-disambiguation"></a>Uściślanie szablonu  
 [!INCLUDE[cpp_dev11_long](../build/includes/cpp_dev11_long_md.md)]Wymusza C ++ 98/03/11 standardowych zasad na Uściślanie ze słowem kluczowym "szablon". W poniższym przykładzie Visual C++ 2010 będzie akceptować niezgodnych linii i zgodnych wierszy.  [!INCLUDE[cpp_dev11_long](../build/includes/cpp_dev11_long_md.md)]akceptuje tylko zgodnych wierszy.  
  
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
  
 Zgodność z regułami Uściślanie jest wymagana, ponieważ domyślnie C++ zakłada się, że `AY::Rebind` nie jest szablonem, i dlatego kompilator interpretuje następujące "`<`" jako mniej-niż. Należy pamiętać, że `Rebind` jest szablonem, dzięki czemu można poprawnie przeanalizować "`<`" jako nawias.  
  
## <a name="see-also"></a>Zobacz też  
 [Rozpoznawanie nazw](../cpp/templates-and-name-resolution.md)