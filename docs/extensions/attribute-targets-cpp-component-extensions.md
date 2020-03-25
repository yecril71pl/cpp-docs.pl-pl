---
title: Cele atrybutu (C++/CLI i C++/CX)
ms.date: 10/12/2018
ms.topic: reference
helpviewer_keywords:
- custom attributes, targets
ms.assetid: b4e6e224-da77-4520-b6e6-b96846e0ebc1
ms.openlocfilehash: fe2c1d27042b51300d01ba70b951b7601d87701e
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/24/2020
ms.locfileid: "80172623"
---
# <a name="attribute-targets-ccli-and-ccx"></a>Cele atrybutu (C++/CLI i C++/CX)

Specyfikatory użycia atrybutów pozwalają określić cele atrybutu.  Każdy atrybut jest zdefiniowany do zastosowania do niektórych elementów języka. Na przykład atrybut może być zdefiniowany do zastosowania tylko do klas i struktur.  Na poniższej liście przedstawiono możliwe elementy składni, w których można użyć atrybutu niestandardowego. Mogą być używane kombinacje tych wartości (za pomocą logicznych lub).

Aby określić element docelowy atrybutu, należy przekazać co najmniej jeden moduł wyliczający <xref:System.AttributeTargets> do <xref:System.AttributeUsageAttribute> podczas definiowania atrybutu.

Poniżej znajduje się lista prawidłowych obiektów docelowych atrybutu:

- `All` (dotyczy wszystkich konstrukcji)

    ```cpp
    using namespace System;
    [AttributeUsage(AttributeTargets::All)]
    ref class Attr : public Attribute {};

    [assembly:Attr];
    ```

- `Assembly` (dotyczy zestawu jako całości)

    ```cpp
    using namespace System;
    [AttributeUsage(AttributeTargets::Assembly)]
    ref class Attr : public Attribute {};

    [assembly:Attr];
    ```

- `Module` (dotyczy modułu jako całości)

    ```cpp
    using namespace System;
    [AttributeUsage(AttributeTargets::Module)]
    ref class Attr : public Attribute {};

    [module:Attr];
    ```

- `Class`

    ```cpp
    using namespace System;
    [AttributeUsage(AttributeTargets::Class)]
    ref class Attr : public System::Attribute {};

    [Attr]   // same as [class:Attr]
    ref class MyClass {};
    ```

- `Struct`

    ```cpp
    using namespace System;
    [AttributeUsage(AttributeTargets::Struct)]
    ref class Attr : public Attribute {};

    [Attr]   // same as [struct:Attr]
    value struct MyStruct{};
    ```

- `enum`

    ```cpp
    using namespace System;
    [AttributeUsage(AttributeTargets::Enum)]
    ref class Attr : public Attribute {};

    [Attr]   // same as [enum:Attr]
    enum struct MyEnum{e, d};
    ```

- `Constructor`

    ```cpp
    using namespace System;
    [AttributeUsage(AttributeTargets::Constructor)]
    ref class Attr : public Attribute {};

    ref struct MyStruct{
    [Attr] MyStruct(){}   // same as [constructor:Attr]
    };
    ```

- `Method`

    ```cpp
    using namespace System;
    [AttributeUsage(AttributeTargets::Method)]
    ref class Attr : public Attribute {};

    ref struct MyStruct{
    [Attr] void Test(){}   // same as [method:Attr]
    };
    ```

- `Property`

    ```cpp
    using namespace System;
    [AttributeUsage(AttributeTargets::Property)]
    ref class Attr : public Attribute {};

    ref struct MyStruct{
    [Attr] property int Test;   // same as [property:Attr]
    };
    ```

- `Field`

    ```cpp
    using namespace System;
    [AttributeUsage(AttributeTargets::Field)]
    ref class Attr : public Attribute {};

    ref struct MyStruct{
    [Attr] int Test;   // same as [field:Attr]
    };
    ```

- `Event`

    ```cpp
    using namespace System;
    [AttributeUsage(AttributeTargets::Event)]
    ref class Attr : public Attribute {};

    delegate void ClickEventHandler(int, double);

    ref struct MyStruct{
    [Attr] event ClickEventHandler^ OnClick;   // same as [event:Attr]
    };
    ```

