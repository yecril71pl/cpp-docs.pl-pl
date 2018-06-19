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
ms.openlocfilehash: 9826b689e2b8a640efe66e8625b97b3cec347acf
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/08/2018
ms.locfileid: "33862065"
---
# <a name="attribute"></a>— atrybut
Służy do tworzenia atrybutu niestandardowego.  
  
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
 Określa elementy języka, do których można zastosować atrybutu niestandardowego. Domyślnie jest **System::AttributeTargets::All** (zobacz [System::AttributeTargets](https://msdn.microsoft.com/en-us/library/system.attributetargets.aspx)).  
  
 `AllowMultiple`  
 Określa, czy atrybut niestandardowy może odnosić się wielokrotnie do konstrukcję. Domyślnie jest **FALSE**.  
  
 `Inherited`  
 Wskazuje, czy ten atrybut ma być dziedziczone przez podklasy. Kompilator nie zapewnia specjalne obsługi dla tej funkcjonalności. zadanie konsumentów atrybutu (na przykład odbicia) jest do przestrzegania tych informacji. Jeśli `Inherited` jest **TRUE**, ten atrybut jest dziedziczona. Jeśli `AllowMultiple` jest **TRUE**, atrybut będą gromadzone w elemencie członkowskim pochodnej; Jeśli `AllowMultiple` jest **FALSE**, ten atrybut zostanie zastąpienia (lub Zastąp) w dziedziczeniu. Jeśli `Inherited` jest **FALSE**, ten atrybut nie będą dziedziczone. Domyślnie jest **TRUE**.  
  
## <a name="remarks"></a>Uwagi  
  
> [!NOTE]
>  `attribute` Atrybutu jest już przestarzały.  Umożliwia utworzenie zdefiniowanej przez użytkownika attirbutes wspólnego języka środowiska uruchomieniowego atrybut klasy System.Attribute bezpośrednio.  Aby uzyskać więcej informacji, zobacz [zdefiniowane przez użytkownika atrybuty](../windows/user-defined-attributes-cpp-component-extensions.md).  
  
 Należy zdefiniować [atrybutu niestandardowego](../windows/custom-attributes-cpp.md) przez umieszczenie `attribute` atrybutu zarządzanej definicji klasy lub struktury. Nazwa klasy jest atrybutu niestandardowego. Na przykład:  
  
```  
[ attribute(Parameter) ]  
public ref class MyAttr {};  
```  
  
 Definiuje atrybut o nazwie MyAttr, który można zastosować do parametrów funkcji. Klasa musi być publiczna, jeśli atrybut ma być używane w innych zestawów.  
  
> [!NOTE]
>  Aby uniknąć kolizji nazw, wszystkie nazwy atrybutu niejawnie kończyć "Atrybutu"; w tym przykładzie nazwa atrybutu i klasa jest rzeczywiście MyAttrAttribute, ale MyAttr i MyAttrAttribute mogą być używane zamiennie.  
  
 Konstruktory publiczne klasy definiują parametry bez nazwy atrybutu. Przeciążone konstruktory Zezwalaj na wiele sposobów określenie atrybutu, więc atrybutu niestandardowego, który jest zdefiniowany w następujący sposób:  
  
```  
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
  
 Publiczne elementy członkowskie danych i właściwości tej klasy są opcjonalnymi parametrami nazwanego atrybutu:  
  
```  
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
  
 Listę atrybutów możliwe typy parametrów, zobacz [atrybuty niestandardowe](../windows/custom-attributes-cpp.md).  
  
 Zobacz [zdefiniowane przez użytkownika atrybuty](../windows/user-defined-attributes-cpp-component-extensions.md) omówienie na docelowe atrybuty.  
  
 `attribute` Ma atrybut `AllowMultiple` parametr, który określa, czy atrybut niestandardowy jest jednorazowe lub multiuse (może występować więcej niż raz w tej samej jednostce).  
  
```  
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
  
 Niestandardowy atrybut klasy pochodne bezpośrednio lub pośrednio <xref:System.ComponentModel.AttributeCollection.%23ctor%2A>, która sprawia, że identyfikacji definicje atrybutów w metadanych szybkie i łatwe. `attribute` Atrybut oznacza dziedziczenia z System::Attribute, więc jawne pochodnego nie jest konieczne:  
  
```  
[ attribute(Class) ]  
ref class MyAttr  
```  
  
 jest równoważny  
  
```  
[ attribute(Class) ]  
ref class MyAttr : System::Attribute   // OK, but redundant.  
```  
  
 `attribute` alias jest <xref:System.AttributeUsageAttribute?displayProperty=fullName> (nie AttributeAttribute; jest to wyjątek reguły nazewnictwa atrybutu).  
  
## <a name="requirements"></a>Wymagania  
  
### <a name="attribute-context"></a>Atrybut kontekstu  
  
|||  
|-|-|  
|**Dotyczy**|`ref` **Klasa**, **ref struct**|  
|**Powtarzalne**|Nie|  
|**Wymaganych atrybutów**|Brak|  
|**Nieprawidłowe atrybuty**|Brak|  
  
 Aby uzyskać więcej informacji na temat konteksty atrybutu, zobacz [konteksty atrybutu](../windows/attribute-contexts.md).  
  
## <a name="example"></a>Przykład  
  
```  
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
 `Inherited` Nazwany argument określa, czy atrybut niestandardowy stosowane w klasie podstawowej zostaną wyświetlone na odbicia klasy pochodnej.  
  
```  
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
 [Atrybuty niestandardowe](http://msdn.microsoft.com/en-us/558ebdb2-082f-44dc-b442-d8d33bf7bdb8)