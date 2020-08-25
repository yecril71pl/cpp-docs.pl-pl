---
title: Platform::Collections::UnorderedMap — Klasa
ms.date: 12/30/2016
ms.topic: reference
f1_keywords:
- collection/Platform::Collections::UnorderedMap
ms.assetid: dc84f261-b13c-4c0a-9b57-30dcb9e3065e
ms.openlocfilehash: ec458f5d4a47b6eced939c4fe346d5d0414ea7c2
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/25/2020
ms.locfileid: "88839130"
---
# <a name="platformcollectionsunorderedmap-class"></a>Platform::Collections::UnorderedMap — Klasa

Reprezentuje *mapę*nieuporządkowaną, która jest kolekcją par klucz-wartość.

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

*K*<br/>
Typ klucza w parze klucz-wartość.

*V*<br/>
Typ wartości w parze klucz-wartość.

*S*<br/>
Typ, który dostarcza obiekt funkcji, który może porównać dwie wartości elementów jako klucze sortowania, aby określić ich względną kolejność w mapie. Domyślnie [std:: equal_to \<K> ](../standard-library/equal-to-struct.md).

### <a name="remarks"></a>Uwagi

Dozwolone typy to:

- integers

- Klasa interfejsu ^

- publiczna Klasa referencyjna ^

- Struktura wartości

- publiczna Klasa enum

**UnorderedMap** jest w zasadzie otoką dla [std:: unordered_map](../standard-library/unordered-map-class.md) , która obsługuje magazyn typów środowisko wykonawcze systemu Windows. Jest to konkretna implementacja typów [Windows:: Foundation:: Collections:: IMAP](/uwp/api/windows.foundation.collections.imap-2) i [IObservableMap](/uwp/api/windows.foundation.collections.iobservablemap-2) , które są przesyłane przez publiczne interfejsy środowisko wykonawcze systemu Windows. Jeśli spróbujesz użyć `Platform::Collections::UnorderedMap` typu w publicznej wartości zwracanej lub parametrze, zostanie zgłoszony błąd kompilatora C3986. Możesz naprawić ten błąd, zmieniając typ parametru lub wartość zwrotną na [Windows:: Foundation:: Collections:: IMAP](/uwp/api/windows.foundation.collections.imap-2).

Aby uzyskać więcej informacji, zobacz [kolekcje](../cppcx/collections-c-cx.md).

