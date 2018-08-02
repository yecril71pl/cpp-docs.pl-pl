---
title: atrybut | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- vc-attr.attribute
dev_langs:
- C++
helpviewer_keywords:
- __typeof keyword
- custom attributes, creating
- attribute attribute
- attributes [C++], custom
ms.assetid: 8cb3489f-65c4-44ea-b0aa-3c3c6b15741d
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: d72506e3f384a784bce4d159e8e76e88098c79f7
ms.sourcegitcommit: 51f804005b8d921468775a0316de52ad39b77c3e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/02/2018
ms.locfileid: "39461812"
---
# <a name="attribute"></a>— atrybut
Umożliwia tworzenie atrybutów niestandardowych.  
  
## <a name="syntax"></a>Składnia  
  
```  
[ attribute(  
   AllowOn,  
   AllowMultiple=boolean,  
   Inherited=boolean  
) ]  
```  
  
#### <a name="parameters"></a>Parametry  
 *AllowOn*  
 Określa elementy języka, do których można zastosować atrybutu niestandardowego. Wartość domyślna to `System::AttributeTargets::All` (zobacz [System::AttributeTargets](https://msdn.microsoft.com/library/system.attributetargets.aspx)).  
  
 *AllowMultiple*  
 Określa, czy atrybut niestandardowy mogą dotyczyć wielokrotnie konstrukcję. Domyślną jest FALSE.  
  
 *Dziedziczone*  
 Wskazuje, czy ten atrybut ma być dziedziczona przez podklasy. Kompilator nie obsługuje specjalne tej funkcjonalności. zadanie konsumentów atrybutu (na przykład odbicia) jest do przestrzegania tych informacji. Jeśli *dziedziczone* ma wartość PRAWDA, ten atrybut jest dziedziczona. Jeśli *AllowMultiple* ma wartość TRUE, atrybut będą gromadzone w pochodnej składowej; Jeśli *AllowMultiple* ma wartość FALSE, atrybut spowoduje zastąpienie (lub Zastąp) w dziedziczeniu. Jeśli *dziedziczone* ma wartość FAŁSZ, ten atrybut nie będą dziedziczone. Domyślna wartość to TRUE.  
  
## <a name="remarks"></a>Uwagi  
  
> [!NOTE]
>  `attribute` Atrybutu jest już przestarzały.  Użyj wspólnego języka środowiska uruchomieniowego atrybut klasy System.Attribute bezpośrednio, aby utworzyć attirbutes zdefiniowanych przez użytkownika.  Aby uzyskać więcej informacji, zobacz [atrybuty zdefiniowane przez użytkownika](../windows/user-defined-attributes-cpp-component-extensions.md).  
  
 Należy zdefiniować [atrybutu niestandardowego](../windows/custom-attributes-cpp.md) , umieszczając `attribute` atrybutu zarządzanych definicji klasy lub struktury. Nazwa klasy jest atrybutu niestandardowego. Na przykład:  
  
```  
[ attribute(Parameter) ]  
public ref class MyAttr {};  
```  
  
 Definiuje atrybut o nazwie `MyAttr` , który można zastosować do parametrów funkcji. Klasy muszą być publiczne, jeśli atrybut ma być używane w innych zestawach.  
  
> [!NOTE]
>  Aby uniknąć kolizji nazw, wszystkie nazwy atrybutu niejawnie kończą się ciągiem "Attribute"; w tym przykładzie nazwa atrybutu i klasa jest faktycznie `MyAttrAttribute`, ale `MyAttr` i `MyAttrAttribute` mogą być używane zamiennie.  
  
 Konstruktory publiczne klasy definiują parametry bez nazwy atrybutu. Przeciążenia konstruktorów Zezwalaj na wiele sposobów określania atrybutów, dzięki czemu niestandardowy atrybut, który jest zdefiniowany w następujący sposób:  
  
```cpp  
// cpp_attr_ref_attribute.cpp  
// compile with: /c /clr  
using namespace System;  
[ attribute(AttributeTargets::Class) ]   // apply attribute to classes  
public ref class MyAttr {  
public:  
   MyAttr() {}   // Constructor with no parameters  
   MyAttr(int arg1) {}   // Constructor with one parameter  
};  
  
[MyAttr]  
ref class ClassA {};   // Attribute with no parameters  
  
[MyAttr(123)]  
ref class ClassB {};   // Attribute with one parameter  
```  
  
 Publiczne składowe danych klasy i właściwości są opcjonalne parametry nazwane atrybutu:  
  
```cpp  
// cpp_attr_ref_attribute_2.cpp  
// compile with: /c /clr  
using namespace System;  
[ attribute(AttributeTargets::Class) ]  
ref class MyAttr {  
public:  
   // Property Priority becomes attribute's named parameter Priority  
    property int Priority {  
       void set(int value) {}  
       int get() { return 0;}  
   }  
   // Data member Version becomes attribute's named parameter Version  
   int Version;  
   MyAttr() {}   // constructor with no parameters  
   MyAttr(int arg1) {}   // constructor with one parameter  
};  
  
[MyAttr(123, Version=2)]   
ref class ClassC {};  
```  
  
 Aby uzyskać listę typy parametrów atrybutu możliwe, zobacz [atrybuty niestandardowe](../windows/custom-attributes-cpp.md).  
  
 Zobacz [atrybuty zdefiniowane przez użytkownika](../windows/user-defined-attributes-cpp-component-extensions.md) do dyskusji na temat docelowe atrybuty.  
  
 `attribute` Atrybut ma *AllowMultiple* parametr, który określa, czy atrybut niestandardowy jest jednorazowego użytku lub multiuse (może wystąpić więcej niż raz w tej samej jednostce).  
  
```cpp  
// cpp_attr_ref_attribute_3.cpp  
// compile with: /c /clr  
using namespace System;  
[ attribute(AttributeTargets::Class, AllowMultiple = true) ]  
ref struct MyAttr {  
   MyAttr(){}  
};   // MyAttr is a multiuse attribute  
  
[MyAttr, MyAttr()]  
ref class ClassA {};  
```  
  
 Niestandardowy atrybut klasy pochodzą bezpośrednio lub pośrednio z <xref:System.ComponentModel.AttributeCollection.%23ctor%2A>, co sprawia, że identyfikowanie definicji atrybutów w metadanych jest łatwe i szybkie. `attribute` Atrybut oznacza dziedziczenie z System::Attribute, więc jawne tworzenie wartości pochodnych nie jest konieczne:  
  
```  
[ attribute(Class) ]  
ref class MyAttr  
```  
  
 odpowiada wyrażeniu  
  
```  
[ attribute(Class) ]  
ref class MyAttr : System::Attribute   // OK, but redundant.  
```  
  
 `attribute` jest aliasem dla <xref:System.AttributeUsageAttribute?displayProperty=fullName> (nie AttributeAttribute; jest to wyjątek reguły nazewnictwa atrybutu).  
  
## <a name="requirements"></a>Wymagania  
  
### <a name="attribute-context"></a>Kontekst atrybutu  
  
|||  
|-|-|  
|**Dotyczy**|**Klasa REF**, **struktury ref**|  
|**Powtarzalne**|Nie|  
|**Wymaganych atrybutów**|Brak|  
|**Nieprawidłowe atrybuty**|Brak|  
  
 Aby uzyskać więcej informacji na temat konteksty atrybutu zobacz [konteksty atrybutu](../windows/attribute-contexts.md).  
  
## <a name="example"></a>Przykład  
  
```cpp  
// cpp_attr_ref_attribute_4.cpp  
// compile with: /c /clr  
using namespace System;  
[attribute(AttributeTargets::Class)]  
ref struct ABC {  
   ABC(Type ^) {}  
};  
  
[ABC(String::typeid)]   // typeid operator yields System::Type ^  
ref class MyClass {};  
```  
  
## <a name="example"></a>Przykład  
 `Inherited` Nazwany argument określa, czy atrybut niestandardowy stosowane w klasie bazowej pojawią się na podstawie odbicia klasy pochodnej.  
  
```cpp  
// cpp_attr_ref_attribute_5.cpp  
// compile with: /clr  
using namespace System;  
using namespace System::Reflection;  
  
[attribute( AttributeTargets::Method, Inherited=false )]  
ref class BaseOnlyAttribute { };  
  
[attribute( AttributeTargets::Method, Inherited=true )]  
ref class DerivedTooAttribute { };  
  
ref struct IBase {  
public:  
   [BaseOnly, DerivedToo]  
   virtual void meth() {}  
};  
  
// Reflection on Derived::meth will show DerivedTooAttribute   
// but not BaseOnlyAttribute.  
ref class Derived : public IBase {  
public:  
   virtual void meth() override {}  
};  
  
int main() {  
   IBase ^ pIB = gcnew Derived;  
  
   MemberInfo ^ pMI = pIB->GetType( )->GetMethod( "meth" );  
   array<Object ^> ^ pObjs = pMI->GetCustomAttributes( true );  
   Console::WriteLine( pObjs->Length ) ;  
}  
```  
  
```Output  
2  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Alfabetyczny spis atrybutów](../windows/attributes-alphabetical-reference.md)   
 [Atrybuty niestandardowe](http://msdn.microsoft.com/558ebdb2-082f-44dc-b442-d8d33bf7bdb8)