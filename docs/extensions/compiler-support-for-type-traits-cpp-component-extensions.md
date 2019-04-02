---
title: Obsługa cech typu w kompilatorze (C + +/ CLI i C + +/ CX)
ms.date: 10/12/2018
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
ms.openlocfilehash: 5d7b83822d731905a8b2c00624f640998133bc83
ms.sourcegitcommit: 5cecccba0a96c1b4ccea1f7a1cfd91f259cc5bde
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/01/2019
ms.locfileid: "58787289"
---
# <a name="compiler-support-for-type-traits-ccli-and-ccx"></a>Obsługa cech typu w kompilatorze (C + +/ CLI i C + +/ CX)

Microsoft C++ obsługuje kompilatora *typ cechy* C + +/ CLI i C + +/ CX rozszerzenia, które wskazują różne cechy typu w czasie kompilacji.

## <a name="all-runtimes"></a>Wszystkie środowiska wykonawcze

### <a name="remarks"></a>Uwagi

Cechy typu są szczególnie przydatne dla programistów, którzy bibliotek.

Poniższa lista zawiera cech typu, które są obsługiwane przez kompilator. Wszystkie wpisz powrotu cech **false** Jeśli nie jest spełniony warunek określony przez nazwę typu cechy.

(Na poniższej liście przykłady kodu są zapisywane tylko w języku C + +/ interfejsu wiersza polecenia. Ale obsługiwana jest również odpowiedni cech typu w języku C + +/ CX, chyba że określono inaczej. Termin "platform type" odwołuje się do typów środowiska wykonawczego Windows lub popularnych typów środowiska wykonawczego języka.)

- `__has_assign(` *Typ* `)`

   Zwraca **true** Jeśli platforma lub typ natywny zawiera operator przypisania kopiowania.

    ```cpp
    ref struct R {
    void operator=(R% r) {}
    };

    int main() {
    System::Console::WriteLine(__has_assign(R));
    }
    ```

- `__has_copy(` *Typ* `)`

   Zwraca **true** Jeśli platforma lub typ natywny ma Konstruktor kopiujący.

    ```cpp
    ref struct R {
    R(R% r) {}
    };

    int main() {
    System::Console::WriteLine(__has_copy(R));
    }
    ```

