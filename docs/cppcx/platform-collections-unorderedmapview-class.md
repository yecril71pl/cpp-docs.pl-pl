---
title: "Platform::Collections:: unorderedmapview — klasa | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 12/30/2016
ms.technology: cpp-windows
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- collection/Platform::Collections::UnorderedMapView
ms.assetid: 545a3725-2efd-4cc1-b590-4a7cd2351f61
caps.latest.revision: 
author: ghogen
ms.author: ghogen
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: e1bb555cc804069aed3c778acf1ac71e795a11ff
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/14/2018
---
# <a name="platformcollectionsunorderedmapview-class"></a>Platform::Collections::UnorderedMapView — Klasa
Reprezentuje widok tylko do odczytu do *mapy*, która jest kolekcją par klucz wartość.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
template <  
   typename K,  
   typename V,  
   typename C = ::std::equal_to<K>>  
ref class UnorderedMapView sealed;  
```  
  
#### <a name="parameters"></a>Parametry  
 `K`  
 Typ klucza w pary klucz wartość.  
  
 `V`  
 Typ wartości w pary klucz wartość.  
  
 `C`  
 Typ, który udostępnia obiekt funkcji, które można porównać dwóch wartości klucza pod kątem równości. Domyślnie [std::equal_to\<K >](../standard-library/equal-to-struct.md)  
  
### <a name="remarks"></a>Uwagi  
 UnorderedMapView jest konkretną implementację C++ [Windows::Foundation::Collections::IMapView\<K, V >](http://go.microsoft.com/fwlink/p/?LinkId=262409) interfejs, który jest przekazywany przez interfejs binarne aplikacji (ABI). Aby uzyskać więcej informacji, zobacz [kolekcji (C + +/ CX)](../cppcx/collections-c-cx.md).  
  
### <a name="members"></a>Elementy członkowskie  
  
### <a name="public-constructors"></a>Konstruktory publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[UnorderedMapView::UnorderedMapView](#ctor)|Inicjuje nowe wystąpienie klasy UnorderedMapView.|  
  
### <a name="public-methods"></a>Metody publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[UnorderedMapView::First](#first)|Zwraca iteratora inicjowany do pierwszego elementu w widoku mapy.|  
|[UnorderedMapView::HasKey](#haskey)|Określa, czy bieżący UnorderedMapView zawiera określony klucz.|  
|[UnorderedMapView::Lookup](#lookup)|Pobiera element pod określony klucz w bieżącym obiekcie UnorderedMapView.|  
|[UnorderedMapView::Size](#size)|Zwraca liczbę elementów w bieżącym obiekcie UnorderedMapView.|  
|[UnorderedMapView::Split](#split)|Dzieli oryginalny obiekt UnorderedMapView na dwa obiekty UnorderedMapView.|  
  
## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia  
 `UnorderedMapView`  
  
### <a name="requirements"></a>Wymagania  
 **Nagłówek:** collection.h  
  
 **Namespace:** Platform::Collections  

## <a name="first"></a>  UnorderedMapView::First — metoda
Zwraca iteratora określająca pierwszy [Windows::Foundation::Collections::IKeyValuePair\<K, V >](http://msdn.microsoft.com/library/windows/apps/br226031.aspx) element nieuporządkowaną mapy.  
  
### <a name="syntax"></a>Składnia  
  
```cpp   
virtual Windows::Foundation::Collections::IIterator<  
    Windows::Foundation::Collections::IKeyValuePair<K, V>^>^   
    First();  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Iteratora określający pierwszego elementu w widoku mapy.  
  
### <a name="remarks"></a>Uwagi  
 Jest to wygodny sposób przechowywania iteratora zwrócony przez First() można przypisać do zmiennej, która jest zadeklarowana z wartością zwracaną **automatycznie** wpisz wnioskowanie — słowo kluczowe. Na przykład `auto x = myMapView->First();`.  
  


## <a name="haskey"></a>  UnorderedMapView::HasKey — metoda
Określa, czy bieżący UnorderedMap zawiera określony klucz.  
  
### <a name="syntax"></a>Składnia  
  
```cpp    
bool HasKey(K key);  
```  
  
### <a name="parameters"></a>Parametry  
 `key`  
 Klucz używana do lokalizowania elementu. Typ `key` jest typename *K*.  
  
### <a name="return-value"></a>Wartość zwracana  
 `true` Jeśli klucz zostanie znaleziony; w przeciwnym razie `false`.  
  


## <a name="lookup"></a>  UnorderedMapView::Lookup — metoda
Pobiera wartość typu V skojarzony z określonym kluczem typu K.  
  
### <a name="syntax"></a>Składnia  
  
