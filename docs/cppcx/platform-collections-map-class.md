---
title: Klasa platform::Collections::map | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 12/30/2016
ms.technology: cpp-windows
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- COLLECTION/Platform::Collections::Map::Map
- COLLECTION/Platform::Collections::Map::Clear
- COLLECTION/Platform::Collections::Map::First
- COLLECTION/Platform::Collections::Map::GetView
- COLLECTION/Platform::Collections::Map::HasKey
- COLLECTION/Platform::Collections::Map::Insert
- COLLECTION/Platform::Collections::Map::Lookup
- COLLECTION/Platform::Collections::Map::Remove
- COLLECTION/Platform::Collections::Map::Size
dev_langs: C++
helpviewer_keywords: Map Class (C++/Cx)
ms.assetid: 2b8cf968-1167-4898-a149-1195b32c1785
caps.latest.revision: "19"
author: ghogen
ms.author: ghogen
manager: ghogen
ms.openlocfilehash: 3cf7cec405170a1bb1ee02cfd076c78c43524c74
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="platformcollectionsmap-class"></a>Klasa platform::Collections::map
Reprezentuje *mapy*, która jest kolekcją par klucz wartość.  
  
## <a name="syntax"></a>Składnia  
  
```  
template <  
   typename K,  
   typename V,  
   typename C = std::less<K>>  
ref class Map sealed;  
```  
#### <a name="parameters"></a>Parametry  
 `K`  
 Typ klucza w pary klucz wartość.  
  
 `V`  
 Typ wartości w pary klucz wartość.  
  
 `C`  
 Typ, który udostępnia obiekt funkcji, które można porównać dwóch wartości elementu jako klucze sortowania, aby określić ich kolejność względne w planie. Domyślnie [std::less\<K >](../standard-library/less-struct.md).  
  
 __is_valid_winrt_type()  
 Funkcja, która weryfikuje typu K i V i udostępnia przyjazne komunikaty o błędach, jeśli typ nie mogą być przechowywane w mapie wygenerowany przez kompilator.  
  
### <a name="remarks"></a>Uwagi  
 Dozwolone typy to:  
  
-   liczby całkowite  
  
-   Klasa interfejsu ^  
  
-   Klasa ref publicznego ^  
  
-   wartość — Struktura  
  
