---
title: Atrybuty zdefiniowane przez użytkownika (C++/CLI i C++/CX)
ms.date: 10/12/2018
ms.topic: reference
helpviewer_keywords:
- metadata, extending
- custom attributes, extending metadata
ms.assetid: 98b29048-a3ea-4698-8441-f149cdaec9fb
ms.openlocfilehash: aed36ac7fed7eb1f16f8648f7bcd7efb37f43a75
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/24/2020
ms.locfileid: "80171895"
---
# <a name="user-defined-attributes--ccli-and-ccx"></a>Atrybuty zdefiniowane przez użytkownika (C++/CLI i C++/CX)

C++/CLI i C++/CX umożliwiają tworzenie atrybutów specyficznych dla platformy, które zwiększają metadane interfejsu, klasy lub struktury, metody, parametru lub wyliczenia. Te atrybuty różnią się od [standardowych C++ atrybutów](../cpp/attributes.md).

## <a name="windows-runtime"></a>Środowisko wykonawcze systemu Windows

Można zastosować C++atrybuty/CX do właściwości, ale nie do konstruktorów lub metod.

### <a name="requirements"></a>Wymagania

Opcja kompilatora: `/ZW`

## <a name="common-language-runtime"></a>środowiska uruchomieniowe w trakcie wykonania

Informacje i składnia przedstawione w tym temacie mają na celu zastąpienie informacji przedstawionych w [atrybucie](../windows/attributes/attribute.md).

Można zdefiniować atrybut niestandardowy, definiując typ i wprowadzając <xref:System.Attribute> klasę bazową dla typu i opcjonalnie stosując atrybut <xref:System.AttributeUsageAttribute>.

Aby uzyskać więcej informacji, zobacz:

- [Docelowe atrybuty](attribute-targets-cpp-component-extensions.md)

- [Typy parametrów atrybutu](attribute-parameter-types-cpp-component-extensions.md)

Aby uzyskać informacje dotyczące podpisywania zestawów w C++wizualizacji, zobacz [zestawy o silnych nazwachC++(podpisywanie zestawów) (/CLI)](../dotnet/strong-name-assemblies-assembly-signing-cpp-cli.md).

### <a name="requirements"></a>Wymagania

Opcja kompilatora: `/clr`

### <a name="examples"></a>Przykłady

Poniższy przykład pokazuje, jak zdefiniować atrybut niestandardowy.

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

Poniższy przykład ilustruje kilka ważnych funkcji atrybutów niestandardowych. Na przykład w tym przykładzie przedstawiono typowe użycie atrybutów niestandardowych: Tworzenie wystąpienia serwera, który może być w pełni opisywany klientom.

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

Typ `Object^` zastępuje typ danych Variant. W poniższym przykładzie zdefiniowano atrybut niestandardowy, który pobiera tablicę `Object^` jako parametry.

Argumenty atrybutu muszą być stałymi czasu kompilacji; w większości przypadków powinny to być literały stałe.

Aby uzyskać informacje na temat sposobu zwracania wartości system:: Type z bloku atrybutu niestandardowego, zobacz [typeid](typeid-cpp-component-extensions.md) .

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

Środowisko uruchomieniowe wymaga, aby publiczna część klasy atrybutu niestandardowego musiała być serializowana.  Podczas tworzenia atrybutów niestandardowych, nazwane argumenty atrybutu niestandardowego są ograniczone do stałych czasu kompilacji.  (Pomyśl, że jest to sekwencja bitów dołączona do układu klasy w metadanych).

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
