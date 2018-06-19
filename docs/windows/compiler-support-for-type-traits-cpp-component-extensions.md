---
title: Obsługa cech typu w kompilatorze (C++ Component Extensions) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- __is_simple_value_class
- __has_trivial_destructor
- __has_assign
- __is_union
- __is_class
- __is_abstract
- __has_trivial_assign
- __has_virtual_destructor
- __is_ref_array
- __is_base_of
- __has_copy
- __is_polymorphic
- __has_nothrow_constructor
- __is_ref_class
- __is_delegate
- __is_convertible_to
- __is_value_class
- __is_interface_class
- __has_nothrow_copy
- __is_sealed
- __has_trivial_constructor
- __has_trivial_copy
- __is_enum
- __has_nothrow_assign
- __has_finalizer
- __is_empty
- __is_pod
- __has_user_destructor
dev_langs:
- C++
helpviewer_keywords:
- __is_class keyword [C++]
- __is_pod keyword [C++]
- __is_delegate keyword [C++]
- __is_value_class keyword [C++]
- __has_copy keyword [C++]
- __has_nothrow_copy keyword [C++]
- __is_interface_class keyword [C++]
- __is_sealed keyword [C++]
- __is_convertible_to keyword [C++]
- __is_ref_class keyword [C++]
- __has_trivial_copy keyword [C++]
- __has_user_destructor keyword [C++]
- __is_abstract keyword [C++]
- __is_empty keyword [C++]
- __has_trivial_assign keyword [C++]
- __has_nothrow_constructor keyword [C++]
- __is_ref_array keyword [C++]
- __is_base_of keyword [C++]
- __has_nothrow_assign keyword [C++]
- __has_virtual_destructor keyword [C++]
- __has_finalizer keyword [C++]
- __is_union keyword [C++]
- __has_assign keyword [C++]
- __has_trivial_destructor keyword [C++]
- __is_polymorphic keyword [C++]
- __is_enum keyword [C++]
- __is_simple_value_class keyword [C++]
- __has_trivial_constructor keyword [C++]
ms.assetid: cd440630-0394-48c0-a16b-1580b6ef5844
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: c68e354e70f3976bffba12020ff1175142715fbc
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/08/2018
ms.locfileid: "33862419"
---
# <a name="compiler-support-for-type-traits-c-component-extensions"></a>Obsługa cech typu w kompilatorze (C++ Component Extensions)
Obsługa kompilatora *wpisz cech*, które wskazują różnych cech typu w czasie kompilacji.  
  
## <a name="all-runtimes"></a>Wszystkie środowiska wykonawcze  
 **Uwagi**  
  
 Cech typu w kompilatorze jest przydatny dla programistów, którzy bibliotek.  
  
 Poniższa lista zawiera cech typu, które są obsługiwane przez kompilator. Wszystkie typ zwracany cech `false` Jeśli nie jest spełniony warunek określony przez nazwę typu cechy.  
  
 (Na poniższej liście, przykłady kodu są zapisywane tylko w języku C + +/ CLI. Ale obsługiwana jest również odpowiedniego typu cechy w [!INCLUDE[cppwrt](../build/reference/includes/cppwrt_md.md)] Jeżeli nie określono inaczej. Termin "typ platformy" odwołuje się do typów środowiska wykonawczego systemu Windows lub typów środowiska wykonawczego języka wspólnego.)  
  
-   `__has_assign(` `type` `)`  
  
     Zwraca wartość PRAWDA, jeśli platforma lub typ macierzysty ma operatora przypisania kopii.  
  
    ```  
  
    ref struct R {  
    void operator=(R% r) {}  
    };  
  
    int main() {  
    System::Console::WriteLine(__has_assign(R));  
    }  
  
    ```  
  