- `Interface`

    ```cpp
    using namespace System;
    [AttributeUsage(AttributeTargets::Interface)]
    ref class Attr : public Attribute {};

    [Attr]   // same as [event:Attr]
    interface struct MyStruct{};
    ```

- `Parameter`

    ```cpp
    using namespace System;
    [AttributeUsage(AttributeTargets::Parameter)]
    ref class Attr : public Attribute {};

    ref struct MyStruct{
    void Test([Attr] int i);
    void Test2([parameter:Attr] int i);
    };
    ```

- `Delegate`

    ```cpp
    using namespace System;
    [AttributeUsage(AttributeTargets::Delegate)]
    ref class Attr : public Attribute {};

    [Attr] delegate void Test();
    [delegate:Attr] delegate void Test2();
    ```

- `ReturnValue`

    ```cpp
    using namespace System;
    [AttributeUsage(AttributeTargets::ReturnValue)]
    ref class Attr : public Attribute {};

    ref struct MyStruct {
    // Note required specifier
    [returnvalue:Attr] int Test() { return 0; }
    };
    ```

Zazwyczaj atrybut bezpośrednio poprzedza element języka, do którego się odnosi. Jednak w niektórych przypadkach pozycja atrybutu nie jest wystarczająca do określenia zamierzonego celu atrybutu. Rozważmy następujący przykład:

```cpp
[Attr] int MyFn(double x)...
```

Syntaktycznie nie istnieje sposób, aby stwierdzić, czy atrybut jest przeznaczony do zastosowania do metody lub do wartości zwracanej metody (w tym przypadku jest to wartość domyślna metody). W takich przypadkach można użyć specyfikatora użycia atrybutu. Na przykład, aby zastosować atrybut do wartości zwracanej, użyj specyfikatora `returnvalue` w następujący sposób:

```cpp
[returnvalue:Attr] int MyFn(double x)... // applies to return value
```

Specyfikatory użycia atrybutów są wymagane w następujących sytuacjach:

- Aby określić atrybut na poziomie zestawu lub modułu.

- Aby określić, że atrybut ma zastosowanie do wartości zwracanej metody, a nie z metody:

    ```cpp
    [method:Attr] int MyFn(double x)...     // Attr applies to method
    [returnvalue:Attr] int MyFn(double x)...// Attr applies to return value
    [Attr] int MyFn(double x)...            // default: method
    ```

- Aby określić, że atrybut ma zastosowanie do akcesora właściwości, a nie do właściwości:

    ```cpp
    [method:MyAttr(123)] property int Property()
    [property:MyAttr(123)] property int Property()
    [MyAttr(123)] property int get_MyPropy() // default: property
    ```

- Aby określić, że atrybut ma zastosowanie do akcesora zdarzenia, a nie zdarzenia:

    ```cpp
    delegate void MyDel();
    ref struct X {
       [field:MyAttr(123)] event MyDel* MyEvent;   //field
       [event:MyAttr(123)] event MyDel* MyEvent;   //event
       [MyAttr(123)] event MyDel* MyEvent;   // default: event
    }
    ```

Specyfikator użycia atrybutu ma zastosowanie tylko do atrybutu, który bezpośrednio następuje po nim. Czyli

```cpp
[returnvalue:Attr1, Attr2]
```

różni się od

```cpp
[returnvalue:Attr1, returnvalue:Attr2]
```

## <a name="example"></a>Przykład

### <a name="description"></a>Opis

Ten przykład pokazuje, jak określić wiele obiektów docelowych.

### <a name="code"></a>Kod

```cpp
using namespace System;
[AttributeUsage(AttributeTargets::Class | AttributeTargets::Struct, AllowMultiple = true )]
ref struct Attr : public Attribute {
   Attr(bool i){}
   Attr(){}
};

[Attr]
ref class MyClass {};

[Attr]
[Attr(true)]
value struct MyStruct {};
```

## <a name="see-also"></a>Zobacz też

[Atrybuty zdefiniowane przez użytkownika](user-defined-attributes-cpp-component-extensions.md)
