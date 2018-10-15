---
title: Elementy docelowe atrybutu (C + +/ CLI i C + +/ CX) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 10/12/2018
ms.technology:
- cpp-windows
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- custom attributes, targets
ms.assetid: b4e6e224-da77-4520-b6e6-b96846e0ebc1
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 9dfb469bb9dcea8a2c1e197fa7c305d08d155cf1
ms.sourcegitcommit: 3f4e92266737ecb70507871e87dc8e2965ad7e04
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/15/2018
ms.locfileid: "49327783"
---
# <a name="attribute-targets-ccli-and-ccx"></a>Elementy docelowe atrybutu (C + +/ CLI i C + +/ CX)

Specyfikatory użycia atrybutu umożliwiają określenie docelowe atrybuty.  Każdy atrybut jest zdefiniowany dotyczą niektóre elementy języka. Na przykład być stosowana tylko do klasy i struktury można zdefiniować atrybut.  Na poniższej liście przedstawiono możliwe elementy składni, w których można użyć atrybutu niestandardowego. Kombinacje tych wartości (przy użyciu logicznych lub) mogą być używane.

Aby określić element docelowy atrybutu, aby przekazać co najmniej jeden <xref:System.AttributeTargets> moduły wyliczające do <xref:System.AttributeUsageAttribute> podczas definiowania atrybutu.

Oto lista elementów docelowych prawidłowego atrybutu:

- `All` (dotyczy wszystkich konstrukcji)

    ```cpp
    using namespace System;
    [AttributeUsage(AttributeTargets::All)]
    ref class Attr : public Attribute {};

    [assembly:Attr];
    ```

- `Assembly` (dotyczy całego zestawu)

    ```cpp
    using namespace System;
    [AttributeUsage(AttributeTargets::Assembly)]
    ref class Attr : public Attribute {};

    [assembly:Attr];
    ```

- `Module` (dotyczy moduł jako całość)

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

Zazwyczaj atrybut bezpośrednio poprzedza element języka, do której jest stosowany. W niektórych przypadkach, pozycja atrybut nie jest wystarczające, aby określić docelową ten atrybut. Rozważmy następujący przykład:

```cpp
[Attr] int MyFn(double x)...
```

Syntaktycznie, nie ma żadnego sposobu, aby poinformować, jeśli ten atrybut jest przeznaczony do zastosowania do metody lub wartość zwracaną metody (w tym przypadku domyślnie metody). W takich przypadkach specyfikatorze użycia atrybutu może być używany. Na przykład aby atrybutu, dotyczy wartości zwracanej, należy użyć `returnvalue` specyfikator w następujący sposób:

```cpp
[returnvalue:Attr] int MyFn(double x)... // applies to return value
```

Specyfikatory użycia atrybutu są wymagane w następujących sytuacjach:

- Aby określić atrybut na poziomie zestawu lub modułu.

- Aby określić, czy atrybut dotyczy wartości zwracanej metody, nie metody:

    ```cpp
    [method:Attr] int MyFn(double x)...     // Attr applies to method
    [returnvalue:Attr] int MyFn(double x)...// Attr applies to return value
    [Attr] int MyFn(double x)...            // default: method
    ```

- Aby określić, że atrybut ma zastosowanie do właściwości metody dostępu właściwość nie:

    ```cpp
    [method:MyAttr(123)] property int Property()  
    [property:MyAttr(123)] property int Property()  
    [MyAttr(123)] property int get_MyPropy() // default: property
    ```

- Aby określić, że atrybut ma zastosowanie do metody dostępu zdarzeń, nie zdarzenia:

    ```cpp
    delegate void MyDel();
    ref struct X {
       [field:MyAttr(123)] event MyDel* MyEvent;   //field
       [event:MyAttr(123)] event MyDel* MyEvent;   //event
       [MyAttr(123)] event MyDel* MyEvent;   // default: event
    }
    ```

Specyfikator użycia atrybutu ma zastosowanie tylko do atrybutu, który następuje bezpośrednio po nim; Czyli

```cpp
[returnvalue:Attr1, Attr2]
```

różni się od

```cpp
[returnvalue:Attr1, returnvalue:Attr2]
```

## <a name="example"></a>Przykład

### <a name="description"></a>Opis

Ten przykład pokazuje, jak określić wiele elementów docelowych.

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

[Atrybuty zdefiniowane przez użytkownika](../windows/user-defined-attributes-cpp-component-extensions.md)