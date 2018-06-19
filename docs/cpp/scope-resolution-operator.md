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
ms.openlocfilehash: 7caea3a32c0bb983518f7610918c78c8c31c63a0
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
ms.locfileid: "32420944"
---
# <a name="scope-resolution-operator-"></a>Operator rozpoznawania zakresów: ::
Operator rozpoznawania zakresów `::` służy do identyfikowania i odróżnienia identyfikatory używane w innych zakresach. Aby uzyskać więcej informacji na temat zakresu, zobacz [zakres](../cpp/scope-visual-cpp.md).  
  
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
  
## <a name="with-classes-and-namespaces"></a>Z klasami i przestrzenie nazw  
 W poniższym przykładzie pokazano, jak jest używany operator rozpoznawania zakresów z przestrzeni nazw i klasy:  
  
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
  
 Operator rozpoznawania zakresów, bez kwalifikatora zakres odwołuje się do globalnej przestrzeni nazw.  
  
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
  
 Operator rozpoznawania zakresów można użyć do identyfikacji członka przestrzeni nazw lub do identyfikowania przestrzeni nazw, która wybiera obszar nazw elementu członkowskiego w dyrektywy using. W poniższym przykładzie, można użyć `NamespaceC` na kwalifikować się `ClassB`, nawet jeśli `ClassB` została zadeklarowana w przestrzeni nazw `NamespaceB`, ponieważ `NamespaceB` zostały określone w `NamespaceC` przy użyciu dyrektywy.  
  
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
  
 Możesz użyć łańcuchów operatorów rozpoznawania zakresu. W poniższym przykładzie `NamespaceD::NamespaceD1` identyfikuje zagnieżdżonych przestrzeni nazw `NamespaceD1`, i `NamespaceE::ClassE::ClassE1` identyfikuje zagnieżdżona klasa `ClassE1`.  
  
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
  
## <a name="with-static-members"></a>Ze statycznymi elementami członkowskimi  
 Operator rozpoznawania zakresów należy użyć, aby wywołać statyczne elementy członkowskie klasy.  
  
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
  
## <a name="with-scoped-enumerations"></a>Z zakresie wyliczenia  
 Operator zakresie rozpoznawania jest również używany z wartości wyliczenia w zakresie [deklaracje modułów Wyliczających](../cpp/enumerations-cpp.md), jak w poniższym przykładzie:  
  
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
  
## <a name="see-also"></a>Zobacz też  
 [Operatory C++ wbudowanych, priorytet i łączność](../cpp/cpp-built-in-operators-precedence-and-associativity.md)   
 [Przestrzenie nazw](../cpp/namespaces-cpp.md)   