---
title: Obsługa kompilatora dla cech typu (C++/CLI i C++/CX)
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
ms.openlocfilehash: 1bfb4308dc76e3393eceddf8dedd6d11e73adc17
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/24/2020
ms.locfileid: "80172533"
---
# <a name="compiler-support-for-type-traits-ccli-and-ccx"></a>Obsługa kompilatora dla cech typu (C++/CLI i C++/CX)

Kompilator firmy C++ Microsoft obsługuje *cechy typów* dla C++rozszerzeń/CLI i C++/CX, które wskazują różne cechy typu w czasie kompilacji.

## <a name="all-runtimes"></a>Wszystkie środowiska wykonawcze

### <a name="remarks"></a>Uwagi

Cechy typu są szczególnie przydatne dla programistów, którzy zapisują biblioteki.

Poniższa lista zawiera cechy typów, które są obsługiwane przez kompilator. Wszystkie cechy typu zwracają **wartość false** , jeśli warunek określony przez nazwę cechy typu nie jest spełniony.

(Na poniższej liście przykłady kodu są zapisywane tylko w C++/CLI. Jednak odpowiednia cecha typu jest również obsługiwana w C++/CX, chyba że określono inaczej. Termin "typ platformy" odnosi się do typów środowisko wykonawcze systemu Windows lub typów środowiska uruchomieniowego języka wspólnego.)

- *typ* `__has_assign(` `)`

   Zwraca **wartość PRAWDA** , jeśli platforma lub typ natywny ma operator przypisania kopiowania.

    ```cpp
    ref struct R {
    void operator=(R% r) {}
    };

    int main() {
    System::Console::WriteLine(__has_assign(R));
    }
    ```

- *typ* `__has_copy(` `)`

   Zwraca **wartość PRAWDA** , jeśli platforma lub typ natywny ma Konstruktor kopiujący.

    ```cpp
    ref struct R {
    R(R% r) {}
    };

    int main() {
    System::Console::WriteLine(__has_copy(R));
    }
    ```

