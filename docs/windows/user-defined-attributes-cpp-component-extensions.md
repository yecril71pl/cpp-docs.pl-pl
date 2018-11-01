---
title: Atrybuty zdefiniowane przez użytkownika (C + +/ CLI i C + +/ CX)
ms.date: 10/12/2018
ms.topic: reference
helpviewer_keywords:
- metadata, extending
- custom attributes, extending metadata
ms.assetid: 98b29048-a3ea-4698-8441-f149cdaec9fb
ms.openlocfilehash: f64cf5415e79678f0e0b43b58aae2249601fb3d7
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50546656"
---
# <a name="user-defined-attributes--ccli-and-ccx"></a>Atrybuty zdefiniowane przez użytkownika (C + +/ CLI i C + +/ CX)

C + +/ CLI i C + +/ CX umożliwiają tworzenie atrybuty specyficzne dla platformy, które rozszerzają metadane interfejsu, klasy lub struktury, metody, parametr lub wyliczenia. Te atrybuty różnią się od [standardowe atrybuty C++](../cpp/attributes.md).

## <a name="windows-runtime"></a>Środowisko wykonawcze systemu Windows

Możesz zastosować C + +/ CX atrybuty do właściwości, ale nie do konstruktorów i metod.

### <a name="requirements"></a>Wymagania

— Opcja kompilatora: `/ZW`

## <a name="common-language-runtime"></a>środowiska uruchomieniowe w trakcie wykonania

Informacje i składni przedstawione w tym temacie jest przeznaczona do zastąpienia informacje znajdujące się w [atrybutu](attributes/attribute.md).

Można zdefiniować atrybut niestandardowy typ definiujący i dokonując <xref:System.Attribute> klasę bazową dla typu i opcjonalnie stosowanie <xref:System.AttributeUsageAttribute> atrybutu.

Aby uzyskać więcej informacji, zobacz:

- [Docelowe atrybuty](attribute-targets-cpp-component-extensions.md)

- [Typy parametrów atrybutu](attribute-parameter-types-cpp-component-extensions.md)

Instrukcje dotyczące podpisywania zestawów w programie Visual C++, zobacz [zestawy o silnej nazwach (podpisywanie zestawów) (C + +/ CLI)](../dotnet/strong-name-assemblies-assembly-signing-cpp-cli.md).

### <a name="requirements"></a>Wymagania

— Opcja kompilatora: `/clr`

### <a name="examples"></a>Przykłady

Poniższy przykład pokazuje sposób definiowania atrybutu niestandardowego.

```cpp
// user_defined_attributes.cpp
// compile with: /clr /c
using namespace System;

[AttributeUsage(AttributeTargets::All)]
ref struct Attr : public Attribute {
   Attr(bool i){}
   Attr(){}
};

[Attr]
ref class MyClass {};
```

W poniższym przykładzie pokazano kilka ważnych funkcji atrybutów niestandardowych. Na przykład, w tym przykładzie wspólne użycie atrybutów niestandardowych: utworzenie wystąpienia serwera, na którym można w pełni opisania siebie klientom.

```cpp
// extending_metadata_b.cpp
// compile with: /clr
using namespace System;
using namespace System::Reflection;

public enum class Access { Read, Write, Execute };

// Defining the Job attribute:
[AttributeUsage(AttributeTargets::Class, AllowMultiple=true )]
public ref class Job : Attribute {
public:
   property int Priority {
      void set( int value ) { m_Priority = value; }
      int get() { return m_Priority; }
   }

   // You can overload constructors to specify Job attribute in different ways
   Job() { m_Access = Access::Read; }
   Job( Access a ) { m_Access = a; }
   Access m_Access;

protected:
   int m_Priority;
};

interface struct IService {
   void Run();
};

   // Using the Job attribute:
   // Here we specify that QueryService is to be read only with a priority of 2.
   // To prevent namespace collisions, all custom attributes implicitly
   // end with "Attribute".

[Job( Access::Read, Priority=2 )]
ref struct QueryService : public IService {
   virtual void Run() {}
};

// Because we said AllowMultiple=true, we can add multiple attributes
[Job(Access::Read, Priority=1)]
[Job(Access::Write, Priority=3)]
ref struct StatsGenerator : public IService {
   virtual void Run( ) {}
};

int main() {
   IService ^ pIS;
   QueryService ^ pQS = gcnew QueryService;
   StatsGenerator ^ pSG = gcnew StatsGenerator;

   //  use QueryService
   pIS = safe_cast<IService ^>( pQS );

   // use StatsGenerator
   pIS = safe_cast<IService ^>( pSG );

   // Reflection
   MemberInfo ^ pMI = pIS->GetType();
   array <Object ^ > ^ pObjs = pMI->GetCustomAttributes(false);

   // We can now quickly and easily view custom attributes for an
   // Object through Reflection */
   for( int i = 0; i < pObjs->Length; i++ ) {
      Console::Write("Service Priority = ");
      Console::WriteLine(static_cast<Job^>(pObjs[i])->Priority);
      Console::Write("Service Access = ");
      Console::WriteLine(static_cast<Job^>(pObjs[i])->m_Access);
   }
}
```

```Output
Service Priority = 0

Service Access = Write

Service Priority = 3

Service Access = Write

Service Priority = 1

Service Access = Read
```

`Object^` Typu zastępuje typ danych variant. W poniższym przykładzie zdefiniowano niestandardowy atrybut, który przyjmuje tablicę `Object^` jako parametry.

Argumenty atrybutów muszą być stałymi kompilacji; w większości przypadków powinny one być stałe literały.

Zobacz [typeid](typeid-cpp-component-extensions.md) informacji na temat sposobu zwracania wartości System::Type z bloku atrybutów niestandardowych.

```cpp
// extending_metadata_e.cpp
// compile with: /clr /c
using namespace System;
[AttributeUsage(AttributeTargets::Class | AttributeTargets::Method)]
public ref class AnotherAttr : public Attribute {
public:
   AnotherAttr(array<Object^>^) {}
   array<Object^>^ var1;
};

// applying the attribute
[ AnotherAttr( gcnew array<Object ^> { 3.14159, "pi" }, var1 = gcnew array<Object ^> { "a", "b" } ) ]
public ref class SomeClass {};
```

Środowisko uruchomieniowe wymaga, że publiczną część klasy atrybutu niestandardowego musi podlegać serializacji.  Podczas tworzenia niestandardowych atrybutów, argumenty nazwane atrybutu niestandardowego są ograniczone do stałych w czasie kompilacji.  (Go traktować jako sekwencja bitów dołączany do układu klasy w metadanych.)

```cpp
// extending_metadata_f.cpp
// compile with: /clr /c
using namespace System;
ref struct abc {};

[AttributeUsage( AttributeTargets::All )]
ref struct A : Attribute {
   A( Type^ ) {}
   A( String ^ ) {}
   A( int ) {}
};

[A( abc::typeid )]
ref struct B {};
```

## <a name="see-also"></a>Zobacz też

[Rozszerzenia składników dla platformy .NET i platformy uniwersalnej systemu Windows](component-extensions-for-runtime-platforms.md)