---
title: "Array — klasa | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- array
- AMP/array
- AMP/Concurrency::array::array
- AMP/Concurrency::array::copy_to
- AMP/Concurrency::array::data
- AMP/Concurrency::array::get_accelerator_view
- AMP/Concurrency::array::get_associated_accelerator_view
- AMP/Concurrency::array::get_cpu_access_type
- AMP/Concurrency::array::get_extent
- AMP/Concurrency::array::reinterpret_as
- AMP/Concurrency::array::section
- AMP/Concurrency::array::view_as
- AMP/Concurrency::array::rank
- AMP/Concurrency::array::accelerator_view
- AMP/Concurrency::array::associated_accelerator_view
- AMP/Concurrency::array::cpu_access_type
- AMP/Concurrency::array::extent
dev_langs:
- C++
helpviewer_keywords:
- array class
ms.assetid: 0832b6c1-40f0-421d-9104-6b1baa0c63a7
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 6a8b7fa960fab118f527d12553725af794db3f0d
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/23/2018
---
# <a name="array-class"></a>array — Klasa
Reprezentuje kontener danych używane do przenoszenia danych do akceleratora.  
  
## <a name="syntax"></a>Składnia  
  
```  
template <typename value_type, int _Rank>  
friend class array;  
```  
  
#### <a name="parameters"></a>Parametry  
 `value_type`  
 Typ elementu danych.  
  
 `_Rank`  
 Ranga tablicy.  
  
## <a name="members"></a>Elementy członkowskie  
  
