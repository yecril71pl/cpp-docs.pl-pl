---
title: "Platform::Collections:: unorderedmap — klasa | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 12/30/2016
ms.technology: cpp-windows
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: collection/Platform::Collections::UnorderedMap
ms.assetid: dc84f261-b13c-4c0a-9b57-30dcb9e3065e
caps.latest.revision: "7"
author: ghogen
ms.author: ghogen
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 8b2266e43f3168fca823147f4c2c7e2c33513343
ms.sourcegitcommit: 6f40bba1772a09ff0e3843d5f70b553e1a15ab50
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/22/2018
---
# <a name="platformcollectionsunorderedmap-class"></a>Platform::Collections::UnorderedMap — Klasa

Reprezentuje nieuporządkowaną *mapy*, która jest kolekcją par klucz wartość.

## <a name="syntax"></a>Składnia

```cpp
template <
   typename K,
   typename V,
   typename C = std::equal_to<K>
>
ref class Map sealed;
```

#### <a name="parameters"></a>Parametry

*K*  
Typ klucza w pary klucz wartość.

*V*  
Typ wartości w pary klucz wartość.

*C*  
Typ, który udostępnia obiekt funkcji, które można porównać dwóch wartości elementu jako klucze sortowania, aby określić ich kolejność względne w planie. Domyślnie [std::equal_to\<K >](../standard-library/equal-to-struct.md).

### <a name="remarks"></a>Uwagi

Dozwolone typy to:

- liczby całkowite

- Klasa interfejsu ^

- Klasa ref publicznego ^

- wartość — Struktura

- Wyliczenie publiczne — klasa

**UnorderedMap** jest zasadniczo otoki dla [std::unordered_map](../standard-library/unordered-map-class.md) obsługującej magazynu typów środowiska wykonawczego systemu Windows. Jest konkretną implementację [Windows::Foundation::Collections::IMap](/uwp/api/Windows.Foundation.Collections.IMap_K_V_) i [IObservableMap](/uwp/api/Windows.Foundation.Collections.IObservableMap_K_V_) interfejsy środowiska wykonawczego systemu Windows typy, które są przekazywane przez publicznego. Jeśli spróbujesz użyć `Platform::Collections::UnorderedMap` typu publicznego zwracana wartość lub parametr C3986 jest zgłoszony został błąd kompilatora. Naprawić ten błąd, zmieniając typ wartości parametru lub return na [Windows::Foundation::Collections::IMap](/uwp/api/Windows.Foundation.Collections.IMap_K_V_).

Aby uzyskać więcej informacji, zobacz [kolekcji](../cppcx/collections-c-cx.md).