```cpp  
V Lookup(K key);  
```  
  
### <a name="parameters"></a>Parametry  
 `key`  
 Klucz używana do lokalizowania elementu w UnorderedMapView. Typ `key` jest typename *K*.  
  
### <a name="return-value"></a>Wartość zwracana  
 Wartość, która jest łączyć się z `key`. Typ zwracanej wartości to typename *V*.  
  


## <a name="size"></a>  UnorderedMapView::Size — metoda
Zwraca liczbę [Windows::Foundation::Collections::IKeyValuePair\<K, V >](http://msdn.microsoft.com/library/windows/apps/br226031.aspx) elementów w UnorderedMapView.  
  
### <a name="syntax"></a>Składnia  
  
```cpp    
virtual property unsigned int Size;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Liczba elementów w nieuporządkowaną MapView.  
  


## <a name="split"></a>  UnorderedMapView::Split — metoda
Bieżący obiekt UnorderedMapView jest podzielony na dwa obiekty UnorderedMapView. Ta metoda jest nie działa.  
  
### <a name="syntax"></a>Składnia  
  
```cpp  
void Split(  
   Windows::Foundation::Collections::IMapView<  
                         K,V>^ * firstPartition,  
   Windows::Foundation::Collections::IMapView<  
                         K,V>^ * secondPartition);  
```  
  
### <a name="parameters"></a>Parametry  
 `firstPartition`  
 Pierwsza część oryginalnego obiektu UnorderedMapView.  
  
 `secondPartition`  
 Druga część oryginalnego obiektu UnorderedMapView.  
  
### <a name="remarks"></a>Uwagi  
 Ta metoda nie działa; nie działają.  
  


## <a name="ctor"></a>  Unorderedmapview::unorderedmapview — Konstruktor
Inicjuje nowe wystąpienie klasy UnorderedMapView.  
  
### <a name="syntax"></a>Składnia  
  
```cpp  
  
UnorderedMapView();    
explicit UnorderedMapView(size_t n);   
UnorderedMapView(size_t n, const H& h);   
UnorderedMapView(size_t n, const H& h, const P& p);  
  
explicit UnorderedMapView(  
    const std::unordered_map<K, V, H, P>& m);  
explicit UnorderedMapView(  
    std::unordered_map<K, V, H, P>&& m);  
  
template <typename InIt> UnorderedMapView(InIt first, InIt last );  
template <typename InIt> UnorderedMapView(InIt first, InIt last, size_t n );  
  
template <typename InIt> UnorderedMapView(  
    InIt first,  
    InIt last,  
    size_t n,  
    const H& h );  
  
template <typename InIt> UnorderedMapView(  
    InIt first,  
    InIt last,  
    size_t n,  
    const H& h,  
    const P& p );  
  
UnorderedMapView(std::initializer_list<std::pair<const K, V>);  
  
UnorderedMapView(std::initializer_list< std::pair<const K, V>> il, size_t n   
  
UnorderedMapView(  
    std::initializer_list< std::pair<const K, V>> il,  
    size_t n,  
    const H& h);  
  
UnorderedMapView(  
    std::initializer_list< std::pair<const K, V>> il,  
    size_t n,  
    const H& h,  
    const P& p );  
```  
  
### <a name="parameters"></a>Parametry  
 n  
 Liczba elementów do przydzielenia miejsca.  
  
 `InIt`  
 Wartość atrybutu typename UnorderedMapView.  
  
 `H`  
 Obiekt funkcji, który można wartość skrótu dla klucza. Domyślnie [std::hash\<K >](http://msdn.microsoft.com/en-us/54f67435-af9d-4217-a29d-fa4d2491a104) dla typów który `std::hash` obsługuje.  
  
 `P`  
 Typ, który udostępnia obiekt funkcji, które można porównać dwa klucze, aby określić ich równości. Domyślnie [std::equal_to\<K >](../standard-library/equal-to-struct.md).  
  
 `m`  
 Odwołanie lub [Lvalues i Rvalues](../cpp/lvalues-and-rvalues-visual-cpp.md) do [std::unordered_map](../standard-library/unordered-map-class.md) używany do inicjowania UnorderedMapView.  
  
 `first`  
 Wejściowy iteratora pierwszego elementu w zakresie elementów używaną do inicjalizacji UnorderedMapView.  
  
 `last`  
 Wejściowy iteratora pierwszego elementu po zakres używany do inicjowania UnorderedMapView elementów.  
   
## <a name="see-also"></a>Zobacz też  
 [Platform::Collections Namespace](../cppcx/platform-collections-namespace.md)   
 [Windows::Foundation::IMapView](http://go.microsoft.com/fwlink/p/?LinkId=262409)