- `__has_finalizer(` *Typ* `)`

   (Nieobsługiwane w języku C + +/ CX.) Zwraca **true** Jeśli typ CLR ma finalizator. Zobacz [destruktory i finalizatory w sposób: Definiowanie oraz stosowanie klas i struktur (C + +/ CLI)](../dotnet/how-to-define-and-consume-classes-and-structs-cpp-cli.md#BKMK_Destructors_and_finalizers) Aby uzyskać więcej informacji.

    ```cpp
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

- `__has_nothrow_assign(` *Typ* `)`

   Zwraca **true** Jeśli specyfikacja wyjątku pusty operator przypisania kopiowania.

    ```cpp
    #include <stdio.h>
    struct S {
    void operator=(S& r) throw() {}
    };

    int main() {
    __has_nothrow_assign(S) == true ?
    printf("true\n") : printf("false\n");
    }
    ```

- `__has_nothrow_constructor(` *Typ* `)`

   Zwraca **true** Jeśli specyfikacja wyjątku pusty konstruktor domyślny.

    ```cpp
    #include <stdio.h>
    struct S {
    S() throw() {}
    };

    int main() {
    __has_nothrow_constructor(S) == true ?
    printf("true\n") : printf("false\n");
    }
    ```

- `__has_nothrow_copy(` *Typ* `)`

   Zwraca **true** Jeśli Konstruktor kopiujący ma specyfikację wyjątku puste.

    ```cpp
    #include <stdio.h>
    struct S {
    S(S& r) throw() {}
    };

    int main() {
    __has_nothrow_copy(S) == true ?
    printf("true\n") : printf("false\n");
    }
    ```

- `__has_trivial_assign(` *Typ* `)`

   Zwraca **true** Jeśli typ ma operatora przypisania prosta, generowane przez kompilator.

    ```cpp
    #include <stdio.h>
    struct S {};

    int main() {
    __has_trivial_assign(S) == true ?
    printf("true\n") : printf("false\n");
    }
    ```

- `__has_trivial_constructor(` *Typ* `)`

   Zwraca **true** Jeśli typ ma konstruktora prosta, generowane przez kompilator.

    ```cpp
    #include <stdio.h>
    struct S {};

    int main() {
    __has_trivial_constructor(S) == true ?
    printf("true\n") : printf("false\n");
    }
    ```

- `__has_trivial_copy(` *Typ* `)`

   Zwraca **true** Jeśli typ ma konstruktora kopiującego prosta, generowane przez kompilator.

    ```cpp
    #include <stdio.h>
    struct S {};

    int main() {
    __has_trivial_copy(S) == true ?
    printf("true\n") : printf("false\n");
    }
    ```

- `__has_trivial_destructor(` *Typ* `)`

   Zwraca **true** Jeśli typ ma destruktor prosta, generowane przez kompilator.

    ``` cpp
    // has_trivial_destructor.cpp
    #include <stdio.h>
    struct S {};

    int main() {
    __has_trivial_destructor(S) == true ?
    printf("true\n") : printf("false\n");
    }
    ```

- `__has_user_destructor(` *Typ* `)`

   Zwraca **true** Jeśli platforma lub typ natywny ma destruktor zgłoszone przez użytkownika.

    ```cpp
    // has_user_destructor.cpp

    using namespace System;
    ref class R {
    ~R() {}
    };

    int main() {
    Console::WriteLine(__has_user_destructor(R));
    }
    ```

- `__has_virtual_destructor(` *Typ* `)`

   Zwraca **true** Jeśli typ ma destruktor wirtualny.

   `__has_virtual_destructor` destruktor wirtualny jest również działa na typy platform i dowolny destruktor zdefiniowany przez użytkownika w typie platformy.

    ```cpp
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

- `__is_abstract(` *Typ* `)`

   Zwraca **true** Jeśli typ jest typem abstrakcyjnym. Aby uzyskać więcej informacji dotyczących natywnych typów abstrakcyjnych, zobacz [klasy abstrakcyjne](../cpp/abstract-classes-cpp.md).

   `__is_abstract` działa również typy platform. Interfejs z co najmniej jednego członka jest typem abstrakcyjnym, podobnie jak typ odwołania z co najmniej jedną abstrakcyjną składową. Aby uzyskać więcej informacji na typy abstrakcyjne platform, zobacz [abstrakcyjne](abstract-cpp-component-extensions.md).

    ```cpp
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

- `__is_base_of(` `base` `,` `derived` `)`

   Zwraca **true** Jeśli pierwszy typ jest klasą bazową dla drugi typ, jeśli oba typy są takie same.

   `__is_base_of` działa również na typy platform. Na przykład, zwróci **true** Jeśli pierwszy typ to [interfejsu klasy](interface-class-cpp-component-extensions.md) i drugi typ implementuje interfejs.

    ```cpp
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

- `__is_class(` *Typ* `)`

   Zwraca **true** Jeśli typ jest natywny klasy lub struktury.

    ```cpp
    #include <stdio.h>
    struct S {};

    int main() {
    __is_class(S) == true ?
    printf("true\n") : printf("false\n");
    }
    ```

- `__is_convertible_to(` `from` `,`  `to` `)`

   Zwraca **true** Jeśli można przekonwertować na drugi typ pierwszego typu.

    ```cpp
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

- `__is_delegate(` *Typ* `)`

   Zwraca **true** Jeśli `type` jest delegat. Aby uzyskać więcej informacji, zobacz [delegowania (C + +/ CLI i C + +/ CX)](delegate-cpp-component-extensions.md).

    ```cpp
    delegate void MyDel();
    int main() {
    System::Console::WriteLine(__is_delegate(MyDel));
    }
    ```

- `__is_empty(` *Typ* `)`

   Zwraca **true** Jeśli typ nie ma żadnych składowych danych wystąpienia.

    ```cpp
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

- `__is_enum(` *Typ* `)`

   Zwraca **true** Jeśli typ jest natywnym wyliczeniem.

    ```cpp
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

- `__is_interface_class(` *Typ* `)`

   Zwraca **true** jeśli przekazany interfejsu platformy. Aby uzyskać więcej informacji, zobacz [interfejsu klasy](interface-class-cpp-component-extensions.md).

    ```cpp
    // is_interface_class.cpp

    using namespace System;
    interface class I {};
    int main() {
    Console::WriteLine(__is_interface_class(I));
    }
    ```

- `__is_pod(` *Typ* `)`

   Zwraca **true** Jeśli typ jest klasą lub Unii z żaden konstruktor lub prywatnych lub chronionych niestatycznych elementów członkowskich, nie mają klas bazowych i żadnych funkcji wirtualnych. Zobacz języka C++ w warstwie standardowa sekcje 8.5.1/1, 9/4 i 3.9/10, aby uzyskać więcej informacji o zasobników.

   `__is_pod` Zwraca wartość false dla typów podstawowych.

    ```cpp
    #include <stdio.h>
    struct S {};

    int main() {
    __is_pod(S) == true ?
    printf("true\n") : printf("false\n");
    }
    ```

- `__is_polymorphic(` *Typ* `)`

   Zwraca **true** Jeśli typ natywny ma funkcje wirtualne.

    ```cpp
    #include <stdio.h>
    struct S {
    virtual void Test(){}
    };

    int main() {
    __is_polymorphic(S) == true ?
    printf("true\n") : printf("false\n");
    }
    ```

- `__is_ref_array(` *Typ* `)`

   Zwraca **true** Jeśli przekazana tablica platformy. Aby uzyskać więcej informacji, zobacz [tablic](arrays-cpp-component-extensions.md).

    ```cpp
    using namespace System;
    int main() {
    array<int>^ x = gcnew array<int>(10);
    Console::WriteLine(__is_ref_array(array<int>));
    }
    ```

- `__is_ref_class(` *Typ* `)`

   Zwraca **true** jeśli przekazany klasy odniesienia. Aby uzyskać więcej informacji na temat typów odwołań zdefiniowanych przez użytkownika, zobacz [klas i struktur](classes-and-structs-cpp-component-extensions.md).

    ```cpp
    using namespace System;
    ref class R {};
    int main() {
    Console::WriteLine(__is_ref_class(Buffer));
    Console::WriteLine(__is_ref_class(R));
    }
    ```

- `__is_sealed(` *Typ* `)`

   Zwraca **true** jeśli przekazany platformy lub typem natywnym, oznaczone jako zapieczętowany. Aby uzyskać więcej informacji, zobacz [zapieczętowanego](sealed-cpp-component-extensions.md).

    ```cpp
    ref class R sealed{};
    int main() {
    System::Console::WriteLine(__is_sealed(R));
    }
    ```

- `__is_simple_value_class(` *Typ* `)`

   Zwraca **true** jeśli przekazany typ wartości, która nie zawiera żadnych odwołań do stosu odśmieconej pamięci. Aby uzyskać więcej informacji na temat typów zdefiniowanych przez użytkownika wartości, zobacz [klas i struktur](classes-and-structs-cpp-component-extensions.md).

    ```cpp
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

- `__is_union(` *Typ* `)`

   Zwraca **true** Jeśli typ Unii.

    ```cpp
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

- `__is_value_class(` *Typ* `)`

   Zwraca **true** jeśli przekazany typ wartości. Aby uzyskać więcej informacji na temat typów zdefiniowanych przez użytkownika wartości, zobacz [klas i struktur](classes-and-structs-cpp-component-extensions.md).

    ```cpp
    value struct V {};

    int main() {
    System::Console::WriteLine(__is_value_class(V));
    }
    ```

## <a name="windows-runtime"></a>Środowisko wykonawcze systemu Windows

### <a name="remarks"></a>Uwagi

`__has_finalizer(` *Typu* `)` cechy typu nie jest obsługiwana, ponieważ ta platforma nie obsługuje finalizatorów.

### <a name="requirements"></a>Wymagania

— Opcja kompilatora: `/ZW`

## <a name="common-language-runtime"></a>środowiska uruchomieniowe w trakcie wykonania

### <a name="remarks"></a>Uwagi

(Nie ma żadnych uwag specyficznych dla platformy, dla tej funkcji).

### <a name="requirements"></a>Wymagania

— Opcja kompilatora: `/clr`

### <a name="examples"></a>Przykłady

**Przykład**

Poniższy przykład kodu pokazuje sposób używania szablonu klasy do udostępnienia typu cechy kompilatora dla `/clr` kompilacji. Aby uzyskać więcej informacji, zobacz [środowisko wykonawcze Windows i zarządzane szablony](windows-runtime-and-managed-templates-cpp-component-extensions.md).

```cpp
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

```Output
R is a ref class
```

## <a name="see-also"></a>Zobacz też

[Rozszerzenia składników dla platformy .NET i platformy uniwersalnej systemu Windows](component-extensions-for-runtime-platforms.md)