- *typ* `__has_finalizer(` `)`

   (Nieobsługiwane w C++/CX.) Zwraca **wartość true** , jeśli typ CLR ma finalizator. Zobacz [destruktory i finalizatory w instrukcje: Definiowanie i używanie klas i struktur (C++/CLI)](../dotnet/how-to-define-and-consume-classes-and-structs-cpp-cli.md#BKMK_Destructors_and_finalizers) , aby uzyskać więcej informacji.

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

- *typ* `__has_nothrow_assign(` `)`

   Zwraca **wartość true** , jeśli operator przypisania kopiowania ma pustą specyfikację wyjątku.

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

- *typ* `__has_nothrow_constructor(` `)`

   Zwraca **wartość true** , jeśli domyślny Konstruktor ma pustą specyfikację wyjątku.

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

- *typ* `__has_nothrow_copy(` `)`

   Zwraca **wartość true** , jeśli Konstruktor kopiujący ma pustą specyfikację wyjątku.

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

- *typ* `__has_trivial_assign(` `)`

   Zwraca **wartość true** , jeśli typ ma prosty, wygenerowany przez kompilator operator przypisywania.

    ```cpp
    #include <stdio.h>
    struct S {};

    int main() {
    __has_trivial_assign(S) == true ?
    printf("true\n") : printf("false\n");
    }
    ```

- *typ* `__has_trivial_constructor(` `)`

   Zwraca **wartość true** , jeśli typ ma prosty, wygenerowany przez kompilator Konstruktor.

    ```cpp
    #include <stdio.h>
    struct S {};

    int main() {
    __has_trivial_constructor(S) == true ?
    printf("true\n") : printf("false\n");
    }
    ```

- *typ* `__has_trivial_copy(` `)`

   Zwraca **wartość true** , jeśli typ ma prosty, wygenerowany przez kompilator Konstruktor kopiujący.

    ```cpp
    #include <stdio.h>
    struct S {};

    int main() {
    __has_trivial_copy(S) == true ?
    printf("true\n") : printf("false\n");
    }
    ```

- *typ* `__has_trivial_destructor(` `)`

   Zwraca **wartość true** , jeśli typ ma prosty, wygenerowany przez kompilator destruktor.

    ``` cpp
    // has_trivial_destructor.cpp
    #include <stdio.h>
    struct S {};

    int main() {
    __has_trivial_destructor(S) == true ?
    printf("true\n") : printf("false\n");
    }
    ```

- *typ* `__has_user_destructor(` `)`

   Zwraca **wartość PRAWDA** , jeśli platforma lub typ natywny ma destruktor zadeklarowany przez użytkownika.

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

- *typ* `__has_virtual_destructor(` `)`

   Zwraca **wartość true** , jeśli typ ma destruktor wirtualny.

   `__has_virtual_destructor` również działa na typach platform, a każdy destruktor zdefiniowany przez użytkownika w typie platformy jest destruktorem wirtualnym.

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

- *typ* `__is_abstract(` `)`

   Zwraca **wartość true** , jeśli typ jest typem abstrakcyjnym. Aby uzyskać więcej informacji na temat natywnych typów abstrakcyjnych, zobacz [klasy abstrakcyjne](../cpp/abstract-classes-cpp.md).

   `__is_abstract` również działa dla typów platform. Interfejs z co najmniej jednym elementem członkowskim jest typem abstrakcyjnym, podobnie jak typ referencyjny z co najmniej jednym abstrakcyjną składową. Aby uzyskać więcej informacji na temat typów platform abstrakcyjnych, zobacz [abstract](abstract-cpp-component-extensions.md).

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

   Zwraca **wartość true** , jeśli pierwszy typ jest klasą bazową drugiego typu, jeśli oba typy są takie same.

   `__is_base_of` również działa na typach platform. Na przykład zwróci **wartość true** , jeśli pierwszy typ jest [klasą interfejsu](interface-class-cpp-component-extensions.md) , a drugi typ implementuje interfejs.

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

- *typ* `__is_class(` `)`

   Zwraca **wartość true** , jeśli typ jest klasą natywną lub strukturą.

    ```cpp
    #include <stdio.h>
    struct S {};

    int main() {
    __is_class(S) == true ?
    printf("true\n") : printf("false\n");
    }
    ```

- `__is_convertible_to(` `from` `,``to` `)`

   Zwraca **wartość true** , jeśli pierwszy typ można przekonwertować na drugi typ.

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

- *typ* `__is_delegate(` `)`

   Zwraca **wartość true** , jeśli `type` jest delegatem. Aby uzyskać więcej informacji, zobacz [DelegatC++(/CLI C++and/CX)](delegate-cpp-component-extensions.md).

    ```cpp
    delegate void MyDel();
    int main() {
    System::Console::WriteLine(__is_delegate(MyDel));
    }
    ```

- *typ* `__is_empty(` `)`

   Zwraca **wartość true** , jeśli typ nie ma żadnych elementów członkowskich danych wystąpienia.

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

- *typ* `__is_enum(` `)`

   Zwraca **wartość true** , jeśli typ jest natywnym wyliczeniem.

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

- *typ* `__is_interface_class(` `)`

   Zwraca **wartość true** , jeśli przeszedł interfejs platformy. Aby uzyskać więcej informacji, zobacz [interface class](interface-class-cpp-component-extensions.md).

    ```cpp
    // is_interface_class.cpp

    using namespace System;
    interface class I {};
    int main() {
    Console::WriteLine(__is_interface_class(I));
    }
    ```

- *typ* `__is_pod(` `)`

   Zwraca **wartość true** , jeśli typ jest klasą lub Unią bez konstruktorów lub prywatnych lub chronionych niestatycznych elementów członkowskich, brak klas bazowych i bez funkcji wirtualnych. Aby uzyskać C++ więcej informacji na temat zasobników, zobacz Standard, sekcje 8.5.1/1, 9/4 i 3.9/10.

   `__is_pod` zwróci wartość false dla typów podstawowych.

    ```cpp
    #include <stdio.h>
    struct S {};

    int main() {
    __is_pod(S) == true ?
    printf("true\n") : printf("false\n");
    }
    ```

- *typ* `__is_polymorphic(` `)`

   Zwraca **wartość true** , jeśli typ natywny ma funkcje wirtualne.

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

- *typ* `__is_ref_array(` `)`

   Zwraca **wartość true** , jeśli została przeniesiona tablica platformy. Aby uzyskać więcej informacji, zobacz [tablice](arrays-cpp-component-extensions.md).

    ```cpp
    using namespace System;
    int main() {
    array<int>^ x = gcnew array<int>(10);
    Console::WriteLine(__is_ref_array(array<int>));
    }
    ```

- *typ* `__is_ref_class(` `)`

   Zwraca **wartość true** , jeśli została przeniesiona Klasa referencyjna. Aby uzyskać więcej informacji na temat typów odwołań zdefiniowanych przez użytkownika, zobacz [klasy i struktury](classes-and-structs-cpp-component-extensions.md).

    ```cpp
    using namespace System;
    ref class R {};
    int main() {
    Console::WriteLine(__is_ref_class(Buffer));
    Console::WriteLine(__is_ref_class(R));
    }
    ```

- *typ* `__is_sealed(` `)`

   Zwraca **wartość true** , jeśli została przeniesiona na platformę lub typ natywny oznaczony jako zapieczętowany. Aby uzyskać więcej informacji, zobacz [zapieczętowany](sealed-cpp-component-extensions.md).

    ```cpp
    ref class R sealed{};
    int main() {
    System::Console::WriteLine(__is_sealed(R));
    }
    ```

- *typ* `__is_simple_value_class(` `)`

   Zwraca **wartość true** , jeśli przeszedł typ wartości, który nie zawiera odwołań do sterty zebranych elementów bezużytecznych. Aby uzyskać więcej informacji na temat typów wartości zdefiniowanych przez użytkownika, zobacz [klasy i struktury](classes-and-structs-cpp-component-extensions.md).

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

- *typ* `__is_union(` `)`

   Zwraca **wartość true** , jeśli typ jest Unią.

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

- *typ* `__is_value_class(` `)`

   Zwraca wartość **true** , jeśli przeszedł typ wartości. Aby uzyskać więcej informacji na temat typów wartości zdefiniowanych przez użytkownika, zobacz [klasy i struktury](classes-and-structs-cpp-component-extensions.md).

    ```cpp
    value struct V {};

    int main() {
    System::Console::WriteLine(__is_value_class(V));
    }
    ```

## <a name="windows-runtime"></a>Środowisko wykonawcze systemu Windows

### <a name="remarks"></a>Uwagi

Typ `__has_finalizer(`*typu*`)` nie jest obsługiwany, ponieważ ta platforma nie obsługuje finalizatorów.

### <a name="requirements"></a>Wymagania

Opcja kompilatora: `/ZW`

## <a name="common-language-runtime"></a>środowiska uruchomieniowe w trakcie wykonania

### <a name="remarks"></a>Uwagi

(Nie ma żadnych uwag specyficznych dla platformy dla tej funkcji).

### <a name="requirements"></a>Wymagania

Opcja kompilatora: `/clr`

### <a name="examples"></a>Przykłady

**Przykład**

Poniższy przykład kodu pokazuje, jak używać szablonu klasy, aby uwidocznić cechę typu kompilatora dla kompilacji `/clr`. Aby uzyskać więcej informacji, zobacz [środowisko wykonawcze systemu Windows i szablony zarządzane](windows-runtime-and-managed-templates-cpp-component-extensions.md).

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