### <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[Unorderedmap::unorderedmap —](#ctor)|Inicjuje nowe wystąpienie klasy mapy.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[UnorderedMap::Clear](#clear)|Usuwa wszystkie pary klucz wartość z bieżącego obiektu mapy.|
|[UnorderedMap::First](#first)|Zwraca iteratora określająca pierwszy element na mapie.|
|[UnorderedMap::GetView](#getview)|Zwraca widok tylko do odczytu w bieżącym mapy; oznacza to, że platform::Collections:: unorderedmapview — klasa.|
|[UnorderedMap::HasKey](#haskey)|Określa, czy bieżąca mapa zawiera określony klucz.|
|[UnorderedMap::Insert](#insert)|Dodaje określoną parę klucz wartość, jak bieżący obiekt mapy.|
|[UnorderedMap::Lookup](#lookup)|Pobiera element pod określony klucz w bieżącym obiekcie mapy.|
|[UnorderedMap::Remove](#remove)|Usuwa określoną parę klucz wartość z bieżącego obiektu mapy.|
|[UnorderedMap::Size](#size)|Zwraca liczbę elementów w bieżącym obiekcie mapy.|

### <a name="events"></a>Zdarzenia

|||
|-|-|
|Nazwa|Opis|
|[Map::mapchanged —](#mapchanged) zdarzeń|Występuje, gdy mapy.|

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

`UnorderedMap`

### <a name="requirements"></a>Wymagania

**Nagłówek:** collection.h

**Namespace:** Platform::Collections

## <a name="clear"></a>UnorderedMap::Clear — metoda

Usuwa wszystkie pary klucz wartość z bieżącego obiektu UnorderedMap.

### <a name="syntax"></a>Składnia

```cpp
virtual void Clear();
```

## <a name="first"></a>UnorderedMap::First — metoda

Zwraca iteratora określająca pierwszy [Windows::Foundation::Collections::IKeyValuePair\<K, V >](http://msdn.microsoft.com/library/windows/apps/br226031.aspx) element nieuporządkowaną mapy.

### <a name="syntax"></a>Składnia

```cpp
virtual Windows::Foundation::Collections::IIterator<
   Windows::Foundation::Collections::IKeyValuePair<K, V>^>^ 
   First();
```

### <a name="return-value"></a>Wartość zwracana

Iteratora określająca pierwszy element na mapie.

### <a name="remarks"></a>Uwagi

Jest to wygodny sposób przechowywania iteratora zwrócony przez First() można przypisać do zmiennej, która jest zadeklarowana z wartością zwracaną **automatycznie** wpisz wnioskowanie — słowo kluczowe. Na przykład `auto x = myUnorderedMap->First();`.

## <a name="getview"></a>UnorderedMap::GetView — metoda

Zwraca bieżący UnorderedMap; widok tylko do odczytu oznacza to [platform::Collections:: unorderedmapview — klasa](../cppcx/platform-collections-unorderedmapview-class.md) implementującej [Windows::Foundation::Collections::IMapView::IMapView](http://msdn.microsoft.com/library/windows/apps/br226037.aspx) interfejsu.

### <a name="syntax"></a>Składnia

```cpp
Windows::Foundation::Collections::IMapView<K, V>^ GetView();
```

### <a name="return-value"></a>Wartość zwracana

`UnorderedMapView` Obiektu.

## <a name="haskey"></a>UnorderedMap::HasKey — metoda

Określa, czy bieżący UnorderedMap zawiera określony klucz.

### <a name="syntax"></a>Składnia

```cpp
bool HasKey(
   K key
);
```

### <a name="parameters"></a>Parametry

*klucz*  
Klucz używana do lokalizowania elementu UnorderedMap. Typ *klucza* jest typename *K*.

### <a name="return-value"></a>Wartość zwracana

`true`Jeśli klucz zostanie znaleziony; w przeciwnym razie `false`.

## <a name="insert"></a>UnorderedMap::Insert — metoda

Dodaje określoną parę klucz wartość, jak bieżący obiekt UnorderedMap.

### <a name="syntax"></a>Składnia

```cpp
virtual bool Insert(
   K key,
   V value
);
```

### <a name="parameters"></a>Parametry

*klucz*  
Część klucza pary klucz wartość. Typ *klucza* jest typename *K*.

*value*  
Część wartości pary klucz wartość. Typ *wartość* jest typename *V*.

### <a name="return-value"></a>Wartość zwracana

`true`Jeśli klucz istniejącego elementu na bieżącej mapy odpowiada *klucza* i ma ustawioną wartość część elementu *wartość*. `false`Jeśli nie istniejący element w bieżącej mapy nie jest zgodny *klucza* i *klucza* i *wartość* parametry są wprowadzane na parę klucz wartość, a następnie dodać do bieżącej UnorderedMap.

## <a name="lookup"></a>UnorderedMap::Lookup — metoda

Pobiera wartość typu V skojarzony z określonym kluczem typu K.

### <a name="syntax"></a>Składnia

```cpp
V Lookup(
   K key
);
```

### <a name="parameters"></a>Parametry

*klucz*  
Klucz używana do lokalizowania elementu w UnorderedMap. Typ *klucza* jest typename *K*.

### <a name="return-value"></a>Wartość zwracana

Wartość, która jest łączyć się z *klucza*. Typ zwracanej wartości to typename *V*.

## <a name="mapchanged"></a>UnorderedMap::MapChanged

Wywoływane, gdy element zostanie wstawiony do lub usunięty z mapy.

### <a name="syntax"></a>Składnia

```cpp
event Windows::Foundation::Collections::MapChangedEventHandler<K,V>^ MapChanged;
```

### <a name="property-valuereturn-value"></a>Wartość właściwości/Zwracana wartość

A [MapChangedEventHandler\<K, V >](http://msdn.microsoft.com/library/windows/apps/br206644.aspx) zawierający informacje dotyczące obiekt, który wywołał zdarzenie i rodzaju zmiany, który wystąpił. Zobacz też [IMapChangedEventArgs\<K >](http://msdn.microsoft.com/library/windows/apps/br226034.aspx) i [wyliczenie CollectionChange](http://msdn.microsoft.com/library/windows/apps/windows.foundation.collections.collectionchange.aspx).

## <a name="net-framework-equivalent"></a>Odpowiednik w programie .NET Framework

Aplikacje ze Sklepu Windows czy nam C# lub Visual Basic projektu IMap\<K, V > jako IDictionary\<K, V >.

## <a name="remove"></a>UnorderedMap::Remove — Metoda

Usuwa określoną parę klucz wartość z obiektu UnorderedMap.

### <a name="syntax"></a>Składnia

```cpp
virtual void Remove(
   K key);
```

### <a name="parameters"></a>Parametry

*klucz*  
Część klucza pary klucz wartość. Typ *klucza* jest typename *K*.

## <a name="size"></a>UnorderedMap::Size — metoda

Zwraca liczbę [Windows::Foundation::Collections::IKeyValuePair\<K, V >](http://msdn.microsoft.com/library/windows/apps/br226031.aspx) elementów w UnorderedMap.

### <a name="syntax"></a>Składnia

```cpp
virtual property unsigned int Size;
```

### <a name="return-value"></a>Wartość zwracana

Liczba elementów w nieuporządkowaną mapy.

## <a name="ctor"></a>Unorderedmap::unorderedmap — Konstruktor

Inicjuje nowe wystąpienie klasy UnorderedMap.

### <a name="syntax"></a>Składnia

```cpp
UnorderedMap();

explicit UnorderedMap(
    size_t n
    );

UnorderedMap(
    size_t n,
    const H& h
    );

UnorderedMap(
    size_t n,
    const H& h,
    const P& p
    );

explicit UnorderedMap(
    const std::unordered_map<K, V, H, P>& m
    );

explicit UnorderedMap(
    std::unordered_map<K, V, H, P>&& m
    );

template <typename InIt>
UnorderedMap(
    InIt first,
    InIt last
    );

template <typename InIt>
UnorderedMap(
    InIt first,
    InIt last,
    size_t n
    );

template <typename InIt>
UnorderedMap(
    InIt first,
    InIt last,
    size_t n,
    const H& h
    );

template <typename InIt>
UnorderedMap(
    InIt first,
    InIt last,
    size_t n,
    const H& h,
    const P& p
    );

UnorderedMap(
    std::initializer_list< std::pair<const K, V>> il
    );

UnorderedMap(
    std::initializer_list< std::pair<const K, V>> il,
    size_t n
    );

UnorderedMap(
    std::initializer_list< std::pair<const K, V>> il,
    size_t n,
    const H& h
    );

UnorderedMap(
    std::initializer_list< std::pair<const K, V>> il,
    size_t n,
    const H& h,
    const P& p
    );
```

### <a name="parameters"></a>Parametry

*InIt*  
Wartość atrybutu typename UnorderedMap bieżącej.

*P*  
Obiekt funkcji, który można porównać dwa klucze, aby sprawdzić, czy są równe. Wartością domyślną tego parametru [std::equal_to\<K >](../standard-library/equal-to-struct.md).

*H*  
Obiekt funkcji, który generuje wartość skrótu dla kluczy. Wartością domyślną tego parametru [skrótów klasy 1](../standard-library/hash-class.md) dla typów klucz, że ta klasa obsługuje.

*m*  
Odwołanie lub [Lvalues i Rvalues](../cpp/lvalues-and-rvalues-visual-cpp.md) do [std::unordered_map](../standard-library/unordered-map-class.md) używany do inicjowania UnorderedMap bieżącej.

*il* A [std::initializer_list](../standard-library/initializer-list-class.md) z [std::pair](../standard-library/pair-structure.md) obiektów, które służy do inicjowania mapy.

*pierwszy*  
Wejściowy iteratora pierwszego elementu w zakresie elementów używaną do inicjalizacji UnorderedMap bieżącej.

*last*  
Wejściowy iteratora pierwszego elementu po zakresu elementów używaną do inicjalizacji UnorderedMap bieżącej.

## <a name="see-also"></a>Zobacz także

[Namespace platformy](platform-namespace-c-cx.md)  
[Platform::Collections, przestrzeń nazw](../cppcx/platform-collections-namespace.md)  
[Platform::Collections::Map, klasa](../cppcx/platform-collections-map-class.md)  
[Platform::Collections::UnorderedMapView, klasa](../cppcx/platform-collections-unorderedmapview-class.md)  
[Kolekcje](../cppcx/collections-c-cx.md)  
[Tworzenie składników środowiska wykonawczego systemu Windows w języku C++](/windows/uwp/winrt-components/creating-windows-runtime-components-in-cpp)  
