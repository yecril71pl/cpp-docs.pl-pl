---
title: Typy parametrów atrybutu (C + +/ CLI i C + +/ CX) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 10/12/2018
ms.technology:
- cpp-windows
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- custom attributes, parameter types
ms.assetid: d9f127a3-7f08-456f-acc6-256805632712
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 8db82e2b31984429165ce39a328abc28ba6e2cfd
ms.sourcegitcommit: 3f4e92266737ecb70507871e87dc8e2965ad7e04
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/15/2018
ms.locfileid: "49328171"
---
# <a name="attribute-parameter-types--ccli-and-ccx"></a>Typy parametrów atrybutu (C + +/ CLI i C + +/ CX)

Wartości przekazane do atrybutów musi być znane, aby kompilator w czasie kompilacji.  Parametry atrybutów może być następujących typów:

- **bool**

- **CHAR**, **unsigned char**

- **krótki**, **typ unsigned short**

- **int**, **unsigned int**

- **długi**, **unsigned long**

- **__int64**, **__int64 bez znaku**

- **float**, **double**

- **wchar_t**

- `char*` lub `wchar_t*` lub `System::String*`

- `System::Type ^`

- `System::Object ^`

- **enum**

## <a name="example"></a>Przykład

### <a name="code"></a>Kod

```cpp
// attribute_parameter_types.cpp
// compile with: /clr /c
using namespace System;
ref struct AStruct {};

[AttributeUsage(AttributeTargets::ReturnValue)]
ref struct Attr : public Attribute {
   Attr(AStruct ^ i){}
   Attr(bool i){}
   Attr(){}
};

ref struct MyStruct {
   static AStruct ^ x = gcnew AStruct;
   [returnvalue:Attr(x)] int Test() { return 0; }   // C3104
   [returnvalue:Attr] int Test2() { return 0; }   // OK
   [returnvalue:Attr(true)] int Test3() { return 0; }   // OK
};
```

## <a name="example"></a>Przykład

### <a name="description"></a>Opis

Podczas określania atrybutów, wszystkich nienazwanych argumentów (pozycyjny) musi poprzedzać wszystkie argumenty nazwane.

### <a name="code"></a>Kod

```cpp
// extending_metadata_c.cpp
// compile with: /clr /c
using namespace System;
[AttributeUsage(AttributeTargets::Class)]
ref class MyAttr : public Attribute {
public:
   MyAttr() {}
   MyAttr(int i) {}
   property int Priority;
   property int Version;
};

[MyAttr]
ref class ClassA {};   // No arguments

[MyAttr(Priority = 1)]
ref class ClassB {};   // Named argument

[MyAttr(123)]
ref class ClassC {};   // Positional argument

[MyAttr(123, Version = 1)]
ref class ClassD {};   // Positional and named
```

## <a name="example"></a>Przykład

### <a name="description"></a>Opis

Atrybut parametry mogą być tablice jednowymiarowe poprzedniego typów.

### <a name="code"></a>Kod

```cpp
// extending_metadata_d.cpp
// compile with: /clr /c
using namespace System;

[AttributeUsage(AttributeTargets::Class)]
public ref struct ABC : public Attribute {
   ABC(array<int>^){}
   array<double> ^ param;
};

[ABC( gcnew array<int> {1,2,3}, param = gcnew array<double>{2.71, 3.14})]
ref struct AStruct{};
```

## <a name="see-also"></a>Zobacz też

[Atrybuty zdefiniowane przez użytkownika](../windows/user-defined-attributes-cpp-component-extensions.md)