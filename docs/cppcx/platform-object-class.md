---
title: 'Platform:: Object — Klasa'
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
ms.openlocfilehash: 77313f8c4dcc87fa9de852afe2d60e614f8fc3a3
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/06/2020
ms.locfileid: "78865746"
---
# <a name="platformobject-class"></a>Platform:: Object — Klasa

Zapewnia typowe zachowanie klas referencyjnych i struktur ref w aplikacjach środowisko wykonawcze systemu Windows. Wszystkie wystąpienia klasy ref i ref struct są niejawnie konwertowane na platformę:: Object ^ i mogą przesłonić swoją wirtualną metodę ToString.

## <a name="syntax"></a>Składnia

```cpp
public ref class Object : Object
```

### <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Name (Nazwa)|Opis|
|----------|-----------------|
|[Object:: Object](#ctor)|Inicjuje nowe wystąpienie klasy Object.|

### <a name="public-methods"></a>Metody publiczne

|Name (Nazwa)|Opis|
|----------|-----------------|
|[Obiekt:: Equals](#equals)|Określa, czy dany obiekt jest taki sam, jak bieżący obiekt.|
|[Obiekt:: GetHashCode](#gethashcode)|Zwraca wartość skrótu dla tego wystąpienia.|
|[Obiekt:: ReferenceEquals](#referenceequals)|Określa, czy określone wystąpienia obiektów są tego samego wystąpienia.|
|[ToString](#tostring)|Zwraca ciąg reprezentujący bieżący obiekt. Może zostać zastąpiony.|
|[GetType](#gettype)|Pobiera [platformę:: Type](../cppcx/platform-type-class.md) opisującą bieżące wystąpienie.|

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

`Object`

`Object`

### <a name="requirements"></a>Wymagania

**Nagłówek:** vccorlib. h

**Przestrzeń nazw:** Platformach

## <a name="equals"></a>Object:: Equals — Metoda

Określa, czy dany obiekt jest taki sam, jak bieżący obiekt.

### <a name="syntax"></a>Składnia

```cpp
bool Equals(
    Object^ obj
)
```

### <a name="parameters"></a>Parametry

*obiektów*<br/>
Obiekt do porównania.

### <a name="return-value"></a>Wartość zwracana

**ma wartość true** , jeśli obiekty są równe, w przeciwnym razie **false**.

## <a name="gethashcode"></a>Object:: GetHashCode, Metoda

Zwraca `IUnknown`* wartość tożsamości dla tego wystąpienia, jeśli jest to obiekt COM lub obliczona wartość skrótu, jeśli nie jest obiektem COM.

### <a name="syntax"></a>Składnia

```cpp
public:int GetHashCode();
```

### <a name="return-value"></a>Wartość zwracana

Wartość liczbowa, która jednoznacznie identyfikuje ten obiekt.

### <a name="remarks"></a>Uwagi

Możesz użyć GetHashCode, aby utworzyć klucze dla obiektów w usłudze Maps. Kody skrótów można porównać przy użyciu [obiektu:: Equals](#equals). Jeśli ścieżka kodu jest niezwykle krytyczna i `GetHashCode` i `Equals` nie są wystarczająco szybko, można rozwinąć do źródłowej warstwy modelu COM i wykonać porównania natywnego wskaźnika `IUnknown`.

## <a name="gettype"></a>Object:: GetType — Metoda

Zwraca obiekt [platform:: Type](../cppcx/platform-type-class.md) , który opisuje typ środowiska uruchomieniowego obiektu.

### <a name="syntax"></a>Składnia

```cpp
Object::GetType();
```

### <a name="property-valuereturn-value"></a>Wartość właściwości/Zwracana wartość

Obiekt [platform:: Type](../cppcx/platform-type-class.md) , który opisuje typ środowiska uruchomieniowego obiektu.

### <a name="remarks"></a>Uwagi

Typ statyczny [:: GetTypeCode](../cppcx/platform-type-class.md#gettypecode) może służyć do uzyskania wartości [wyliczenia platform:: TypeCode](../cppcx/platform-typecode-enumeration.md) , która reprezentuje bieżący typ. Jest to szczególnie przydatne w przypadku typów wbudowanych. Kod typu dla dowolnej klasy ref poza [platformą:: String](../cppcx/platform-string-class.md) jest obiektem (1).

Klasa [Windows:: UI:: XAML:: Interop:: TypeName](/uwp/api/windows.ui.xaml.interop.typename) jest używana w interfejsach API systemu Windows jako niezależna od języka Metoda przekazywania informacji o typie między składnikami i aplikacjami systemu Windows. Klasa T[platformy:: Type](../cppcx/platform-type-class.md) ma operatory umożliwiające konwersję między `Type` i `TypeName`.

Użyj operatora [typeid](../extensions/typeid-cpp-component-extensions.md) do zwrócenia obiektu `Platform::Type` dla nazwy klasy, na przykład podczas nawigowania między stronami XAML:

```
rootFrame->Navigate(TypeName(MainPage::typeid), e->Arguments);
```

## <a name="ctor"></a>Object:: Object — Konstruktor

Inicjuje nowe wystąpienie klasy Object.

### <a name="syntax"></a>Składnia

```cpp
public:Object();
```

## <a name="referenceequals"></a>Object:: ReferenceEquals, Metoda

Określa, czy określone wystąpienia obiektów są tego samego wystąpienia.

### <a name="syntax"></a>Składnia

```cpp
public:static bool ReferenceEquals(  Object^ obj1,   Object^ obj2);
```

### <a name="parameters"></a>Parametry

*obj1*<br/>
Pierwszy obiekt do porównania.

*obj2*<br/>
Drugi obiekt do porównania.

### <a name="return-value"></a>Wartość zwracana

**prawda** , jeśli dwa obiekty są takie same; w przeciwnym razie **false**.

## <a name="tostring"></a>Object:: ToString — MetodaC++(/CX)

Zwraca ciąg reprezentujący bieżący obiekt.

### <a name="syntax"></a>Składnia

```cpp
public:
virtual String^ ToString();
```

### <a name="return-value"></a>Wartość zwracana

Ciąg reprezentujący bieżący obiekt. Można zastąpić tę metodę, aby podać niestandardowy komunikat ciągu w klasie lub strukturze ref:

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

[Przestrzeń nazw platformy](platform-namespace-c-cx.md)<br/>
[Platform::Type, klasa](platform-type-class.md)<br/>
[System typów](type-system-c-cx.md)
