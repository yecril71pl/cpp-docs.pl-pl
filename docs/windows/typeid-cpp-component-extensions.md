---
title: TypeID (C + +/ CLI i C + +/ CX) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 10/12/2018
ms.technology:
- cpp-windows
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- typeid keyword [C++]
ms.assetid: e9706cae-e7c4-4d6d-b474-646d73df3e70
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: b31344b1ba72b37bcfff45a3fd4feefda85f6a7a
ms.sourcegitcommit: 3f4e92266737ecb70507871e87dc8e2965ad7e04
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/15/2018
ms.locfileid: "49327586"
---
# <a name="typeid--ccli-and-ccx"></a>TypeID (C + +/ CLI i C + +/ CX)

Pobiera wartość wskazującą typ obiektu.

> [!NOTE]
> W tym temacie odnosi się do wersji C++ Component Extensions typeid. Wersja ISO C++ to słowo kluczowe, zobacz [typeid, Operator](../cpp/typeid-operator.md).

## <a name="all-runtimes"></a>Wszystkie środowiska wykonawcze

### <a name="syntax"></a>Składnia

```cpp
T::typeid
```

### <a name="parameters"></a>Parametry

*T*<br/>
Nazwa typu.

## <a name="windows-runtime"></a>Środowisko wykonawcze systemu Windows

### <a name="syntax"></a>Składnia

```cpp
Platform::Type^ type = T::typeid;
```

### <a name="parameters"></a>Parametry

*T*<br/>
Nazwa typu.

### <a name="remarks"></a>Uwagi

W języku C + +/ CX typeid zwraca [Platform::Type](../cppcx/platform-type-class.md) , są konstruowane na podstawie informacji o typie środowiska uruchomieniowego.

### <a name="requirements"></a>Wymagania

— Opcja kompilatora: `/ZW`

## <a name="common-language-runtime"></a>środowiska uruchomieniowe w trakcie wykonania

### <a name="syntax"></a>Składnia

```
type::typeid
```

### <a name="parameters"></a>Parametry

*Typ*<br/>
Nazwa typu (abstrakcyjnym deklaratorze), dla którego chcesz `System::Type` obiektu.

### <a name="remarks"></a>Uwagi

`typeid` Służy do uzyskiwania <xref:System.Type> dla typu w czasie kompilacji.

`typeid` jest podobny do pobierania System::Type dla typu w czasie wykonywania za pomocą <xref:System.Type.GetType%2A> lub <xref:System.Object.GetType%2A>. Jednak typeid akceptowane są tylko nazwę typu jako parametru.  Jeśli chcesz użyć wystąpienia typu można pobrać nazwy System::Type, należy użyć GetType.

`typeid` musi mieć możliwość oceny nazwę typu (typ) w czasie kompilacji, natomiast GetType ocenia typ do zwrócenia w czasie wykonywania.

`typeid` może potrwać nazwy natywnego typu lub wspólnej alias środowiska uruchomieniowego języka dla nazwy typu natywnego; zobacz [.NET Framework odpowiedniki typów natywnych języka C++ (C + +/ CLI)](../dotnet/dotnet-framework-equivalents-to-cpp-native-types-cpp-cli.md) Aby uzyskać więcej informacji.

`typeid` współpracuje również z natywnych typów, chociaż nadal zwróci System::Type.  Aby uzyskać strukturę type_info, użyj [typeid, Operator](../cpp/typeid-operator.md).

### <a name="requirements"></a>Wymagania

— Opcja kompilatora: `/clr`

### <a name="examples"></a>Przykłady

W poniższym przykładzie porównano typeid, słowo kluczowe do `GetType()` elementu członkowskiego.

```cpp
// keyword__typeid.cpp
// compile with: /clr
using namespace System;

ref struct G {
   int i;
};

int main() {
   G ^ pG = gcnew G;
   Type ^ pType = pG->GetType();
   Type ^ pType2 = G::typeid;

   if (pType == pType2)  
      Console::WriteLine("typeid and GetType returned the same System::Type");
   Console::WriteLine(G::typeid);

   typedef float* FloatPtr;
   Console::WriteLine(FloatPtr::typeid);
}
```

```Output
typeid and GetType returned the same System::Type
G

System.Single*  
```

Poniższy przykład pokazuje, że zmienna typu System::Type może służyć do pobieranie atrybutów w danym typie.  Pokazano także, że dla niektórych typów, trzeba będzie utworzyć element typedef do użycia `typeid`.

```cpp
// keyword__typeid_2.cpp
// compile with: /clr
using namespace System;
using namespace System::Security;
using namespace System::Security::Permissions;

typedef int ^ handle_to_int;
typedef int * pointer_to_int;

public ref class MyClass {};

class MyClass2 {};

[attribute(AttributeTargets::All)]
ref class AtClass {
public:
   AtClass(Type ^) {
      Console::WriteLine("in AtClass Type ^ constructor");
   }
};

[attribute(AttributeTargets::All)]
ref class AtClass2 {
public:
   AtClass2() {
      Console::WriteLine("in AtClass2 constructor");
   }
};

// Apply the AtClass and AtClass2 attributes to class B
[AtClass(MyClass::typeid), AtClass2]
[AttributeUsage(AttributeTargets::All)]
ref class B : Attribute {};

int main() {
   Type ^ MyType = B::typeid;

   Console::WriteLine(MyType->IsClass);

   array<Object^>^ MyArray = MyType -> GetCustomAttributes(true);
   for (int i = 0 ; i < MyArray->Length ; i++ )  
      Console::WriteLine(MyArray[i]);

   if (int::typeid != pointer_to_int::typeid)  
      Console::WriteLine("int::typeid != pointer_to_int::typeid, as expected");

   if (int::typeid == handle_to_int::typeid)  
      Console::WriteLine("int::typeid == handle_to_int::typeid, as expected");
}
```

```Output
True

in AtClass2 constructor

in AtClass Type ^ constructor

AtClass2

System.AttributeUsageAttribute

AtClass

int::typeid != pointer_to_int::typeid, as expected

int::typeid == handle_to_int::typeid, as expected
```

## <a name="see-also"></a>Zobacz też

[Component Extensions dla platformy .NET i platformy uniwersalnej systemu Windows](../windows/component-extensions-for-runtime-platforms.md)