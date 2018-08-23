---
title: Zdefiniowane przez użytkownika atrybuty (C++ Component Extensions) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- metadata, extending
- custom attributes, extending metadata
ms.assetid: 98b29048-a3ea-4698-8441-f149cdaec9fb
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 605759e241498e83174f4d6b16435c3119c56671
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2018
ms.locfileid: "42600384"
---
# <a name="user-defined-attributes--c-component-extensions"></a>Atrybuty zdefiniowane przez użytkownika (C++ Component Extensions)

Atrybutów niestandardowych, które umożliwiają poszerzanie funkcjonalności metadanych interfejsu, klasy lub struktury, metody, parametr lub wyliczenia.

## <a name="all-runtimes"></a>Wszystkie środowiska wykonawcze

Wszystkie środowiska wykonawcze obsługuje atrybutów niestandardowych.

## <a name="windows-runtime"></a>Środowisko wykonawcze systemu Windows

C + +/ CX atrybuty obsługuje tylko właściwości, ale nie atrybutu konstruktorów i metod.

### <a name="remarks"></a>Uwagi

### <a name="requirements"></a>Wymagania

— Opcja kompilatora: `/ZW`

## <a name="common-language-runtime"></a>środowiska uruchomieniowe w trakcie wykonania

Atrybutów niestandardowych, które umożliwiają rozszerzenie metadanych elementu zarządzanego. Aby uzyskać więcej informacji, zobacz [atrybuty](/dotnet/standard/attributes/index).

### <a name="remarks"></a>Uwagi

Informacje i składni przedstawione w tym temacie jest przeznaczona do zastąpienia informacje znajdujące się w [atrybutu](../windows/attribute.md).

Można zdefiniować atrybut niestandardowy typ definiujący i dokonując <xref:System.Attribute> klasę bazową dla typu i opcjonalnie stosowanie <xref:System.AttributeUsageAttribute> atrybutu.

Na przykład Równoważenie obciążenia w Microsoft Transaction Server (MTS) 1.0, zachowanie w odniesieniu do transakcji, synchronizacji i itd została określona za pomocą niestandardowych identyfikatorów GUID wstawione do biblioteki typów, przy użyciu atrybutu niestandardowego ODL. Z tego powodu klient serwera MTS można określić jego właściwości, czytając biblioteki typów. W .NET Framework analogowy biblioteki typów jest metadanych, a analogowy atrybutu niestandardowego ODL jest atrybutów niestandardowych. Ponadto odczytywanie biblioteki typów jest analogiczne do typów przy użyciu odbicia.

Aby uzyskać więcej informacji, zobacz,

- [Docelowe atrybuty](../windows/attribute-targets-cpp-component-extensions.md)

- [Typy parametrów atrybutu](../windows/attribute-parameter-types-cpp-component-extensions.md)

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

Zobacz [typeid](../windows/typeid-cpp-component-extensions.md) informacji na temat sposobu zwracania wartości System::Type z bloku atrybutów niestandardowych.

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

[Component Extensions dla platform środowiska uruchomieniowego](../windows/component-extensions-for-runtime-platforms.md)