-   Wyliczenie publiczne — klasa  
  
 Mapa jest zasadniczo otoki dla [std::map](../standard-library/map-class.md). Jest C++ konkretną implementację [Windows::Foundation::Collections::IMap < Windows::Foundation::Collections::IKeyValuePair\<K, V >>](http://go.microsoft.com/fwlink/p/?LinkId=262408) i [IObservableMap](http://msdn.microsoft.com/library/windows/apps/br226050.aspx) typy, które są przekazywane przez publicznego interfejsów środowiska wykonawczego systemu Windows. Jeśli spróbujesz użyć `Platform::Collections::Map` typu publicznego zwracana wartość lub parametr C3986 jest zgłoszony został błąd kompilatora. Naprawić ten błąd, zmieniając typ wartości parametru lub return na [Windows::Foundation::Collections::IMap\<K, V >](http://go.microsoft.com/fwlink/p/?LinkId=262408).  
  
 Aby uzyskać więcej informacji, zobacz [kolekcji](../cppcx/collections-c-cx.md).  
  
### <a name="members"></a>Elementy członkowskie  
  
### <a name="public-constructors"></a>Konstruktory publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[Map::map](#ctor)|Inicjuje nowe wystąpienie klasy mapy.|  
  
### <a name="public-methods"></a>Metody publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[Map::Clear](#clear)|Usuwa wszystkie pary klucz wartość z bieżącego obiektu mapy.|  
|[Map::First](#first)|Zwraca iteratora określająca pierwszy element na mapie.|  
|[Map::GetView](#getview)|Zwraca widok tylko do odczytu w bieżącym mapy; oznacza to [Platform::Collections::MapView klasy](../cppcx/platform-collections-mapview-class.md).|  
|[Map::HasKey](#haskey)|Określa, czy bieżąca mapa zawiera określony klucz.|  
|[Map::INSERT](#insert)|Dodaje określoną parę klucz wartość, jak bieżący obiekt mapy.|  
|[Map::LOOKUP](#lookup)|Pobiera element pod określony klucz w bieżącym obiekcie mapy.|  
|[Map::Remove](#remove)|Usuwa określoną parę klucz wartość z bieżącego obiektu mapy.|  
|[Map::size](#size)|Zwraca liczbę elementów w bieżącym obiekcie mapy.|  
  
### <a name="events"></a>Zdarzenia  
  
|||  
|-|-|  
|Nazwa|Opis|  
|[Map::mapchanged —](#mapchanged-event.md)`event`|Występuje, gdy mapy.|  
  
## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia  
 `Map`  
  
### <a name="requirements"></a>Wymagania  
 **Nagłówek:** collection.h  
  
 **Namespace:** Platform::Collections  

## <a name="clear"></a>Map::Clear — metoda
Usuwa wszystkie pary klucz wartość z bieżącego obiektu mapy.  
  
### <a name="syntax"></a>Składnia  
  
```    
virtual void Clear();   
```  
  


## <a name="first"></a>Map::First — metoda
Zwraca iteratora określająca pierwszy element na mapie lub `nullptr` Jeśli mapy jest pusta.  
  
### <a name="syntax"></a>Składnia  
  
```    
virtual Windows::Foundation::Collections::IIterator<  
Windows::Foundation::Collections::IKeyValuePair<K, V>^>^ First();  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Iteratora określająca pierwszy element na mapie.  
  
### <a name="remarks"></a>Uwagi  
 Jest to wygodny sposób przechowywania iteratora zwrócony przez First() można przypisać do zmiennej, która jest zadeklarowana z wartością zwracaną **automatycznie** wpisz wnioskowanie — słowo kluczowe. Na przykład `auto x = myMap->First();`.  
  


## <a name="getview"></a>Map::GetView — metoda
Zwraca widok tylko do odczytu w bieżącym mapy; oznacza to [klasy Platform::Collections::MapView](../cppcx/platform-collections-mapview-class.md), który implementuje [Windows::Foundation::Collections::IMapView\<K, V >](http://msdn.microsoft.com/library/windows/apps/br226037.aspx) interfejsu.  
  
### <a name="syntax"></a>Składnia  
  
```    
Windows::Foundation::Collections::IMapView<K, V>^ GetView();  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 A `MapView` obiektu.  
  


## <a name="haskey"></a>Map::HasKey — metoda
Określa, czy bieżąca mapa zawiera określony klucz.  
  
### <a name="syntax"></a>Składnia  
  
```    
bool HasKey(K key);  
```  
  
### <a name="parameters"></a>Parametry  
 `key`  
 Klucz używana do lokalizowania elementu mapy. Typ `key` jest typename *K*.  
  
### <a name="return-value"></a>Wartość zwracana  
 `true`Jeśli klucz zostanie znaleziony; w przeciwnym razie `false`.  
  


## <a name="insert"></a>Map::INSERT — metoda
Dodaje określoną parę klucz wartość, jak bieżący obiekt mapy.  
  
### <a name="syntax"></a>Składnia  
  
```  
  
virtual bool Insert(K key, V value);  
```  
  
### <a name="parameters"></a>Parametry  
 `key`  
 Część klucza pary klucz wartość. Typ `key` jest typename *K*.  
  
 `value`  
 Część wartości pary klucz wartość. Typ `value` jest typename *V*.  
  
### <a name="return-value"></a>Wartość zwracana  
 `true`Jeśli klucz istniejącego elementu na bieżącej mapy odpowiada `key` i ma ustawioną wartość część elementu `value`. `false`Jeśli nie istniejący element w bieżącej mapy nie jest zgodny `key` i `key` i `value` parametry są wprowadzane na parę klucz wartość, a następnie dodać do bieżącej mapy.  
  


## <a name="lookup"></a>Map::LOOKUP — metoda
Pobiera wartość typu V, który jest skojarzony z określonym kluczem typu K, jeśli ten klucz istnieje.  
  
### <a name="syntax"></a>Składnia  
  
```  
V Lookup(K key);  
```  
  
### <a name="parameters"></a>Parametry  
 `key`  
 Klucz używana do lokalizowania elementu w planie. Typ `key` jest typename *K*.  
  
### <a name="return-value"></a>Wartość zwracana  
 Wartość, która jest łączyć się z `key`. Typ zwracanej wartości to typename *V*.  
  
### <a name="remarks"></a>Uwagi  
 Jeśli klucz nie istnieje, a następnie [Platform::OutOfBoundsException](../cppcx/platform-outofboundsexception-class.md) jest generowany.  
  


## <a name="ctor"></a>Map::map — Konstruktor
Inicjuje nowe wystąpienie klasy mapy.  
  
### <a name="syntax"></a>Składnia  
  
```  
explicit Map(const C& comp = C());  
explicit Map(const StdMap& m);  
explicit Map(StdMap&& m ;  
template <typename InIt>  
Map(  
   InItfirst,  
   InItlast,  
   const C& comp = C());  
```  
  
### <a name="parameters"></a>Parametry  
 `InIt`  
 Właściwość typename bieżącego mapy.  
  
 `comp`  
 Typ, który udostępnia obiekt funkcji, które można porównać dwóch wartości elementu jako klucze sortowania, aby określić ich kolejność względne w planie.  
  
 `m`  
 Odwołanie lub [Lvalues i Rvalues](../cpp/lvalues-and-rvalues-visual-cpp.md) do `map Class` używany do inicjowania bieżącej mapy.  
  
 `first`  
 Wejściowy iteratora pierwszego elementu w zakresie elementów używaną do inicjalizacji bieżącej mapy.  
  
 `last`  
 Wejściowy iteratora pierwszego elementu po zakresu elementów używaną do inicjalizacji bieżącej mapy.  
  


## <a name="mapchanged"></a>Map::mapchanged — zdarzenie
Wywoływane, gdy element zostanie wstawiony do lub usunięty z mapy.  
  
### <a name="syntax"></a>Składnia  
  
```cpp  
event Windows::Foundation::Collections::MapChangedEventHandler<K,V>^ MapChanged;  
```  
  
### <a name="property-valuereturn-value"></a>Wartość właściwości/Zwracana wartość  
 A [MapChangedEventHandler\<K, V >](http://msdn.microsoft.com/library/windows/apps/br206644.aspx) zawierający informacje dotyczące obiekt, który wywołał zdarzenie i rodzaju zmiany, który wystąpił. Zobacz też [IMapChangedEventArgs\<K >](http://msdn.microsoft.com/library/windows/apps/br226034.aspx) i [wyliczenie CollectionChange](http://msdn.microsoft.com/library/windows/apps/windows.foundation.collections.collectionchange.aspx).  
  
## <a name="net-framework-equivalent"></a>Odpowiednik w programie .NET Framework  
 Aplikacje ze Sklepu Windows korzystających z języka C# lub Visual Basic projektu IMap\<K, V > jako IDictionary\<K, V >.  
  


## <a name="remove"></a>Map::Remove — Metoda
Usuwa określoną parę klucz wartość z bieżącego obiektu mapy.  
  
### <a name="syntax"></a>Składnia  
  
```    
virtual void Remove(K key);  
```  
  
### <a name="parameters"></a>Parametry  
 `key`  
 Część klucza pary klucz wartość. Typ `key` jest typename *K*.  
  


## <a name="size"></a>Map::size — metoda
Zwraca liczbę [Windows::Foundation::Collections::IKeyValuePair\<K, V >](http://msdn.microsoft.com/library/windows/apps/br226031.aspx) elementy na mapie.  
  
### <a name="syntax"></a>Składnia  
  
```    
virtual property unsigned int Size;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Liczba elementów w planie.  
  

  
## <a name="see-also"></a>Zobacz też  
 [Namespace platformy](platform-namespace-c-cx.md)   
 [Tworzenie składników środowiska wykonawczego systemu Windows w języku C++](/MicrosoftDocs/windows-uwp/blob/docs/windows-apps-src/winrt-components/creating-windows-runtime-components-in-cpp.md)