### <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[UnorderedMap:: UnorderedMap](#ctor)|Inicjuje nowe wystąpienie klasy map.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[UnorderedMap:: Clear](#clear)|Usuwa wszystkie pary klucz-wartość z bieżącego obiektu mapy.|
|[UnorderedMap:: First](#first)|Zwraca iterator, który określa pierwszy element na mapie.|
|[UnorderedMap:: GetView](#getview)|Zwraca widok tylko do odczytu bieżącej mapy; oznacza to, że Klasa platform:: Collections:: UnorderedMapView.|
|[UnorderedMap:: Haskey —](#haskey)|Określa, czy bieżąca Mapa zawiera określony klucz.|
|[UnorderedMap:: INSERT](#insert)|Dodaje określoną parę klucz-wartość do bieżącego obiektu mapy.|
|[UnorderedMap:: Lookup](#lookup)|Pobiera element z określonego klucza w obiekcie mapy bieżącej.|
|[UnorderedMap:: Remove](#remove)|Usuwa określoną parę klucz-wartość z bieżącego obiektu mapy.|
|[UnorderedMap:: size](#size)|Zwraca liczbę elementów w bieżącym obiekcie mapy.|

### <a name="events"></a>Zdarzenia

| Nazwa | Opis |
|--|--|
| [Map:: MapChanged](#mapchanged) , zdarzenie | Występuje, gdy mapa zostanie zmieniona. |

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

`UnorderedMap`

### <a name="requirements"></a>Wymagania

**Nagłówek:** Collection. h

**Przestrzeń nazw:** Platform:: Collections

## <a name="unorderedmapclear-method"></a><a name="clear"></a> UnorderedMap:: Clear — Metoda

Usuwa wszystkie pary klucz-wartość z bieżącego obiektu UnorderedMap.

### <a name="syntax"></a>Składnia

```cpp
virtual void Clear();
```

## <a name="unorderedmapfirst-method"></a><a name="first"></a> UnorderedMap:: First — Metoda

Zwraca iterator, który określa pierwszy element [Windows:: Foundation:: Collections:: \<K,V> IKeyValuePair](/uwp/api/windows.foundation.collections.ikeyvaluepair-2) w nieuporządkowanej mapie.

### <a name="syntax"></a>Składnia

```cpp
virtual Windows::Foundation::Collections::IIterator<
   Windows::Foundation::Collections::IKeyValuePair<K, V>^>^
   First();
```

### <a name="return-value"></a>Wartość zwracana

Iterator, który określa pierwszy element na mapie.

### <a name="remarks"></a>Uwagi

Wygodnym sposobem przechowywania iteratora zwracanego przez First () jest przypisanie wartości zwracanej do zmiennej, która jest zadeklarowana za pomocą **`auto`** słowa kluczowego odejmowania. Na przykład `auto x = myUnorderedMap->First();`.

## <a name="unorderedmapgetview-method"></a><a name="getview"></a> UnorderedMap:: GetView — metoda

Zwraca widok tylko do odczytu dla bieżącego UnorderedMap; oznacza to, że [Klasa platform:: Collections:: UnorderedMapView](../cppcx/platform-collections-unorderedmapview-class.md) implementująca interfejs [systemu Windows:: Foundation:: Collections:: IMapView:: IMapView](/uwp/api/windows.foundation.collections.imapview-2) .

### <a name="syntax"></a>Składnia

```cpp
Windows::Foundation::Collections::IMapView<K, V>^ GetView();
```

### <a name="return-value"></a>Wartość zwracana

Obiekt `UnorderedMapView`.

## <a name="unorderedmaphaskey-method"></a><a name="haskey"></a> UnorderedMap:: Haskey —, Metoda

Określa, czy bieżący UnorderedMap zawiera określony klucz.

### <a name="syntax"></a>Składnia

```cpp
bool HasKey(
   K key
);
```

### <a name="parameters"></a>Parametry

*głównych*<br/>
Klucz używany do lokalizowania elementu UnorderedMap. Typ *klucza* to TypeName *K*.

### <a name="return-value"></a>Wartość zwracana

**`true`** Jeśli klucz zostanie znaleziony; w przeciwnym razie **`false`** .

## <a name="unorderedmapinsert-method"></a><a name="insert"></a> UnorderedMap:: Insert — Metoda

Dodaje określoną parę klucz-wartość do bieżącego obiektu UnorderedMap.

### <a name="syntax"></a>Składnia

```cpp
virtual bool Insert(
   K key,
   V value
);
```

### <a name="parameters"></a>Parametry

*głównych*<br/>
Część klucza pary klucz-wartość. Typ *klucza* to TypeName *K*.

*wartościami*<br/>
Część wartości pary klucz-wartość. Typ *wartości* to TypeName *V*.

### <a name="return-value"></a>Wartość zwracana

**`true`** Jeśli klucz istniejącego elementu w bieżącej mapie pasuje do *klucza* , a część wartości tego elementu jest ustawiona na *wartość Value*. **`false`** Jeśli żaden istniejący element w bieżącej mapie nie pasuje do *klucza* , a parametry *klucza* i *wartości* są wprowadzane do pary klucz-wartość, a następnie dodane do bieżącej UnorderedMap.

## <a name="unorderedmaplookup-method"></a><a name="lookup"></a> UnorderedMap:: Lookup — Metoda

Pobiera wartość typu V, która jest skojarzona z określonym kluczem typu K.

### <a name="syntax"></a>Składnia

```cpp
V Lookup(
   K key
);
```

### <a name="parameters"></a>Parametry

*głównych*<br/>
Klucz służący do lokalizowania elementu w UnorderedMap. Typ *klucza* to TypeName *K*.

### <a name="return-value"></a>Wartość zwracana

Wartość sparowana z *kluczem*. Typ zwracanej wartości to TypeName *V*.

## <a name="unorderedmapmapchanged"></a><a name="mapchanged"></a> UnorderedMap:: MapChanged

Uruchamiany, gdy element zostanie wstawiony do mapy lub usunięty z niego.

### <a name="syntax"></a>Składnia

```cpp
event Windows::Foundation::Collections::MapChangedEventHandler<K,V>^ MapChanged;
```

### <a name="property-valuereturn-value"></a>Wartość właściwości/Zwracana wartość

Element [MapChangedEventHandler \<K,V> ](/uwp/api/windows.foundation.collections.mapchangedeventhandler-2) , który zawiera informacje o obiekcie, który spowodował zdarzenie, oraz o rodzaju zmiany, które wystąpiły. Zobacz również [Wyliczenie \<K> IMapChangedEventArgs](/uwp/api/windows.foundation.collections.imapchangedeventargs-1) i [CollectionChange](/uwp/api/windows.foundation.collections.collectionchange).

## <a name="net-framework-equivalent"></a>Odpowiednik w programie .NET Framework

Środowisko wykonawcze systemu Windows aplikacje, które w języku C# lub Visual Basic projektu IMap \<K,V> jako IDictionary \<K,V> .

## <a name="unorderedmapremove-method"></a><a name="remove"></a> UnorderedMap:: Remove — Metoda

Usuwa określoną parę klucz-wartość z obiektu UnorderedMap.

### <a name="syntax"></a>Składnia

```cpp
virtual void Remove(
   K key);
```

### <a name="parameters"></a>Parametry

*głównych*<br/>
Część klucza pary klucz-wartość. Typ *klucza* to TypeName *K*.

## <a name="unorderedmapsize-method"></a><a name="size"></a> UnorderedMap:: size — Metoda

Zwraca liczbę [IKeyValuePair \<K,V> elementów Windows:: Foundation:: Collections](/uwp/api/windows.foundation.collections.ikeyvaluepair-2) w UnorderedMap.

### <a name="syntax"></a>Składnia

```cpp
virtual property unsigned int Size;
```

### <a name="return-value"></a>Wartość zwracana

Liczba elementów w nieuporządkowanej mapie.

## <a name="unorderedmapunorderedmap-constructor"></a><a name="ctor"></a> UnorderedMap:: UnorderedMap — Konstruktor

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

*InIt*<br/>
Wartość atrybutu TypeName bieżącego UnorderedMap.

*P*<br/>
Obiekt funkcji, który może porównać dwa klucze, aby określić, czy są równe. Wartość domyślna tego parametru to [std:: \<K> equal_to](../standard-library/equal-to-struct.md).

*H*<br/>
Obiekt funkcji, który generuje wartość skrótu dla kluczy. Ten parametr domyślnie określa [klasę wartości 1](../standard-library/hash-class.md) dla typów kluczy obsługiwanych przez klasę.

*mol*<br/>
Odwołanie lub [lvalues i rvalues](../cpp/lvalues-and-rvalues-visual-cpp.md) do [std:: unordered_map](../standard-library/unordered-map-class.md) , który jest używany do inicjowania bieżącego UnorderedMap.

*II*<br/>
[Std:: initializer_list](../standard-library/initializer-list-class.md) z obiektów [std::p Air](../standard-library/pair-structure.md) , które są używane do inicjowania mapy.

*pierwszego*<br/>
Iterator wejściowy pierwszego elementu w zakresie elementów używanych do inicjowania bieżącego UnorderedMap.

*ostatniego*<br/>
Iterator wejściowy pierwszego elementu po zakresie elementów użytych do zainicjowania bieżącego UnorderedMap.

## <a name="see-also"></a>Zobacz też

[Przestrzeń nazw platformy](platform-namespace-c-cx.md)<br/>
[Platform:: Collections, przestrzeń nazw](../cppcx/platform-collections-namespace.md)<br/>
[Platform:: Collections:: map, Klasa](../cppcx/platform-collections-map-class.md)<br/>
[Platform:: Collections:: UnorderedMapView, Klasa](../cppcx/platform-collections-unorderedmapview-class.md)<br/>
[Kolekcje](../cppcx/collections-c-cx.md)<br/>
[Tworzenie składników środowisko wykonawcze systemu Windows w języku C++](/windows/uwp/winrt-components/creating-windows-runtime-components-in-cpp)
