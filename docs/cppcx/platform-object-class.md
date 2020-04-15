---
title: Platforma::Klasa obiektu
ms.date: 12/30/2016
ms.topic: reference
f1_keywords:
- VCCORLIB/Platform::Object::Object
- VCCORLIB/Platform::Object::Equals
- VCCORLIB/Platform::Object::GetHashCode
- VCCORLIB/Platform::Object::ReferenceEquals
- VCCORLIB/Platform::ToString
- VCCORLIB/Platform::GetType
helpviewer_keywords:
- Object class
ms.assetid: 709e84a8-0bff-471b-bc14-63e424080b5a
ms.openlocfilehash: 8300ec484bdb58919ce8e450b706dd07c275ceee
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81363684"
---
# <a name="platformobject-class"></a>Platforma::Klasa obiektu

Zapewnia typowe zachowanie dla klas ref i struktury ref w aplikacjach środowiska wykonawczego systemu Windows. Wszystkie wystąpienia ref klasy i ref struct są niejawnie konwertowane na Platform::Object^ i mogą zastąpić jego wirtualną metodę ToString.

## <a name="syntax"></a>Składnia

```cpp
public ref class Object : Object
```

### <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[Obiekt::Obiekt](#ctor)|Inicjuje nowe wystąpienie Object klasy.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[Obiekt::Równa się](#equals)|Określa, czy dany obiekt jest taki sam, jak bieżący obiekt.|
|[Obiekt::GetHashCode](#gethashcode)|Zwraca wartość skrótu dla tego wystąpienia.|
|[Obiekt::ReferenceEquals](#referenceequals)|Określa, czy określone wystąpienia object są tym samym wystąpieniem.|
|[ToString](#tostring)|Zwraca ciąg reprezentujący bieżący obiekt. Można zastąpić.|
|[GetType](#gettype)|Pobiera [platform::Type,](../cppcx/platform-type-class.md) który opisuje bieżące wystąpienie.|

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

`Object`

`Object`

### <a name="requirements"></a>Wymagania

**Nagłówek:** vccorlib.h

**Obszar nazw:** Platformy

## <a name="objectequals-method"></a><a name="equals"></a>Obiekt::Metoda równa się

Określa, czy dany obiekt jest taki sam, jak bieżący obiekt.

### <a name="syntax"></a>Składnia

```cpp
bool Equals(
    Object^ obj
)
```

### <a name="parameters"></a>Parametry

*Obj*<br/>
Obiekt do porównania.

### <a name="return-value"></a>Wartość zwracana

**true,** jeśli obiekty są równe, w przeciwnym razie **false**.

## <a name="objectgethashcode-method"></a><a name="gethashcode"></a>Obiekt::Metoda GetHashCode

`IUnknown`Zwraca * wartość tożsamości dla tego wystąpienia, jeśli jest to obiekt COM lub obliczona wartość mieszania, jeśli nie jest obiektem COM.

### <a name="syntax"></a>Składnia

```cpp
public:int GetHashCode();
```

### <a name="return-value"></a>Wartość zwracana

Wartość liczbowa, która jednoznacznie identyfikuje ten obiekt.

### <a name="remarks"></a>Uwagi

Za pomocą GetHashCode można tworzyć klucze dla obiektów na mapach. Kody skrótów można porównać za pomocą [obiektu::Równa się](#equals). Jeśli ścieżka kodu jest `GetHashCode` bardzo `Equals` krytyczna i nie są wystarczająco szybkie, następnie można `IUnknown` rozwijać w dół do podstawowej warstwy COM i zrobić natywne porównania wskaźnika.

## <a name="objectgettype-method"></a><a name="gettype"></a>Obiekt::Metoda GetType

Zwraca [platformę::Type](../cppcx/platform-type-class.md) obiektu, który opisuje typ środowiska wykonawczego obiektu.

### <a name="syntax"></a>Składnia

```cpp
Object::GetType();
```

### <a name="property-valuereturn-value"></a>Wartość właściwości/Zwracana wartość

A [Platform::Type](../cppcx/platform-type-class.md) obiektu, który opisuje typ środowiska wykonawczego obiektu.

### <a name="remarks"></a>Uwagi

Typ [statyczny::GetTypeCode](../cppcx/platform-type-class.md#gettypecode) może służyć do uzyskania [platform::TypeCode wartość wyliczenia,](../cppcx/platform-typecode-enumeration.md) która reprezentuje bieżący typ. Jest to głównie przydatne dla typów wbudowanych. Kod typu dla każdej klasy ref oprócz [Platformy::String](../cppcx/platform-string-class.md) jest Object (1).

Klasa [Windows::UI:Xaml::Interop::TypeName](/uwp/api/windows.ui.xaml.interop.typename) jest używana w interfejsach API systemu Windows jako niezależny od języka sposób przekazywania informacji o typie między składnikami i aplikacjami systemu Windows. T[Platform::Type Class](../cppcx/platform-type-class.md) ma operatorów `Type` `TypeName`do konwersji między i .

Operator [typeid](../extensions/typeid-cpp-component-extensions.md) służy do `Platform::Type` zwracania nazwy klasy dla obiektu, na przykład podczas nawigowania między stronami XAML:

```
rootFrame->Navigate(TypeName(MainPage::typeid), e->Arguments);
```

## <a name="objectobject-constructor"></a><a name="ctor"></a>Obiekt::Konstruktor obiektów

Inicjuje nowe wystąpienie Object klasy.

### <a name="syntax"></a>Składnia

```cpp
public:Object();
```

## <a name="objectreferenceequals-method"></a><a name="referenceequals"></a>Obiekt::ReferenceEquals Metoda

Określa, czy określone wystąpienia object są tym samym wystąpieniem.

### <a name="syntax"></a>Składnia

```cpp
public:static bool ReferenceEquals(  Object^ obj1,   Object^ obj2);
```

### <a name="parameters"></a>Parametry

*obj1 (obj1)*<br/>
Pierwszy obiekt do porównania.

*obj2 (obj2)*<br/>
Drugi obiekt do porównania.

### <a name="return-value"></a>Wartość zwracana

**true,** jeśli dwa obiekty są takie same; w przeciwnym razie **false**.

## <a name="objecttostring-method-ccx"></a><a name="tostring"></a>Obiekt::Metoda ToString (C++/CX)

Zwraca ciąg reprezentujący bieżący obiekt.

### <a name="syntax"></a>Składnia

```cpp
public:
virtual String^ ToString();
```

### <a name="return-value"></a>Wartość zwracana

Ciąg reprezentujący bieżący obiekt. Tę metodę można zastąpić, aby zapewnić niestandardowy komunikat ciągu w klasie ref lub strukturze:

```cpp
public ref class Tree sealed
{
public:
    Tree(){}
    virtual Platform::String^ ToString() override
    {
      return "I’m a Tree";
    };
};
```

## <a name="see-also"></a>Zobacz też

[Obszar nazw platformy](platform-namespace-c-cx.md)<br/>
[Platform::Type, klasa](platform-type-class.md)<br/>
[System typów](type-system-c-cx.md)