-   `__has_copy(` `type` `)`  
  
     Zwraca wartość PRAWDA, jeśli platforma lub natywny typ ma konstruktora kopiującego.  
  
    ```  
  
    ref struct R {  
    R(R% r) {}  
    };  
  
    int main() {  
    System::Console::WriteLine(__has_copy(R));  
    }  
  
    ```  
  
-   `__has_finalizer(` `type` `)`  
  
     (Nieobsługiwane w [!INCLUDE[cppwrt](../build/reference/includes/cppwrt_md.md)].) Zwraca wartość PRAWDA, jeśli typ CLR ma finalizator. Zobacz [destruktory i finalizatory w porady: Definiowanie oraz stosowanie klas i struktur (C + +/ CLI)](../dotnet/how-to-define-and-consume-classes-and-structs-cpp-cli.md#BKMK_Destructors_and_finalizers) Aby uzyskać więcej informacji.  
  
    ```  
  
    using namespace System;  
    ref struct R {  
    ~R() {}  
    protected:  
    !R() {}  
    };  
  
    int main() {  
    Console::WriteLine(__has_finalizer(R));  
    }  
  
    ```  
  
-   `__has_nothrow_assign(` `type` `)`  
  
     Zwraca wartość PRAWDA, jeśli operatora przypisania kopii ma specyfikację wyjątku puste.  
  
    ```  
  
    #include <stdio.h>  
    struct S {  
    void operator=(S& r) throw() {}  
    };  
  
    int main() {  
    __has_nothrow_assign(S) == true ?  
    printf("true\n") : printf("false\n");  
    }  
  
    ```  
  
-   `__has_nothrow_constructor(` `type` `)`  
  
     Zwraca wartość PRAWDA, jeśli Specyfikacja wyjątku pusty ma domyślnego konstruktora.  
  
    ```  
  
    #include <stdio.h>  
    struct S {  
    S() throw() {}  
    };  
  
    int main() {  
    __has_nothrow_constructor(S) == true ?  
    printf("true\n") : printf("false\n");  
    }  
  
    ```  
  
-   `__has_nothrow_copy(` `type` `)`  
  
     Zwraca wartość PRAWDA, jeśli Konstruktor kopiujący ma specyfikację wyjątku puste.  
  
    ```  
  
    #include <stdio.h>  
    struct S {  
    S(S& r) throw() {}  
    };  
  
    int main() {  
    __has_nothrow_copy(S) == true ?  
    printf("true\n") : printf("false\n");  
    }  
  
    ```  
  
-   `__has_trivial_assign(` `type` `)`  
  
     Zwraca wartość PRAWDA, jeśli typ ma operatora przypisania trivial, generowane przez kompilator.  
  
    ```  
  
    #include <stdio.h>  
    struct S {};  
  
    int main() {  
    __has_trivial_assign(S) == true ?  
    printf("true\n") : printf("false\n");  
    }  
  
    ```  
  
-   `__has_trivial_constructor(` `type` `)`  
  
     Zwraca wartość PRAWDA, jeśli typ ma konstruktora trivial, generowane przez kompilator.  
  
    ```  
  
    #include <stdio.h>  
    struct S {};  
  
    int main() {  
    __has_trivial_constructor(S) == true ?  
    printf("true\n") : printf("false\n");  
    }  
  
    ```  
  
-   `__has_trivial_copy(` `type` `)`  
  
     Zwraca wartość PRAWDA, jeśli typ ma konstruktora kopiującego trivial, generowane przez kompilator.  
  
    ```  
  
    #include <stdio.h>  
    struct S {};  
  
    int main() {  
    __has_trivial_copy(S) == true ?  
    printf("true\n") : printf("false\n");  
    }  
  
    ```  
  
-   `__has_trivial_destructor(` `type` `)`  
  
     Zwraca wartość PRAWDA, jeśli typ ma destruktora trivial, generowane przez kompilator.  
  
    ```  
  
    // has_trivial_destructor.cpp  
    #include <stdio.h>  
    struct S {};  
  
    int main() {  
    __has_trivial_destructor(S) == true ?  
    printf("true\n") : printf("false\n");  
    }  
  
    ```  
  
-   `__has_user_destructor(` `type` `)`  
  
     Zwraca wartość PRAWDA, jeśli platforma lub typ macierzysty ma destruktor zadeklarowanych przez użytkownika.  
  
    ```  
  
    // has_user_destructor.cpp  
  
    using namespace System;  
    ref class R {  
    ~R() {}  
    };  
  
    int main() {  
    Console::WriteLine(__has_user_destructor(R));  
    }  
  
    ```  
  
-   `__has_virtual_destructor(` `type` `)`  
  
     Zwraca wartość PRAWDA, jeśli typ ma destruktor wirtualny.  
  
     `__has_virtual_destructor` destruktor wirtualny jest również działa na typy platform i wszelkie destruktora zdefiniowane przez użytkownika w typie platformy.  
  
    ```  
  
    // has_virtual_destructor.cpp  
    #include <stdio.h>  
    struct S {  
    virtual ~S() {}  
    };  
  
    int main() {  
    __has_virtual_destructor(S) == true ?  
    printf("true\n") : printf("false\n");  
    }  
  
    ```  
  
-   `__is_abstract(` `type` `)`  
  
     Zwraca wartość PRAWDA, jeśli typ jest typem abstrakcyjnym. Aby uzyskać więcej informacji na typach abstrakcyjnych macierzystego, zobacz [abstrakcyjny](../windows/abstract-cpp-component-extensions.md).  
  
     `__is_abstract` działa także dla typy platform. Interfejs z co najmniej jeden element członkowski jest abstrakcyjna, ponieważ jest typem odwołania z co najmniej jeden abstrakcyjny element członkowski. Aby uzyskać więcej informacji na typach abstrakcyjnych platformy, zobacz [klasy abstrakcyjne](../cpp/abstract-classes-cpp.md)  
  
    ```  
  
    // is_abstract.cpp  
    #include <stdio.h>  
    struct S {  
    virtual void Test() = 0;  
    };  
  
    int main() {  
    __is_abstract(S) == true ?  
    printf("true\n") : printf("false\n");  
    }  
  
    ```  
  
-   `__is_base_of(` `base` `,` `derived` `)`  
  
     Zwraca wartość PRAWDA, jeśli pierwszy typ jest klasę podstawową drugi typ, jeśli oba typy są takie same.  
  
     `__is_base_of` również działa na typy platform. Na przykład, zostanie zwrócona wartość PRAWDA, jeśli jest pierwszy typ [interfejsu klasy](../windows/interface-class-cpp-component-extensions.md) i drugi typ implementuje interfejs.  
  
    ```  
  
    // is_base_of.cpp  
    #include <stdio.h>  
    struct S {};  
    struct T : public S {};  
  
    int main() {  
    __is_base_of(S, T) == true ?  
    printf("true\n") : printf("false\n");  
  
    __is_base_of(S, S) == true ?  
    printf("true\n") : printf("false\n");  
    }  
  
    ```  
  
-   `__is_class(` `type` `)`  
  
     Zwraca wartość PRAWDA, jeśli typ jest natywny klasie lub strukturze.  
  
    ```  
  
    #include <stdio.h>  
    struct S {};  
  
    int main() {  
    __is_class(S) == true ?  
    printf("true\n") : printf("false\n");  
    }  
  
    ```  
  
-   `__is_convertible_to(` `from` `,`  `to` `)`  
  
     Zwraca wartość PRAWDA, jeśli pierwszy typ można przekonwertować na typ drugiego.  
  
    ```  
  
    #include <stdio.h>  
    struct S {};  
    struct T : public S {};  
  
    int main() {  
    S * s = new S;  
    T * t = new T;  
    s = t;  
    __is_convertible_to(T, S) == true ?  
    printf("true\n") : printf("false\n");  
    }  
  
    ```  
  
-   `__is_delegate(` `type` `)`  
  
     Zwraca wartość true, jeśli `type` to delegate. Aby uzyskać więcej informacji, zobacz [delegata (C++ Component Extensions)](../windows/delegate-cpp-component-extensions.md).  
  
    ```  
  
    delegate void MyDel();  
    int main() {  
    System::Console::WriteLine(__is_delegate(MyDel));  
    }  
  
    ```  
  
-   `__is_empty(` `type` `)`  
  
     Zwraca wartość PRAWDA, jeśli typ nie ma żadnych członków danych wystąpienia.  
  
    ```  
  
    #include <stdio.h>  
    struct S {  
    int Test() {}  
    static int i;  
    };  
    int main() {  
    __is_empty(S) == true ?  
    printf("true\n") : printf("false\n");  
    }  
  
    ```  
  
-   `__is_enum(` `type` `)`  
  
     Zwraca wartość PRAWDA, jeśli typ jest natywnym wyliczeniem.  
  
    ```  
  
    // is_enum.cpp  
    #include <stdio.h>  
    enum E { a, b };  
  
    struct S {  
    enum E2 { c, d };  
    };  
  
    int main() {  
    __is_enum(E) == true ?  
    printf("true\n") : printf("false\n");  
  
    __is_enum(S::E2) == true ?  
    printf("true\n") : printf("false\n");  
    }  
  
    ```  
  
-   `__is_interface_class(` `type` `)`  
  
     Zwraca wartość PRAWDA, jeśli przekazany interfejs platformy. Aby uzyskać więcej informacji, zobacz [interfejsu klasy](../windows/interface-class-cpp-component-extensions.md).  
  
    ```  
  
    // is_interface_class.cpp  
  
    using namespace System;  
    interface class I {};  
    int main() {  
    Console::WriteLine(__is_interface_class(I));  
    }  
  
    ```  
  
-   `__is_pod(` `type` `)`  
  
     Zwraca wartość PRAWDA, jeśli typ jest klasy lub union ma konstruktora lub prywatnych lub chronionych elementów członkowskich niestatyczna, nie klas podstawowych i żadnych funkcji wirtualnych. Zobacz stanowiskami C++ standard sekcje 8.5.1/1, 9/4 i 3.9/10, aby uzyskać więcej informacji.  
  
     `__is_pod` Zwraca wartość false w typach podstawowych.  
  
    ```  
  
    #include <stdio.h>  
    struct S {};  
  
    int main() {  
    __is_pod(S) == true ?  
    printf("true\n") : printf("false\n");  
    }  
  
    ```  
  
-   `__is_polymorphic(` `type` `)`  
  
     Zwraca wartość PRAWDA, jeśli typ macierzysty ma funkcje wirtualne.  
  
    ```  
  
    #include <stdio.h>  
    struct S {  
    virtual void Test(){}  
    };  
  
    int main() {  
    __is_polymorphic(S) == true ?  
    printf("true\n") : printf("false\n");  
    }  
  
    ```  
  
-   `__is_ref_array(` `type` `)`  
  
     Zwraca wartość PRAWDA, jeśli przekazany tablicy platformy. Aby uzyskać więcej informacji, zobacz [tablice](../windows/arrays-cpp-component-extensions.md).  
  
    ```  
  
    using namespace System;  
    int main() {  
    array<int>^ x = gcnew array<int>(10);  
    Console::WriteLine(__is_ref_array(array<int>));  
    }  
  
    ```  
  
-   `__is_ref_class(` `type` `)`  
  
     Zwraca wartość PRAWDA, jeśli klasa odwołania przekazany. Aby uzyskać więcej informacji w typach referencyjnych zdefiniowane przez użytkownika, zobacz [klas i struktur](../windows/classes-and-structs-cpp-component-extensions.md).  
  
    ```  
  
    using namespace System;  
    ref class R {};  
    int main() {  
    Console::WriteLine(__is_ref_class(Buffer));  
    Console::WriteLine(__is_ref_class(R));  
    }  
  
    ```  
  
-   `__is_sealed(` `type` `)`  
  
     Zwraca wartość PRAWDA, jeśli platforma lub typ macierzysty oznaczony jako sealed. Aby uzyskać więcej informacji, zobacz [zapieczętowanego](../windows/sealed-cpp-component-extensions.md).  
  
    ```  
  
    ref class R sealed{};  
    int main() {  
    System::Console::WriteLine(__is_sealed(R));  
    }  
  
    ```  
  
-   `__is_simple_value_class(` `type` `)`  
  
     Zwraca wartość PRAWDA, jeśli przekazany typ wartości, która nie zawiera żadnych odwołań do stosu zebranego przez pamięci. Aby uzyskać więcej informacji o typach wartości zdefiniowanej przez użytkownika, zobacz [klas i struktur](../windows/classes-and-structs-cpp-component-extensions.md).  
  
    ```  
  
    using namespace System;  
    ref class R {};  
    value struct V {};  
    value struct V2 {  
    R ^ r;   // not a simnple value type  
    };  
  
    int main() {  
    Console::WriteLine(__is_simple_value_class(V));  
    Console::WriteLine(__is_simple_value_class(V2));  
    }  
  
    ```  
  
-   `__is_union(` `type` `)`  
  
     Zwraca wartość PRAWDA, jeśli typ union.  
  
    ```  
  
    #include <stdio.h>  
    union A {  
    int i;  
    float f;  
    };  
  
    int main() {  
    __is_union(A) == true ?  
    printf("true\n") : printf("false\n");  
    }  
  
    ```  
  
-   `__is_value_class(` `type` `)`  
  
     Zwraca wartość PRAWDA, jeśli przekazany typ wartości. Aby uzyskać więcej informacji o typach wartości zdefiniowanej przez użytkownika, zobacz [klas i struktur](../windows/classes-and-structs-cpp-component-extensions.md).  
  
    ```  
  
    value struct V {};  
  
    int main() {  
    System::Console::WriteLine(__is_value_class(V));  
    }  
  
    ```  
  
## <a name="windows-runtime"></a>Środowisko wykonawcze systemu Windows  
 **Uwagi**  
  
 `__has_finalizer(` *Typu* `)` typu cechy nie jest obsługiwana, ponieważ ta platforma nie obsługuje finalizatory.  
  
### <a name="requirements"></a>Wymagania  
 — Opcja kompilatora: **/ZW**  
  
## <a name="common-language-runtime"></a>środowiska uruchomieniowe w trakcie wykonania 
 **Uwagi**  
  
 (Istnieją nie uwagi specyficzne dla platformy, dla tej funkcji.)  
  
### <a name="requirements"></a>Wymagania  
 — Opcja kompilatora:   **/CLR**  
  
### <a name="examples"></a>Przykłady  
 **Przykład**  
  
 Poniższy przykładowy kod przedstawia sposób ujawniać typu cechy kompilatora dla za pomocą szablonu klasy **/CLR** kompilacji. Aby uzyskać więcej informacji, zobacz [środowiska wykonawczego systemu Windows i zarządzane szablony](../windows/windows-runtime-and-managed-templates-cpp-component-extensions.md).  
  
```  
// compiler_type_traits.cpp  
// compile with: /clr  
using namespace System;  
  
template <class T>  
ref struct is_class {  
   literal bool value = __is_ref_class(T);  
};  
  
ref class R {};  
  
int main () {  
   if (is_class<R>::value)  
      Console::WriteLine("R is a ref class");  
   else  
      Console::WriteLine("R is not a ref class");  
}  
```  
  
 **Output**  
  
```Output  
R is a ref class  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Component Extensions dla platform środowiska uruchomieniowego](../windows/component-extensions-for-runtime-platforms.md)