### <a name="public-constructors"></a>Konstruktory publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[Array — Konstruktor](#ctor)|Inicjuje nowe wystąpienie klasy `array` klasy.|  
|[~ array — destruktor](#dtor)|Niszczy `array` obiektu.|  
### <a name="public-methods"></a>Metody publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[copy_to](#copy_to)|Kopiuje zawartość tablicy do innej tablicy.|  
|[Dane](#data)|Zwraca wskaźnik do danych pierwotnych w tablicy.|  
|[get_accelerator_view](#get_accelerator_view)|Zwraca [accelerator_view](accelerator-view-class.md) obiekt, który reprezentuje lokalizację, w której został przydzielony tablicy. Ta właściwość jest dostępna tylko na Procesor.|  
|[get_associated_accelerator_view](#get_associated_accelerator_view)|Pobiera drugi [accelerator_view](accelerator-view-class.md) obiekt, który jest przekazywany jako parametru wywołanego przemieszczania Konstruktor do tworzenia wystąpienia `array` obiektu.|  
|[get_cpu_access_type](#get_cpu_access_type)|Zwraca [access_type](concurrency-namespace-enums-amp.md#access_type) tablicy. Ta metoda jest dostępna tylko na Procesor.|  
|[get_extent](#get_extent)|Zwraca [zakres](extent-class.md) obiektu tablicy.|  
|[reinterpret_as](#reinterpret_as)|Zwraca Jednowymiarowa tablica, która zawiera wszystkie elementy w `array` obiektu.|  
|[sekcja](#section)|Zwraca podsekcją `array` obiektu, który znajduje się w określonym pochodzenia i, opcjonalnie, który ma określony zakres.|  
|[view_as](#view_as)|Zwraca [array_view —](array-view-class.md) obiektu, który jest tworzony z `array` obiektu.|  
  
### <a name="public-operators"></a>Operatory publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[Operator std::vector&lt;value_type&gt;](#operator_vec)|Używa `copy(*this, vector)` można niejawnie przekonwertować tablicy na std::[wektor](../../../standard-library/vector-class.md) obiektu.|  
|[operator()](#operator_call)|Zwraca wartość elementu określoną przez parametry.|  
|[Operator]](#operator_at)|Zwraca element pod określonym indeksem.|  
|[operator=](#operator_eq)|Kopiuje zawartość określonego `array` obiektu do tego.|  
  
### <a name="public-constants"></a>Publiczny — stałe  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[Rank — stała](#rank)|Przechowuje rangą tablicy.|  
  
### <a name="public-data-members"></a>Publiczne elementy członkowskie danych  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[accelerator_view](#accelerator_view)|Pobiera [accelerator_view](accelerator-view-class.md) obiekt, który reprezentuje lokalizację, w której został przydzielony tablicy. Ta właściwość jest dostępna tylko na Procesor.|  
|[associated_accelerator_view](#associated_accelerator_view)|Pobiera drugi [accelerator_view](accelerator-view-class.md) obiekt, który jest przekazywany jako parametru wywołanego przemieszczania Konstruktor do tworzenia wystąpienia `array` obiektu.|  
|[cpu_access_type](#cpu_access_type)|Pobiera [access_type](concurrency-namespace-enums-amp.md#access_type) reprezentujący jak Procesora można uzyskać dostęp do tablicy magazynu.|  
|[extent](#extent)|Pobiera zakres, która definiuje kształt tablicy.|  
  
## <a name="remarks"></a>Uwagi  
 Typ `array<T,N>` reprezentuje dense i regularne (nie nieregularne) *N*-wymiarową tablicą, który znajduje się w określonej lokalizacji, takich jak akceleratora lub Procesora. Typ danych elementów w tablicy jest `T`, która musi być typu, który jest zgodny z akceleratora docelowej. Mimo że rangę, `N`, (dla tablicy jest określana statycznie i jest częścią typu, zakresu tablicy jest określana przez środowisko uruchomieniowe i jest wyrażona za pomocą klasy `extent<N>`.  
  
 Tablica może mieć dowolną liczbę wymiarów, mimo że niektóre funkcje jest przeznaczone do `array` obiekty o jeden rangi, dwa i trzy. Jeśli zostanie pominięty argument wymiaru, wartość domyślna to 1.  
  
 Dane tablicy jest rozmieszczona ciągłym w pamięci. Elementy, które różnią się co najmniej znaczący wymiaru znajdują się obok siebie w pamięci.  
  
 Tablice są logicznie uważane typy wartości, po skopiowaniu tablicy do innej tablicy głębokie kopiowania jest wykonywana. Dwie tablice nigdy punktu do tych samych danych.  
  
 `array<T,N>` Typ jest używany w kilku scenariuszach:  
  
-   Jako kontener danych, który może być używana w obliczeniach na akceleratora.  
  
-   Jako kontener danych do przechowywania w pamięci na hoście procesora CPU (który może służyć do kopiowania do i z innych tablice).  
  
-   Jako obiekt przemieszczania do działania jako szybkiego pośrednik kopie urządzenia hosta.  
  
## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia  
 `array`  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** amp.h  
  
 **Namespace:** współbieżności  
  
##  <a name="dtor"></a> ~ tablicy 

 Niszczy `array` obiektu.  
  
```  
~array() restrict(cpu);
```  
  
##  <a name="accelerator_view"></a> accelerator_view 

 Pobiera [accelerator_view](accelerator-view-class.md) obiekt, który reprezentuje lokalizację, w której został przydzielony tablicy. Ta właściwość jest dostępna tylko na Procesor.  
  
```  
__declspec(property(get= get_accelerator_view)) Concurrency::accelerator_view accelerator_view;  
```  
  
##  <a name="ctor"></a> Tablica 

 Inicjuje nowe wystąpienie klasy [array — klasa](array-class.md). Nie istnieje ma domyślnego konstruktora dla `array<T,N>`. Wszystkie konstruktory są uruchamiane tylko procesora. Ich nie można wykonać w celu Direct3D.  
  
```  
explicit array(  
    const Concurrency::extent<_Rank>& _Extent) restrict(cpu);  
  
explicit array(  
    int _E0) restrict(cpu);  
  
explicit array(  
    int _E0,  
    int _E1) restrict(cpu);  
  
explicit array(  
    int _E0,  
    int _E1,  
    int _E2) restrict(cpu);  
  
array(  
    const Concurrency::extent<_Rank>& _Extent,  
    Concurrency::accelerator_view _Av  
    access_type _Cpu_access_type = access_type_auto) restrict(cpu);  
  
array(  
    int _E0,  
    Concurrency::accelerator_view _Av  
    access_type _Cpu_access_type = access_type_auto) restrict(cpu);  
  
array(  
    int _E0,  
    int _E1,  
    Concurrency::accelerator_view _Av  
    access_type _Cpu_access_type = access_type_auto) restrict(cpu);  

 
array(
    int _E0,  
    int _E1,  
    int _E2,  
    Concurrency::accelerator_view _Av  
    access_type _Cpu_access_type = access_type_auto) restrict(cpu);  
  
array(  
    const Concurrency::extent<_Rank>& _Extent,  
    Concurrency::accelerator_view _Av,  
    Concurrency::accelerator_view _Associated_Av) restrict(cpu);  
  
array(  
    int _E0,  
    accelerator_view _Av,  
    Concurrency::accelerator_view _Associated_Av) restrict(cpu);  
  
array(  
    int _E0,  
    int _E1,  
    Concurrency::accelerator_view _Av,  
    Concurrency::accelerator_view _Associated_Av) restrict(cpu);  
  
array(  
    int _E0,  
    int _E1,  
    int _E2,  
    Concurrency::accelerator_view _Av,  
    Concurrency::accelerator_view _Associated_Av) restrict(cpu);  
  
template <typename _InputIterator>  
array(  
    const Concurrency::extent<_Rank>& _Extent,  
    _InputIterator _Src_first,  
    _InputIterator _Src_last) restrict(cpu);  
  
template <typename _InputIterator>  
array(  
    const Concurrency::extent<_Rank>& _Extent,  
    _InputIterator _Src_first) restrict(cpu);  
  
template <typename _InputIterator>  
array(  
    int _E0,  
    _InputIterator _Src_first,  
    _InputIterator _Src_last) restrict(cpu);  
  
template <typename _InputIterator>  
array(  
    int _E0,  
    _InputIterator _Src_first) restrict(cpu);  
  
template <typename _InputIterator>  
array(  
    int _E0,  
    int _E1,  
    _InputIterator _Src_first,  
    _InputIterator _Src_last) restrict(cpu);  
  
template <typename _InputIterator>  
array(  
    int _E0,  
    int _E1,  
    _InputIterator _Src_first) restrict(cpu);  
  
template <typename _InputIterator>  
array(  
    int _E0,  
    int _E1,  
    int _E2,  
    _InputIterator _Src_first, 
    _InputIterator _Src_last) restrict(cpu);
  
template <typename _InputIterator>  
array(  
    int _E0,  
    int _E1,  
    int _E2,  
    _InputIterator _Src_first) restrict(cpu);  
  
template <typename _InputIterator>  
array(  
    const Concurrency::extent<_Rank>& _Extent,  
    _InputIterator _Src_first,  
    _InputIterator _Src_last,  
    Concurrency::accelerator_view _Av  
    access_type _Cpu_access_type = access_type_auto) restrict(cpu);  
  
template <typename _InputIterator>  
array(  
    const Concurrency::extent<_Rank>& _Extent,  
    _InputIterator _Src_first,  
    Concurrency::accelerator_view _Av  
    access_type _Cpu_access_type = access_type_auto) restrict(cpu);  
  
template <typename _InputIterator>  
array(  
    int _E0,  
    _InputIterator _Src_first,  
    _InputIterator _Src_last,  
    Concurrency::accelerator_view _Av  
    access_type _Cpu_access_type = access_type_auto) restrict(cpu);  
  
template <typename _InputIterator>  
array(  
    int _E0,  
    _InputIterator _Src_first,  
    Concurrency::accelerator_view _Av  
    access_type _Cpu_access_type = access_type_auto) restrict(cpu);  
  
template <typename _InputIterator>  
array(  
    int _E0,  
    int _E1,  
    _InputIterator _Src_first,  
    _InputIterator _Src_last,  
    Concurrency::accelerator_view _Av  
    access_type _Cpu_access_type = access_type_auto) restrict(cpu);  
  
template <typename _InputIterator>  
array(
    int _E0,  
    int _E1,  
    _InputIterator _Src_first,  
    Concurrency::accelerator_view _Av  
    access_type _Cpu_access_type = access_type_auto) restrict(cpu);  
  
template <typename _InputIterator>  
array(  
    int _E0,  
    int _E1,  
    int _E2,  
    _InputIterator _Src_first,  
    _InputIterator _Src_last,    
    Concurrency::accelerator_view _Av,  
    access_type _Cpu_access_type = access_type_auto) restrict(cpu);  
  
template <typename _InputIterator>  
array(  
    int _E0,  
    int _E1,  
    int _E2,  
    _InputIterator _Src_first,  
    Concurrency::accelerator_view _Av  
    access_type _Cpu_access_type = access_type_auto) restrict(cpu);  
  
template <typename _InputIterator>  
array(  
    const Concurrency::extent<_Rank>& _Extent,  
    _InputIterator _Src_first,  
    _InputIterator _Src_last,  
    Concurrency::accelerator_view _Av,  
    Concurrency::accelerator_view _Associated_Av) restrict(cpu);  
  
template <typename _InputIterator>  
array(  
    const Concurrency::extent<_Rank>& _Extent,  
    _InputIterator _Src_first,  
    Concurrency::accelerator_view _Av,  
    Concurrency::accelerator_view _Associated_Av) restrict(cpu);  
  
template <typename _InputIterator>  
array(  
    int _E0,  
    _InputIterator _Src_first,  
    _InputIterator _Src_last,  
    Concurrency::accelerator_view _Av,  
    Concurrency::accelerator_view _Associated_Av) restrict(cpu);  
  
template <typename _InputIterator>  
array(  
    int _E0, _InputIterator _Src_first,  
    Concurrency::accelerator_view _Av,  
    Concurrency::accelerator_view _Associated_Av) restrict(cpu);  
  
template <typename _InputIterator>  
array(  
    int _E0,  
    int _E1, _InputIterator _Src_first, _InputIterator _Src_last,  
    Concurrency::accelerator_view _Av,  
    Concurrency::accelerator_view _Associated_Av) restrict(cpu);  
  
template <typename _InputIterator>  
array(  
    int _E0,  
    int _E1, _InputIterator _Src_first,  
    Concurrency::accelerator_view _Av,  
    Concurrency::accelerator_view _Associated_Av) restrict(cpu);  
  
template <typename _InputIterator>  
array(  
    int _E0,  
    int _E1,  
    int _E2, _InputIterator _Src_first, _InputIterator _Src_last,  
    Concurrency::accelerator_view _Av,  
    Concurrency::accelerator_view _Associated_Av) restrict(cpu);  
  
template <typename _InputIterator>  
array(  
    int _E0,  
    int _E1,  
    int _E2, _InputIterator _Src_first,  
    Concurrency::accelerator_view _Av,  
    Concurrency::accelerator_view _Associated_Av) restrict(cpu);  
  
explicit array(  
    const array_view<const value_type, _Rank>& _Src) restrict(cpu);  
  
array(  
    const array_view<const value_type, _Rank>& _Src,  
    accelerator_view _Av  
    access_type _Cpu_access_type = access_type_auto) restrict(cpu);  
  
array(
    const array_view<const value_type, _Rank>& _Src,  
    accelerator_view _Av,  
    accelerator_view _Associated_Av) restrict(cpu);  
  
array(const array& _Other) restrict(cpu);  
  
array(array&& _Other) restrict(cpu);  
```  
  
### <a name="parameters"></a>Parametry  
 `_Associated_Av`  
 Accelerator_view, który określa lokalizację docelową preferowanych tablicy.  
  
 `_Av`  
 [Accelerator_view](accelerator-view-class.md) obiekt, który określa lokalizację, w tablicy.  
  
 `_Cpu_access_type`  
 Żądane [access_type](concurrency-namespace-enums-amp.md#access_type) dla tablicy na Procesor. Ten parametr ma wartość domyślną `access_type_auto` pozostawienie Procesora `access_type` oznaczanie do środowiska wykonawczego. Rzeczywiste użycie procesora CPU `access_type` dla tablicy można wyświetlić przy użyciu `get_cpu_access_type` metody.  
  
 `_Extent`  
 Zakres w każdego wymiaru tablicy.  
  
 `_E0`  
 Najbardziej znaczący składnik zakres w tej sekcji.  
  
 `_E1`  
 Składnik dalej do większość — znaczące zakresu w tej sekcji.  
  
 `_E2`  
 Najmniej znaczący składnik zakres w tej sekcji.  
  
 `_InputIterator`  
 Typ wejściowy interator.  
  
 `_Src`  
 Aby obiekt do skopiowania.  
  
 `_Src_first`  
 Iterator początek w kontenerze źródła.  
  
 `_Src_last`  
 Końcowy iteratora w kontenerze źródła.  
  
 `_Other`  
 Inne źródła danych.  
  
 `_Rank`  
 Ranga sekcji.  
  
 `value_type`  
 Typ danych elementów, które są kopiowane.  
  
##  <a name="associated_accelerator_view"></a> associated_accelerator_view — 

 Pobiera drugi [accelerator_view](accelerator-view-class.md) obiekt, który jest przekazywany jako parametru wywołanego przemieszczania Konstruktor do tworzenia wystąpienia `array` obiektu.  
  
```  
__declspec(property(get= get_associated_accelerator_view)) Concurrency::accelerator_view associated_accelerator_view;  
```  
  
##  <a name="copy_to"></a> copy_to 

 Kopiuje zawartość `array` do innego `array`.  
  
```  
void copy_to(
    array<value_type, _Rank>& _Dest) const ;  
 
void copy_to(
    array_view<value_type, _Rank>& _Dest) const ;  
```  
  
### <a name="parameters"></a>Parametry  
 `_Dest`  
 [Array_view —](array-view-class.md) obiektu można skopiować do.  
  
##  <a name="cpu_access_type"></a> cpu_access_type 

 Pobiera access_type Procesora dozwolone dla tej tablicy.  
  
```  
__declspec(property(get= get_cpu_access_type)) access_type cpu_access_type;  
```  
  
##  <a name="data"></a> Dane 

 Zwraca wskaźnik do dane pierwotne `array`.  
  
```  
value_type* data() restrict(amp, cpu);
  
const value_type* data() const restrict(amp, cpu);
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Wskaźnik do danych pierwotnych w tablicy.  
  
##  <a name="extent"></a> zakres 

 Pobiera [zakres](extent-class.md) obiektu, który definiuje kształt `array`.  
  
```  
__declspec(property(get= get_extent)) Concurrency::extent<_Rank> extent;  
```  
  
##  <a name="get_accelerator_view"></a> get_accelerator_view 

 Zwraca [accelerator_view](accelerator-view-class.md) obiekt, który reprezentuje lokalizację gdzie `array` obiekt został przydzielony. Ta właściwość jest dostępna tylko na Procesor.  
  
```  
Concurrency::accelerator_view get_accelerator_view() const;  
```    
  
### <a name="return-value"></a>Wartość zwracana  
 `accelerator_view` Obiekt, który reprezentuje lokalizację gdzie `array` obiekt został przydzielony.  
  
##  <a name="get_associated_accelerator_view"></a> get_associated_accelerator_view 

 Pobiera drugi [accelerator_view](accelerator-view-class.md) obiekt, który jest przekazywany jako parametru wywołanego przemieszczania Konstruktor do tworzenia wystąpienia `array` obiektu.  
  
```  
Concurrency::accelerator_view get_associated_accelerator_view() const ;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Drugi [accelerator_view](accelerator-view-class.md) obiekt przekazany do konstruktora tymczasowej.  
  
##  <a name="get_cpu_access_type"></a> get_cpu_access_type 

 Zwraca access_type Procesora, jaki jest dozwolony dla tej tablicy.  
  
```  
access_type get_cpu_access_type() const restrict(cpu);
```  
  
### <a name="return-value"></a>Wartość zwracana  
  
##  <a name="get_extent"></a> get_extent 

 Zwraca [zakres](extent-class.md) obiektu `array`.  
  
```  
Concurrency::extent<_Rank> get_extent() const restrict(amp,cpu);
```  
  
### <a name="return-value"></a>Wartość zwracana  
 `extent` Obiektu `array`.  
  
##  <a name="operator_vec"></a> Operator std::vector&lt;value_type&gt; 

 Używa `copy(*this, vector)` niejawnie przekonwertować na obiekt std::vector tablicy.  
  
```  
operator std::vector<value_type>() const restrict(cpu);
```  
  
### <a name="parameters"></a>Parametry  
 `value_type`  
 Typ danych elementów wektora.  
  
### <a name="return-value"></a>Wartość zwracana  
 Obiekt typu `vector<T>` zawierający kopię danych, który jest zawarty w tablicy.  
  
##  <a name="operator_call"></a> Operator() 

 Zwraca wartość elementu określoną przez parametry.  
  
```  
value_type& operator() (const index<_Rank>& _Index) restrict(amp,cpu);  
  
const value_type& operator() (const index<_Rank>& _Index) cons  t restrict(amp,cpu);
  
value_type& operator() (int _I0, int _I1) restrict(amp,cpu);  
  
const value_type& operator() (int _I0, int _I1) const restrict(amp,cpu)  ;
  
value_type& operator() (int _I0, int _I1, int _I2) restrict(amp,cpu);  
  
const value_type& operator() (int _I0, int _I1, int _I2) const restrict(amp,cpu);  
  
typename details::_Projection_result_type<value_type,_Rank>::_Result_type operator()(int _I) restrict(amp,cpu);  
  
typename details::_Projection_result_type<value_type,_Rank>::_Const_result_type operator()(int _I) const restrict(amp,cpu);  
```  
  
### <a name="parameters"></a>Parametry  
 `_Index`  
 Lokalizacja elementu.  
  
 `_I0`  
 Najbardziej znaczący składnik pochodzenia danych w tej sekcji.  
  
 `_I1`  
 Składnik dalej do większość — znaczące pochodzenia danych w tej sekcji.  
  
 `_I2`  
 Składnik najmniej znaczący pochodzenia danych w tej sekcji.  
  
 `_I`  
 Lokalizacja elementu.  
  
### <a name="return-value"></a>Wartość zwracana  
 Wartość elementu określoną przez parametry.  
  
##  <a name="operator_at"></a> Operator] 

 Zwraca element pod określonym indeksem.  
  
```  
value_type& operator[](const index<_Rank>& _Index) restrict(amp,cpu);  
  
const value_type& operator[]  
    (const index<_Rank>& _Index) const restrict(amp,cpu);  
  
typename details::_Projection_result_type<value_type,_Rank>::_Result_type operator[](int _i) restrict(amp,cpu);
  
typename details::_Projection_result_type<value_type,_Rank>::_Const_result_type operator[](int _i) const restrict(amp,cpu);
```  
    
### <a name="parameters"></a>Parametry  
 `_Index`  
 Indeks.  
  
 `_I`  
 Indeks.  
  
### <a name="return-value"></a>Wartość zwracana  
 Element pod określonym indeksem.  
  
##  <a name="operator_eq"></a> operator = 

 Kopiuje zawartość określonego `array` obiektu.  
  
```  
array& operator= (const array& _Other) restrict(cpu);  
   
array& operator= (array&& _Other) restrict(cpu);  
 
array& operator= (  
    const array_view<const value_type, _Rank>& _Src) restrict(cpu);
```  
  
### <a name="parameters"></a>Parametry  
 `_Other`  
 `array` Obiektu do skopiowania.  
  
 `_Src`  
 `array` Obiektu do skopiowania.  
  
### <a name="return-value"></a>Wartość zwracana  
 Odwołanie do tego `array` obiektu.  
  
##  <a name="rank"></a> Ranga 

 Przechowuje rangę `array`.  
  
```  
static const int rank = _Rank;  
```  
## <a name="reinterpret_as"></a> reinterpret_as 

Reinterprets tablicy za pomocą jednowymiarowa array_view —, który opcjonalnie może mieć typu wartość inną niż źródłowa tablica.

### <a name="syntax"></a>Składnia
``` 
template <typename _Value_type2>  
array_view<_Value_type2,1> reinterpret_as() restrict(amp,cpu);  
  
template <typename _Value_type2>  
array_view<const _Value_type2, 1> reinterpret_as() const restrict(amp,cpu);  
``` 
  
### <a name="parameters"></a>Parametry  
`_Value_type2` Typ danych zwracanych danych.

### <a name="return-value"></a>Wartość zwracana
Array_view — lub obiekt const array_view — jest oparta na tablicy o typie elementu reinterpreted z T ElementType i rangę zmniejszona od N do 1.

### <a name="remarks"></a>Uwagi
Czasami jest wygodne wyświetlić tablicy wielowymiarowej tak, jakby prawdopodobnie typu wartość inną niż źródłowa tablica jest tablicą jednowymiarową, liniowego. Ta metoda umożliwia to osiągnąć.
**Uwaga** Reinterpreting tablicy obiektów przy użyciu innej wartości typu jest potencjalnie niebezpieczna operacja. Firma Microsoft zaleca ostrożne korzystanie z tej funkcji. 

Poniższy kod stanowi przykład.

```cpp  
struct RGB { float r; float g; float b; };

array<RGB,3>  a = ...; 
array_view<float,1> v = a.reinterpret_as<float>(); 

assert(v.extent == 3*a.extent);
```  
  
##  <a name="section"></a> Sekcja 

 Zwraca podsekcją `array` obiektu, który znajduje się w określonym pochodzenia i, opcjonalnie, który ma określony zakres.  
  
```  
array_view<value_type,_Rank> section(
    const Concurrency::index<_Rank>& _Section_origin,  
    const Concurrency::extent<_Rank>& _Section_extent) restrict(amp,cpu);
  
array_view<const value_type,_Rank> section(
    const Concurrency::index<_Rank>& _Section_origin,  
    const Concurrency::extent<_Rank>& _Section_extent) const restrict(amp,cpu);
  
array_view<value_type,_Rank> section(
    const Concurrency::extent<_Rank>& _Ext) restrict(amp,cpu);
  
array_view<const value_type,_Rank> section(
    const Concurrency::extent<_Rank>& _Ext) const restrict(amp,cpu);
  
array_view<value_type,_Rank> section(
    const index<_Rank>& _Idx) restrict(amp,cpu);
  
array_view<const value_type,_Rank> section(
    const index<_Rank>& _Idx) const restrict(amp,cpu);
  
array_view<value_type,1> section(
    int _I0,  
    int _E0) restrict(amp,cpu);
  
array_view<const value_type,1> section(
    int _I0,  
    int _E0) const restrict(amp,cpu);
  
array_view<value_type,2> section(
    int _I0,  
    int _I1,  
    int _E0,  
    int _E1) restrict(amp,cpu);
  
array_view<const value_type,2> section(
    int _I0,  
    int _I1,  
    int _E0,  
    int _E1) const restrict(amp,cpu);
  
array_view<value_type,3> section(
    int _I0,  
    int _I1,  
    int _I2,  
    int _E0,  
    int _E1,  
    int _E2) restrict(amp,cpu);
  
array_view<const value_type,3> section(
    int _I0,  
    int _I1,  
    int _I2,  
    int _E0,  
    int _E1,  
    int _E2) const restrict(amp,cpu);
```  
  
### <a name="parameters"></a>Parametry  
 `_E0`  
 Najbardziej znaczący składnik zakres w tej sekcji.  
  
 `_E1`  
 Składnik dalej do większość — znaczące zakresu w tej sekcji.  
  
 `_E2`  
 Najmniej znaczący składnik zakres w tej sekcji.  
  
 `_Ext`  
 [Zakres](extent-class.md) obiekt określający zakres sekcji. Punkt początkowy jest równa 0.  
  
 `_Idx`  
 [Indeksu](index-class.md) obiektu, który określa lokalizację źródła. Podsekcji jest pozostałej części zakresu.  
  
 `_I0`  
 Najbardziej znaczący składnik pochodzenia danych w tej sekcji.  
  
 `_I1`  
 Składnik dalej do większość — znaczące pochodzenia danych w tej sekcji.  
  
 `_I2`  
 Składnik najmniej znaczący pochodzenia danych w tej sekcji.  
  
 `_Rank`  
 Ranga sekcji.  
  
 `_Section_extent`  
 [Zakres](extent-class.md) obiekt określający zakres sekcji.  
  
 `_Section_origin`  
 [Indeksu](index-class.md) obiektu, który określa lokalizację źródła.  
  
 `value_type`  
 Typ danych elementów, które są kopiowane.  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca podsekcją `array` obiektu, który znajduje się w określonym pochodzenia i, opcjonalnie, który ma określony zakres. Gdy tylko `index` obiektu jest określony, podsekcja zawiera wszystkie elementy w siatce skojarzone indeksy, które są większe niż indeksów elementów w `index` obiektu.  
  
##  <a name="view_as"></a> view_as 

 Reinterprets tej tablicy jako [array_view —](array-view-class.md) różnych rangi.  
  
```  
template <int _New_rank>  
array_view<value_type,_New_rank> view_as(
    const Concurrency::extent<_New_rank>& _View_extent) restrict(amp,cpu);

 
template <int _New_rank>  
array_view<const value_type,_New_rank> view_as(
    const Concurrency::extent<_New_rank>& _View_extent) const restrict(amp,cpu);
```  
  
### <a name="parameters"></a>Parametry  
 `_New_rank`  
 Rangę `extent` przekazano obiekt jako parametr.  
  
 `_View_extent`  
 Zakres używany do utworzenia nowego [array_view —](array-view-class.md) obiektu.  
  
 `value_type`  
 Typ danych elementów w oryginalnym zarówno `array` obiekt i zwrócona `array_view` obiektu.  
  
### <a name="return-value"></a>Wartość zwracana  
 [Array_view —](array-view-class.md) obiektu, który jest tworzony.  
  
## <a name="see-also"></a>Zobacz też  
 [Przestrzeń nazw współbieżności (C++ AMP)](concurrency-namespace-cpp-amp.md)
