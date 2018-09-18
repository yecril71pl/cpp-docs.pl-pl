---
title: Array — klasa | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-amp
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: abf907fe12f55b44e7f2e184b8752d2e09a326f8
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46071734"
---
# <a name="array-class"></a>array — Klasa
Reprezentuje kontener danych służący do przenoszenia danych do akceleratora.

## <a name="syntax"></a>Składnia

```  
template <typename value_type, int _Rank>
friend class array;
```  

#### <a name="parameters"></a>Parametry
*value_type*<br/>
Typ elementu danych.

*_Rank*<br/>
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
|[Dane](#data)|Zwraca wskaźnik do danych pierwotnych tablicy.|
|[get_accelerator_view](#get_accelerator_view)|Zwraca [accelerator_view](accelerator-view-class.md) obiekt, który reprezentuje lokalizację, w której zaalokowano tablicę. Ta właściwość jest możliwy tylko na procesorze CPU.|
|[get_associated_accelerator_view](#get_associated_accelerator_view)|Pobiera drugi [accelerator_view](accelerator-view-class.md) obiektu, który jest przekazywany jako parametr gdy wywołany zostanie Konstruktor tymczasowy w celu utworzenia wystąpienia `array` obiektu.|
|[get_cpu_access_type](#get_cpu_access_type)|Zwraca [access_type](concurrency-namespace-enums-amp.md#access_type) tablicy. Ta metoda jest możliwy tylko na procesorze CPU.|
|[get_extent](#get_extent)|Zwraca [zakres](extent-class.md) obiektu tablicy.|
|[reinterpret_as](#reinterpret_as)|Zwraca jednowymiarową tablicę, która zawiera wszystkie elementy w `array` obiektu.|
|[sekcja](#section)|Zwraca podsekcję obiektu `array` obiektu, który znajduje się w określonej lokalizacji i, opcjonalnie, który ma określony zakres.|
|[view_as](#view_as)|Zwraca [array_view](array-view-class.md) obiektu, który jest konstruowany z `array` obiektu.|

### <a name="public-operators"></a>Operatory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[Operator std::vector&lt;value_type&gt;](#operator_vec)|Używa `copy(*this, vector)` można niejawnie przekonwertować tablicę do std::[wektor](../../../standard-library/vector-class.md) obiektu.|
|[operator()](#operator_call)|Zwraca wartość elementu, która jest określona przez parametry.|
|[Operator]](#operator_at)|Zwraca element, który jest umieszczony pod określonym indeksem.|
|[operator=](#operator_eq)|Kopiuje zawartość określonego `array` obiektu do wskazanego.|

### <a name="public-constants"></a>Publiczne stałe

|Nazwa|Opis|
|----------|-----------------|
|[Rank — stała](#rank)|Przechowuje rangę tablicy.|

### <a name="public-data-members"></a>Publiczne elementy członkowskie danych

|Nazwa|Opis|
|----------|-----------------|
|[accelerator_view](#accelerator_view)|Pobiera [accelerator_view](accelerator-view-class.md) obiekt, który reprezentuje lokalizację, w której zaalokowano tablicę. Ta właściwość jest możliwy tylko na procesorze CPU.|
|[associated_accelerator_view](#associated_accelerator_view)|Pobiera drugi [accelerator_view](accelerator-view-class.md) obiektu, który jest przekazywany jako parametr gdy wywołany zostanie Konstruktor tymczasowy w celu utworzenia wystąpienia `array` obiektu.|
|[cpu_access_type](#cpu_access_type)|Pobiera [access_type](concurrency-namespace-enums-amp.md#access_type) reprezentujący jak Procesor może uzyskać dostęp do magazynu tablicy.|
|[extent](#extent)|Pobiera zakres, który definiuje kształt tablicy.|

## <a name="remarks"></a>Uwagi
Typ `array<T,N>` reprezentuje gęstą i regularną (niepostrzępioną) *N*-wymiarową tablicę znajdującą się w określonej lokalizacji, na przykład w akceleratorze lub procesorze CPU. Typ danych elementów w tablicy jest `T`, który musi być typu, który jest zgodny z akceleratorem docelowego. Mimo że rangi `N`, (z tablicy jest określana statycznie i jest częścią typu, zakres tablicy jest ustalany w czasie wykonywania i jest wyrażany za pomocą klasy `extent<N>`.

Tablica może mieć dowolną liczbę wymiarów, chociaż niektóre funkcje są ukierunkowane na `array` obiekty o liczbie wymiarów równej jeden, dwa lub trzy. Jeżeli pominięto argument wymiaru, wartość domyślna to 1.

Dane tablicy są ułożone w sposób ciągły w pamięci. Elementy, które różnią się o jeden w najmniej znaczącego wymiaru są obok siebie w pamięci.

Tablice są logicznie uznawane za typy wartości, ponieważ gdy tablica jest kopiowana do innej tablicy, jest wykonywana jest głęboka kopia. Dwie tablice nigdy nie wskazują na te same dane.

`array<T,N>` Typ jest używany w kilku scenariuszach:

-   Jako kontener danych, który może być używany w obliczeniach na akceleratorze.

-   Jako kontener danych do przechowywania pamięci na hoście Procesora (który może służyć do skopiowania do i z innych tablic).

-   Jako tymczasowy obiekt jako szybkiego pośrednika w kopiach urządzeniem hosta.

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia
`array`  

## <a name="requirements"></a>Wymagania
**Nagłówek:** amp.h

**Namespace:** współbieżności

##  <a name="dtor"></a> ~ array

Niszczy `array` obiektu.

```  
~array() restrict(cpu);
```  

##  <a name="accelerator_view"></a> accelerator_view

Pobiera [accelerator_view](accelerator-view-class.md) obiekt, który reprezentuje lokalizację, w której zaalokowano tablicę. Ta właściwość jest możliwy tylko na procesorze CPU.

```  
__declspec(property(get= get_accelerator_view)) Concurrency::accelerator_view accelerator_view;
```  

##  <a name="ctor"></a> Tablica

Inicjuje nowe wystąpienie klasy [array, klasa](array-class.md). Brak domyślnego konstruktora dla `array<T,N>`. Wszystkie konstruktory są uruchamiane tylko na Procesorze. Nie mogą być wykonywane docelowo na Direct3D.

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
*_Associated_Av*<br/>
Obiekt accelerator_view, który określa preferowaną lokalizację docelową tablicy.

*_Av*<br/>
[Accelerator_view](accelerator-view-class.md) obiektu, który określa lokalizację tablicy.

*_Cpu_access_type*<br/>
Żądany [access_type](concurrency-namespace-enums-amp.md#access_type) dla tablicy na CPU. Ten parametr ma wartość domyślną `access_type_auto` opuszczania Procesora `access_type` oznaczanie do środowiska uruchomieniowego. Rzeczywiste użycie procesora CPU `access_type` dla tablicy może być odpytywany za pomocą `get_cpu_access_type` metody.

*_Extent*<br/>
Zakres każdego wymiaru tablicy.

*_E0*<br/>
Najbardziej znaczący składnik z zakresu sekcji.

*_E1*<br/>
Dalej do najbardziej znaczący składnik z zakresu sekcji.

*_E2*<br/>
Najmniej znaczący składnik z zakresu sekcji.

*_InputIterator*<br/>
Typ iteratora wejściowego.

*_Src*<br/>
Obiekt do skopiowania.

*_Src_first*<br/>
Początkowy iterator do kontenera źródłowego.

*_Src_last*<br/>
Końcowy iterator do kontenera źródłowego.

*_Inne*<br/>
Inne źródła danych.

*_Rank*<br/>
Ranga sekcji.

*value_type*<br/>
Typ danych elementów, które są kopiowane.

##  <a name="associated_accelerator_view"></a> associated_accelerator_view —

Pobiera drugi [accelerator_view](accelerator-view-class.md) obiektu, który jest przekazywany jako parametr gdy wywołany zostanie Konstruktor tymczasowy w celu utworzenia wystąpienia `array` obiektu.

```  
__declspec(property(get= get_associated_accelerator_view)) Concurrency::accelerator_view associated_accelerator_view;
```  

##  <a name="copy_to"></a> copy_to —

Kopiuje zawartość `array` do innego `array`.

```  
void copy_to(
    array<value_type, _Rank>& _Dest) const ;

void copy_to(
    array_view<value_type, _Rank>& _Dest) const ;
```  

### <a name="parameters"></a>Parametry
*_Dest*<br/>
[Array_view](array-view-class.md) kopiowanego.

##  <a name="cpu_access_type"></a> cpu_access_type

Pobiera atrybut access_type Procesora dozwolony dla tej tablicy.

```  
__declspec(property(get= get_cpu_access_type)) access_type cpu_access_type;
```  

##  <a name="data"></a> Dane

Zwraca wskaźnik do danych pierwotnych `array`.

```  
value_type* data() restrict(amp, cpu);

const value_type* data() const restrict(amp, cpu);
```  

### <a name="return-value"></a>Wartość zwracana
Wskaźnik do danych pierwotnych tablicy.

##  <a name="extent"></a> zakres

Pobiera [zakres](extent-class.md) obiekt, który definiuje kształt `array`.

```  
__declspec(property(get= get_extent)) Concurrency::extent<_Rank> extent;
```  

##  <a name="get_accelerator_view"></a> get_accelerator_view —

Zwraca [accelerator_view](accelerator-view-class.md) obiekt reprezentujący lokalizację, gdzie `array` obiektowi przypisany. Ta właściwość jest możliwy tylko na procesorze CPU.

```  
Concurrency::accelerator_view get_accelerator_view() const;
```    

### <a name="return-value"></a>Wartość zwracana
`accelerator_view` Obiekt reprezentujący lokalizację, gdzie `array` obiektowi przypisany.

##  <a name="get_associated_accelerator_view"></a> get_associated_accelerator_view —

Pobiera drugi [accelerator_view](accelerator-view-class.md) obiektu, który jest przekazywany jako parametr gdy wywołany zostanie Konstruktor tymczasowy w celu utworzenia wystąpienia `array` obiektu.

```  
Concurrency::accelerator_view get_associated_accelerator_view() const ;
```  

### <a name="return-value"></a>Wartość zwracana
Drugi [accelerator_view](accelerator-view-class.md) obiekt przekazany do konstruktora przemieszczania.

##  <a name="get_cpu_access_type"></a> get_cpu_access_type

Zwraca access_type Procesora dozwolony dla tej tablicy.

```  
access_type get_cpu_access_type() const restrict(cpu);
```  

### <a name="return-value"></a>Wartość zwracana

##  <a name="get_extent"></a> get_extent —

Zwraca [zakres](extent-class.md) obiektu `array`.

```  
Concurrency::extent<_Rank> get_extent() const restrict(amp,cpu);
```  

### <a name="return-value"></a>Wartość zwracana
`extent` Obiektu `array`.

##  <a name="operator_vec"></a> Operator std::vector&lt;value_type&gt;

Używa `copy(*this, vector)` można niejawnie przekonwertować tablicę do obiektu std::vector.

```  
operator std::vector<value_type>() const restrict(cpu);
```  

### <a name="parameters"></a>Parametry
*value_type*<br/>
Typ danych elementów wektora.

### <a name="return-value"></a>Wartość zwracana
Obiekt typu `vector<T>` zawierający kopię danych, który jest zawarty w tablicy.

##  <a name="operator_call"></a> Operator() 

Zwraca wartość elementu, która jest określona przez parametry.

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
*Parametr _Index*<br/>
Lokalizacja elementu.

*_I0*<br/>
Najbardziej znaczący składnik pochodzenia tej sekcji.

*_I1*<br/>
Dalej do najbardziej znaczący składnik pochodzenia tej sekcji.

*_I2*<br/>
Najmniej znaczący składnik pochodzenia tej sekcji.

*_I*<br/>
Lokalizacja elementu.

### <a name="return-value"></a>Wartość zwracana
Wartość elementu określona przez parametry.

##  <a name="operator_at"></a> Operator]

Zwraca element, który jest umieszczony pod określonym indeksem.

```  
value_type& operator[](const index<_Rank>& _Index) restrict(amp,cpu);

const value_type& operator[]
    (const index<_Rank>& _Index) const restrict(amp,cpu);

typename details::_Projection_result_type<value_type,_Rank>::_Result_type operator[](int _i) restrict(amp,cpu);

typename details::_Projection_result_type<value_type,_Rank>::_Const_result_type operator[](int _i) const restrict(amp,cpu);
```  

### <a name="parameters"></a>Parametry
*Parametr _Index*<br/>
Indeks.

*_I*<br/>
Indeks.

### <a name="return-value"></a>Wartość zwracana
Element, który jest umieszczony pod określonym indeksem.

##  <a name="operator_eq"></a> operator =

Kopiuje zawartość określonego `array` obiektu.

```  
array& operator= (const array& _Other) restrict(cpu);

array& operator= (array&& _Other) restrict(cpu);

array& operator= (  
    const array_view<const value_type, _Rank>& _Src) restrict(cpu);
```  

### <a name="parameters"></a>Parametry
*_Inne*<br/>
`array` Obiektu do skopiowania.

*_Src*<br/>
`array` Obiektu do skopiowania.

### <a name="return-value"></a>Wartość zwracana
Odwołanie do `array` obiektu.

##  <a name="rank"></a> Ranga

Przechowuje rangę obiektu `array`.

```  
static const int rank = _Rank;
```  
## <a name="reinterpret_as"></a> reinterpret_as —

Reinterpretuje obiekt array za pośrednictwem jednowymiarowego obiektu array_view, który opcjonalnie może mieć inny typ wartości niż tablica źródłowa.

### <a name="syntax"></a>Składnia
``` 
template <typename _Value_type2>
array_view<_Value_type2,1> reinterpret_as() restrict(amp,cpu);

template <typename _Value_type2>
array_view<const _Value_type2, 1> reinterpret_as() const restrict(amp,cpu);
``` 

### <a name="parameters"></a>Parametry

*_Value_type2*<br/>
Typ danych zwracanych danych.

### <a name="return-value"></a>Wartość zwracana
Array_view lub stała obiektu array_view, który opiera się na tablicy, z typem elementu reinterpretowanym z T ElementType i rangi mniejsze od N do 1.

### <a name="remarks"></a>Uwagi
Czasami wygodne jest wyświetlanie tablicy wielowymiarowej, tak jak w przypadku liniowych, jednowymiarową tablicę, prawdopodobnie z innego typu wartości niż tablica źródłowa. Można to osiągnąć, można użyć tej metody.
**Ostrzeżenie** Reinterpretacja obiektu array przy użyciu innego typu wartości jest operacją potencjalnie niebezpieczną. Zalecamy ostrożne korzystanie z tej funkcji.

Poniższy kod zawiera przykład.

```cpp
struct RGB { float r; float g; float b; };

array<RGB,3>  a = ...;
array_view<float,1> v = a.reinterpret_as<float>();

assert(v.extent == 3*a.extent);
```  

##  <a name="section"></a> Sekcja

Zwraca podsekcję obiektu `array` obiektu, który znajduje się w określonej lokalizacji i, opcjonalnie, który ma określony zakres.

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
*_E0*<br/>
Najbardziej znaczący składnik z zakresu sekcji.

*_E1*<br/>
Dalej do najbardziej znaczący składnik z zakresu sekcji.

*_E2*<br/>
Najmniej znaczący składnik z zakresu sekcji.

*_Ext*<br/>
[Zakres](extent-class.md) obiektu, który określa zakres sekcji. Wartość pierwotna wynosi 0.

*_Idx*<br/>
[Indeksu](index-class.md) obiektu, który określa lokalizację pochodzenia. Podsekcja jest pozostałą częścią zakresu.

*_I0*<br/>
Najbardziej znaczący składnik pochodzenia tej sekcji.

*_I1*<br/>
Dalej do najbardziej znaczący składnik pochodzenia tej sekcji.

*_I2*<br/>
Najmniej znaczący składnik pochodzenia tej sekcji.

*_Rank*<br/>
Ranga sekcji.

*_Section_extent*<br/>
[Zakres](extent-class.md) obiektu, który określa zakres sekcji.

*_Section_origin*<br/>
[Indeksu](index-class.md) obiektu, który określa lokalizację pochodzenia.

*value_type*<br/>
Typ danych elementów, które są kopiowane.

### <a name="return-value"></a>Wartość zwracana
Zwraca podsekcję obiektu `array` obiektu, który znajduje się w określonej lokalizacji i, opcjonalnie, który ma określony zakres. Gdy tylko `index` obiektu jest określony, podsekcja zawiera wszystkie elementy w skojarzonej siatce, których indeksy są większe niż indeksy elementów w `index` obiektu.

##  <a name="view_as"></a> view_as —

Reinterpretuje ten obiekt array jako [array_view](array-view-class.md) innej rangi.

```  
template <int _New_rank>
array_view<value_type,_New_rank> view_as(
    const Concurrency::extent<_New_rank>& _View_extent) restrict(amp,cpu);


template <int _New_rank>
array_view<const value_type,_New_rank> view_as(
    const Concurrency::extent<_New_rank>& _View_extent) const restrict(amp,cpu);
```  

### <a name="parameters"></a>Parametry
*_New_rank*<br/>
Ranga `extent` przekazano obiekt jako parametr.

*_View_extent*<br/>
Zakres, który jest używany do utworzenia nowego [array_view](array-view-class.md) obiektu.

*value_type*<br/>
Typ danych elementów w pierwotnym `array` obiektu i zwracanym `array_view` obiektu.

### <a name="return-value"></a>Wartość zwracana
[Array_view](array-view-class.md) obiektu, który jest konstruowany.

## <a name="see-also"></a>Zobacz też
[Przestrzeń nazw współbieżności (C++ AMP)](concurrency-namespace-cpp-amp.md)
