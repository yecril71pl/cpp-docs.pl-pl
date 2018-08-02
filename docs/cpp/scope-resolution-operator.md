---
title: 'Operator rozpoznawania zakresów::: | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
f1_keywords:
- '::'
dev_langs:
- C++
helpviewer_keywords:
- scope, scope resolution operator
- operators [C++], scope resolution
- scope resolution operator
- ':: operator'
ms.assetid: fd5de9d3-c716-4e12-bae9-03a16fd79a50
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: baf3678d204042bdea5e892a6e89d041b5091f38
ms.sourcegitcommit: 51f804005b8d921468775a0316de52ad39b77c3e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/02/2018
ms.locfileid: "39467082"
---
# <a name="scope-resolution-operator-"></a>Operator rozpoznawania zakresów: ::
Operator rozpoznawania zakresów **::** służy do identyfikowania i rozróżniać identyfikatory używane w różnych zakresach. Aby uzyskać więcej informacji na temat zakresu zobacz [zakres](../cpp/scope-visual-cpp.md).  
  
## <a name="syntax"></a>Składnia  
  
```  
:: identifier  
class-name :: identifier  
namespace :: identifier  
enum class :: identifier  
enum struct :: identifier  
```  
  
## <a name="remarks"></a>Uwagi  
 `identifier` Może być zmienną, funkcji lub wartości wyliczenia.  
  
## <a name="with-classes-and-namespaces"></a>Przy użyciu klas i przestrzeni nazw  
 Poniższy przykład pokazuje, jak operator rozpoznawania zakresów jest używany obszary nazw i klasy:  
  
```cpp  
namespace NamespaceA{  
    int x;  
    class ClassA {  
    public:  
        int x;  
    };  
}  
  
int main() {  
  
    // A namespace name used to disambiguate  
    NamespaceA::x = 1;  
  
    // A class name used to disambiguate  
    NamespaceA::ClassA a1;  
    a1.x = 2;  
}  
```  
  
 Operator rozpoznawania zakresów, bez kwalifikatora zakresu odnosi się do globalnej przestrzeni nazw.  
  
```cpp  
namespace NamespaceA{  
    int x;  
}  
  
int x;   
  
int main() {  
    int x;  
  
    // the x in main()  
    x = 0;   
    // The x in the global namespace  
    ::x = 1;   
  
    // The x in the A namespace  
    NamespaceA::x = 2;   
}  
```  
  
 Operator rozpoznawania zakresów można użyć do identyfikacji członka przestrzeni nazw lub do identyfikowania przestrzeni nazw, która wybiera przestrzeń nazw elementu członkowskiego w dyrektywie przy użyciu. W poniższym przykładzie można użyć `NamespaceC` kwalifikowania `ClassB`, nawet jeśli `ClassB` został zadeklarowany w przestrzeni nazw `NamespaceB`, ponieważ `NamespaceB` zostały określone w `NamespaceC` przy użyciu dyrektywy.  
  
```cpp  
namespace NamespaceB {  
    class ClassB {  
    public:  
        int x;  
    };  
}  
  
namespace NamespaceC{  
    using namespace B;  
}  
int main() {  
    NamespaceB::ClassB c_b;  
    NamespaceC::ClassB c_c;  
  
    c_b.x = 3;  
    c_c.x = 4;  
}  
```  
  
 Możesz użyć łańcuchów operatorów rozpoznawania zakresu. W poniższym przykładzie `NamespaceD::NamespaceD1` identyfikuje zagnieżdżone przestrzenie nazw `NamespaceD1`, i `NamespaceE::ClassE::ClassE1` identyfikuje zagnieżdżona klasa `ClassE1`.  
  
```cpp  
namespace NamespaceD{  
    namespace NamespaceD1{  
        int x;  
    }  
}  
  
namespace NamespaceE{  
    class ClassE{  
    public:  
        class ClassE1{  
        public:  
            int x;  
        };  
    };  
}  
  
int main() {  
    NamespaceD:: NamespaceD1::x = 6;  
    NamespaceE::ClassE::ClassE1 e1;  
    e1.x = 7  ;  
}  
```  
  
## <a name="with-static-members"></a>Ze statycznymi składowymi  
 Operator rozpoznawania zakresów należy użyć do wywołania statyczne elementy członkowskie klas.  
  
```cpp  
class ClassG {  
public:  
    static int get_x() { return x;}  
    static int x;  
};  
  
int ClassG::x = 6;  
  
int main() {  
  
    int gx1 = ClassG::x;  
    int gx2 = ClassG::get_x();   
}  
```  
  
## <a name="with-scoped-enumerations"></a>Za pomocą wyliczenia o określonym zakresie  
 Operator rozpoznawania zakresu jest również używany przy użyciu wartości wyliczenia w zakresie [deklaracje modułów Wyliczających](../cpp/enumerations-cpp.md), jak w poniższym przykładzie:  
  
```cpp  
enum class EnumA{  
    First,  
    Second,  
    Third  
};  
  
int main() {  
    EnumA enum_value = EnumA::First;  
}  
```  
  
## <a name="see-also"></a>Zobacz także  
 [C++ wbudowane operatory, pierwszeństwo i kojarzenie](../cpp/cpp-built-in-operators-precedence-and-associativity.md)   
 [Przestrzenie nazw](../cpp/namespaces-cpp.md)   