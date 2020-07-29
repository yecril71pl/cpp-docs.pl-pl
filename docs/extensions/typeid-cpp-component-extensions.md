---
title: typeid  (C++/CLI i C++/CX)
ms.date: 10/12/2018
ms.topic: reference
helpviewer_keywords:
- typeid keyword [C++]
ms.assetid: e9706cae-e7c4-4d6d-b474-646d73df3e70
ms.openlocfilehash: 56319fb773b8398f85f5fd82c812f0efdb7dde15
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/27/2020
ms.locfileid: "87225114"
---
# <a name="typeid--ccli-and-ccx"></a>typeid  (C++/CLI i C++/CX)

Pobiera wartość wskazującą typ obiektu.

> [!NOTE]
> Ten temat odnosi się do wersji programu typeid składników C++. Aby zapoznać się z wersją tego słowa kluczowego ISO C++, zobacz [Operator typeid](../cpp/typeid-operator.md).

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

W języku C++/CX element typeid zwraca [platformę:: Type](../cppcx/platform-type-class.md) , która jest zbudowana z informacji o typie środowiska uruchomieniowego.

### <a name="requirements"></a>Wymagania

Opcja kompilatora:`/ZW`

## <a name="common-language-runtime"></a>środowiska uruchomieniowe w trakcie wykonania

### <a name="syntax"></a>Składnia

```
type::typeid
```

### <a name="parameters"></a>Parametry

*Wprowadź*<br/>
Nazwa typu (Abstract deklarator), dla którego ma być `System::Type` obiekt.

### <a name="remarks"></a>Uwagi

**`typeid`** służy do pobierania <xref:System.Type> dla typu w czasie kompilacji.

**`typeid`** jest podobny do pobierania `System::Type` dla typu w czasie wykonywania przy użyciu <xref:System.Type.GetType%2A> lub <xref:System.Object.GetType%2A> . Jednakże **`typeid`** tylko akceptuje nazwę typu jako parametr.  Jeśli chcesz użyć wystąpienia typu w celu uzyskania `System::Type` nazwy, użyj `GetType` .

**`typeid`** musi być w stanie oszacować nazwę typu (Type) w czasie kompilacji, natomiast GetType oblicza typ do zwrócenia w czasie wykonywania.

**`typeid`** może przyjmować nazwę typu natywnego lub alias środowiska uruchomieniowego języka wspólnego dla nazwy typu natywnego; Aby uzyskać więcej informacji [, zobacz .NET Framework odpowiedników typów natywnych języka c++ (c++/CLI)](../dotnet/dotnet-framework-equivalents-to-cpp-native-types-cpp-cli.md) .

**`typeid`** działa również z typami natywnymi, chociaż nadal zwracają `System::Type` .  Aby uzyskać strukturę type_info, użyj [ `typeid` operatora](../cpp/typeid-operator.md).

### <a name="requirements"></a>Wymagania

Opcja kompilatora:`/clr`

### <a name="examples"></a>Przykłady

Poniższy przykład porównuje słowo kluczowe typeid z `GetType()` elementem członkowskim.

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

Poniższy przykład pokazuje, że zmienna typu System:: Type może być używana do pobierania atrybutów typu.  Pokazuje również, że dla niektórych typów trzeba utworzyć typedef do użycia **`typeid`** .

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

## <a name="see-also"></a>Zobacz także

[Rozszerzenia składników dla platform .NET i platformy UWP](component-extensions-for-runtime-platforms.md)
