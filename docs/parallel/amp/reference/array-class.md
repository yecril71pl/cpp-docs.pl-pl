---
title: array — Klasa
ms.date: 11/04/2016
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
helpviewer_keywords:
- array class
ms.assetid: 0832b6c1-40f0-421d-9104-6b1baa0c63a7
ms.openlocfilehash: efea8dabb69a48e69d68a86110fdf9bc7664948b
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/11/2020
ms.locfileid: "77127115"
---
# <a name="array-class"></a>array — Klasa

Reprezentuje kontener danych służący do przenoszenia danych do akceleratora.

## <a name="syntax"></a>Składnia

```cpp
template <typename value_type, int _Rank>
friend class array;
```

### <a name="parameters"></a>Parametry

*value_type*<br/>
Typ elementu danych.

*_Rank*<br/>
Ranga tablicy.

## <a name="members"></a>Members

### <a name="public-constructors"></a>Konstruktory publiczne

|Name (Nazwa)|Opis|
|----------|-----------------|
|[Konstruktor Array](#ctor)|Inicjuje nowe wystąpienie klasy `array`.|
|[~ Destruktor tablicy](#dtor)|Niszczy obiekt `array`.|

### <a name="public-methods"></a>Metody publiczne

|Name (Nazwa)|Opis|
|----------|-----------------|
|[copy_to](#copy_to)|Kopiuje zawartość tablicy do innej tablicy.|
|[Data](#data)|Zwraca wskaźnik do danych pierwotnych tablicy.|
|[get_accelerator_view](#get_accelerator_view)|Zwraca obiekt [accelerator_view](accelerator-view-class.md) reprezentujący lokalizację, w której jest przydzielono tablicę. Do tej właściwości można uzyskać dostęp tylko na procesorze CPU.|
|[get_associated_accelerator_view](#get_associated_accelerator_view)|Pobiera drugi [accelerator_view](accelerator-view-class.md) obiektu, który jest przesyłany jako parametr w przypadku wywołania konstruktora przemieszczania w celu utworzenia wystąpienia obiektu `array`.|
|[get_cpu_access_type](#get_cpu_access_type)|Zwraca [access_type](concurrency-namespace-enums-amp.md#access_type) tablicy. Dostęp do tej metody można uzyskać tylko na procesorze CPU.|
|[get_extent](#get_extent)|Zwraca obiekt [zakresu](extent-class.md) tablicy.|
|[reinterpret_as](#reinterpret_as)|Zwraca tablicę jednowymiarową, która zawiera wszystkie elementy w obiekcie `array`.|
|[sekcja](#section)|Zwraca podsekcję obiektu `array`, który znajduje się w podanej lokalizacji i opcjonalnie ma określony zakres.|
|[view_as](#view_as)|Zwraca obiekt [array_view](array-view-class.md) , który jest zbudowany z obiektu `array`.|

### <a name="public-operators"></a>Operatory publiczne

|Name (Nazwa)|Opis|
|----------|-----------------|
|[operator std:: Vector&lt;value_type&gt;](#operator_vec)|Używa `copy(*this, vector)`, aby niejawnie skonwertować tablicę do obiektu[wektora](../../../standard-library/vector-class.md) std:: Vector.|
|[operator ()](#operator_call)|Zwraca wartość elementu, która jest określona przez parametry.|
|[\[operatora \]](#operator_at)|Zwraca element, który znajduje się w określonym indeksie.|
|[operator =](#operator_eq)|Kopiuje zawartość określonego obiektu `array` do tego.|

### <a name="public-constants"></a>Stałe publiczne

|Name (Nazwa)|Opis|
|----------|-----------------|
|[Stała rangi](#rank)|Przechowuje rangę tablicy.|

### <a name="public-data-members"></a>Publiczne elementy członkowskie danych

|Name (Nazwa)|Opis|
|----------|-----------------|
|[accelerator_view](#accelerator_view)|Pobiera obiekt [accelerator_view](accelerator-view-class.md) reprezentujący lokalizację, w której jest przydzielono tablicę. Do tej właściwości można uzyskać dostęp tylko na procesorze CPU.|
|[associated_accelerator_view](#associated_accelerator_view)|Pobiera drugi [accelerator_view](accelerator-view-class.md) obiektu, który jest przesyłany jako parametr w przypadku wywołania konstruktora przemieszczania w celu utworzenia wystąpienia obiektu `array`.|
|[cpu_access_type](#cpu_access_type)|Pobiera [access_type](concurrency-namespace-enums-amp.md#access_type) , które przedstawiają sposób, w jaki procesor może uzyskać dostęp do magazynu macierzy.|
|[rozmiaru](#extent)|Pobiera zakres, który definiuje kształt tablicy.|

## <a name="remarks"></a>Uwagi

Typ `array<T,N>` reprezentuje gęstą i regularną (niepostrzępioną) tablicę *N*-wymiarową, która znajduje się w określonej lokalizacji, na przykład akcelerator lub procesor CPU. Typ danych elementów w tablicy to `T`, które muszą być typu zgodnego z akceleratorem docelowym. Chociaż ranga, `N`, (tablicy jest określana statycznie i jest częścią typu, zakres tablicy jest określany przez środowisko uruchomieniowe i jest wyrażany za pomocą klasy `extent<N>`.

Tablica może mieć dowolną liczbę wymiarów, ale niektóre funkcje są wyspecjalizowane dla `array` obiektów z rangą jeden, dwa i trzy. W przypadku pominięcia argumentu wymiar wartość domyślna to 1.

Dane tablicowe są określane w sposób ciągły w pamięci. Elementy, które różnią się od siebie w najmniej znaczącym wymiarze, są przyległe w pamięci.

Tablice są logicznie uznawane za typy wartości, ponieważ gdy tablica jest kopiowana do innej tablicy, wykonywana jest kopia głęboka. Dwie tablice nigdy nie wskazują na te same dane.

Typ `array<T,N>` jest używany w kilku scenariuszach:

- Jako kontener danych, który może być używany w obliczeniach na akceleratorze.

- Jako kontener danych do przechowywania pamięci na procesorze CPU hosta (który może być używany do kopiowania do i z innych tablic).

- Jako obiekt tymczasowy do działania jako szybkie pośrednika w kopiach między hostami i urządzeniami.

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

`array`

## <a name="requirements"></a>Wymagania

**Nagłówek:** amp. h

**Przestrzeń nazw:** Współbieżności

## <a name="dtor"></a>~ Tablica

Niszczy obiekt `array`.

```cpp
~array() restrict(cpu);
```

## <a name="accelerator_view"></a>accelerator_view

Pobiera obiekt [accelerator_view](accelerator-view-class.md) reprezentujący lokalizację, w której jest przydzielono tablicę. Do tej właściwości można uzyskać dostęp tylko na procesorze CPU.

```cpp
__declspec(property(get= get_accelerator_view)) Concurrency::accelerator_view accelerator_view;
```

## <a name="ctor"></a>macierzy

Inicjuje nowe wystąpienie [klasy Array](array-class.md). Brak domyślnego konstruktora dla `array<T,N>`. Wszystkie konstruktory są uruchamiane tylko na procesorze CPU. Nie można ich wykonać na obiekcie docelowym Direct3D.

```cpp
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
Accelerator_view, która określa preferowaną lokalizację docelową tablicy.

*_Av*<br/>
Obiekt [accelerator_view](accelerator-view-class.md) , który określa lokalizację tablicy.

*_Cpu_access_type*<br/>
Żądany [access_type](concurrency-namespace-enums-amp.md#access_type) tablicy na procesorze. Ten parametr ma wartość domyślną `access_type_auto` opuszczenie `access_type` procesora CPU do środowiska uruchomieniowego. Rzeczywiste `access_type` procesora dla tablicy można zbadać przy użyciu metody `get_cpu_access_type`.

*_Extent*<br/>
Zakres w każdym wymiarze tablicy.

*_E0*<br/>
Najbardziej znaczący składnik zakresu tej sekcji.

*_E1*<br/>
Najbardziej znaczący składnik zakresu tej sekcji.

*_E2*<br/>
Najmniej znaczący składnik zakresu tej sekcji.

*_InputIterator*<br/>
Typ iteratora wejściowego.

*_Src*<br/>
Na obiekt do skopiowania.

*_Src_first*<br/>
Początkowy iterator do kontenera źródłowego.

*_Src_last*<br/>
Końcowy iterator do kontenera źródłowego.

*_Other*<br/>
Inne źródło danych.

*_Rank*<br/>
Ranga sekcji.

*value_type*<br/>
Typ danych elementów, które są kopiowane.

## <a name="associated_accelerator_view"></a>associated_accelerator_view

Pobiera drugi [accelerator_view](accelerator-view-class.md) obiektu, który jest przesyłany jako parametr w przypadku wywołania konstruktora przemieszczania w celu utworzenia wystąpienia obiektu `array`.

```cpp
__declspec(property(get= get_associated_accelerator_view)) Concurrency::accelerator_view associated_accelerator_view;
```

## <a name="copy_to"></a>copy_to

Kopiuje zawartość `array` do innej `array`.

```cpp
void copy_to(
    array<value_type, _Rank>& _Dest) const ;

void copy_to(
    array_view<value_type, _Rank>& _Dest) const ;
```

### <a name="parameters"></a>Parametry

*_Dest*<br/>
Obiekt [array_view](array-view-class.md) , do którego ma zostać skopiowany.

## <a name="cpu_access_type"></a>cpu_access_type

Pobiera access_type procesora CPU dozwolone dla tej tablicy.

```cpp
__declspec(property(get= get_cpu_access_type)) access_type cpu_access_type;
```

## <a name="data"></a>Data

Zwraca wskaźnik do nieprzetworzonych danych `array`.

```cpp
value_type* data() restrict(amp, cpu);

const value_type* data() const restrict(amp, cpu);
```

### <a name="return-value"></a>Wartość zwrócona

Wskaźnik do danych pierwotnych tablicy.

## <a name="extent"></a>rozmiaru

Pobiera obiekt [zakresu](extent-class.md) , który definiuje kształt `array`.

```cpp
__declspec(property(get= get_extent)) Concurrency::extent<_Rank> extent;
```

## <a name="get_accelerator_view"></a>get_accelerator_view

Zwraca obiekt [accelerator_view](accelerator-view-class.md) reprezentujący lokalizację, w której przydzielono obiekt `array`. Do tej właściwości można uzyskać dostęp tylko na procesorze CPU.

```cpp
Concurrency::accelerator_view get_accelerator_view() const;
```

### <a name="return-value"></a>Wartość zwrócona

Obiekt `accelerator_view`, który reprezentuje lokalizację, do której przydzielono obiekt `array`.

## <a name="get_associated_accelerator_view"></a>get_associated_accelerator_view

Pobiera drugi [accelerator_view](accelerator-view-class.md) obiektu, który jest przesyłany jako parametr w przypadku wywołania konstruktora przemieszczania w celu utworzenia wystąpienia obiektu `array`.

```cpp
Concurrency::accelerator_view get_associated_accelerator_view() const ;
```

### <a name="return-value"></a>Wartość zwrócona

Drugi obiekt [accelerator_view](accelerator-view-class.md) przeszedł do konstruktora przemieszczania.

## <a name="get_cpu_access_type"></a>get_cpu_access_type

Zwraca access_type procesora, który jest dozwolony dla tej tablicy.

```cpp
access_type get_cpu_access_type() const restrict(cpu);
```

### <a name="return-value"></a>Wartość zwrócona

## <a name="get_extent"></a>get_extent

Zwraca obiekt [zakresu](extent-class.md) `array`.

```cpp
Concurrency::extent<_Rank> get_extent() const restrict(amp,cpu);
```

### <a name="return-value"></a>Wartość zwrócona

Obiekt `extent` `array`.

## <a name="operator_vec"></a>operator std:: Vector&lt;value_type&gt;

Używa `copy(*this, vector)`, aby niejawnie skonwertować tablicę do obiektu wektora std:: Vector.

```cpp
operator std::vector<value_type>() const restrict(cpu);
```

### <a name="parameters"></a>Parametry

*value_type*<br/>
Typ danych elementów wektora.

### <a name="return-value"></a>Wartość zwrócona

Obiekt typu `vector<T>`, który zawiera kopię danych znajdujących się w tablicy.

## <a name="operator_call"></a>operator ()

Zwraca wartość elementu, która jest określona przez parametry.

```cpp
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

*_Index*<br/>
Lokalizacja elementu.

*_I0*<br/>
Najbardziej znaczący składnik pochodzenia tej sekcji.

*_I1*<br/>
Najbardziej znaczący składnik pochodzenia tej sekcji.

*_I2*<br/>
Najmniej znaczący składnik pochodzenia tej sekcji.

*_I*<br/>
Lokalizacja elementu.

### <a name="return-value"></a>Wartość zwrócona

Wartość elementu określona przez parametry.

## <a name="operator_at"></a>operator []

Zwraca element, który znajduje się w określonym indeksie.

```cpp
value_type& operator[](const index<_Rank>& _Index) restrict(amp,cpu);

const value_type& operator[]
    (const index<_Rank>& _Index) const restrict(amp,cpu);

typename details::_Projection_result_type<value_type,_Rank>::_Result_type operator[](int _i) restrict(amp,cpu);

typename details::_Projection_result_type<value_type,_Rank>::_Const_result_type operator[](int _i) const restrict(amp,cpu);
```

### <a name="parameters"></a>Parametry

*_Index*<br/>
Indeks.

*_I*<br/>
Indeks.

### <a name="return-value"></a>Wartość zwrócona

Element o określonym indeksie.

## <a name="operator_eq"></a>operator =

Kopiuje zawartość określonego obiektu `array`.

```cpp
array& operator= (const array& _Other) restrict(cpu);

array& operator= (array&& _Other) restrict(cpu);

array& operator= (
    const array_view<const value_type, _Rank>& _Src) restrict(cpu);
```

### <a name="parameters"></a>Parametry

*_Other*<br/>
Obiekt `array`, z którego ma być kopiowany.

*_Src*<br/>
Obiekt `array`, z którego ma być kopiowany.

### <a name="return-value"></a>Wartość zwrócona

Odwołanie do tego obiektu `array`.

## <a name="rank"></a>stopni

Przechowuje rangę `array`.

```cpp
static const int rank = _Rank;
```

## <a name="reinterpret_as"></a>reinterpret_as

Interpretuje tablicę za pomocą jednowymiarowej array_view, która opcjonalnie może mieć inny typ wartości niż tablica źródłowa.

### <a name="syntax"></a>Składnia

```cpp
template <typename _Value_type2>
array_view<_Value_type2,1> reinterpret_as() restrict(amp,cpu);

template <typename _Value_type2>
array_view<const _Value_type2, 1> reinterpret_as() const restrict(amp,cpu);
```

### <a name="parameters"></a>Parametry

*_Value_type2*<br/>
Typ danych zwracanych danych.

### <a name="return-value"></a>Wartość zwrócona

Obiekt array_view lub const array_view, który jest oparty na tablicy, z typem elementu reinterpretowanym z T do ElementType i rangą ograniczoną od N do 1.

### <a name="remarks"></a>Uwagi

Czasami wygodnie jest wyświetlić tablicę wielowymiarową, tak jakby była to liniowa, Jednowymiarowa tablica, prawdopodobnie z innym typem wartości niż tablica źródłowa. Możesz użyć tej metody, aby to osiągnąć.
**Przestroga** Reinterpretacja obiektu Array przy użyciu innego typu wartości jest potencjalnie niebezpieczną operacją. Zalecamy korzystanie z tej funkcji uważnie.

Poniższy kod zawiera przykład.

```cpp
struct RGB { float r; float g; float b; };

array<RGB,3>  a = ...;
array_view<float,1> v = a.reinterpret_as<float>();

assert(v.extent == 3*a.extent);
```

## <a name="section"></a>Paragraf

Zwraca podsekcję obiektu `array`, który znajduje się w podanej lokalizacji i opcjonalnie ma określony zakres.

```cpp
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
Najbardziej znaczący składnik zakresu tej sekcji.

*_E1*<br/>
Najbardziej znaczący składnik zakresu tej sekcji.

*_E2*<br/>
Najmniej znaczący składnik zakresu tej sekcji.

*_Ext*<br/>
Obiekt [zakresu](extent-class.md) , który określa zakres sekcji. Początek jest równy 0.

*_Idx*<br/>
Obiekt [index](index-class.md) , który określa lokalizację pochodzenia. Podsekcja jest resztą zakresu.

*_I0*<br/>
Najbardziej znaczący składnik pochodzenia tej sekcji.

*_I1*<br/>
Najbardziej znaczący składnik pochodzenia tej sekcji.

*_I2*<br/>
Najmniej znaczący składnik pochodzenia tej sekcji.

*_Rank*<br/>
Ranga sekcji.

*_Section_extent*<br/>
Obiekt [zakresu](extent-class.md) , który określa zakres sekcji.

*_Section_origin*<br/>
Obiekt [index](index-class.md) , który określa lokalizację pochodzenia.

*value_type*<br/>
Typ danych elementów, które są kopiowane.

### <a name="return-value"></a>Wartość zwrócona

Zwraca podsekcję obiektu `array`, który znajduje się w podanej lokalizacji i opcjonalnie ma określony zakres. Gdy jest określony tylko `index` obiektu, podsekcja zawiera wszystkie elementy w skojarzonej siatce, które mają indeksy, które są większe niż indeksy elementów w obiekcie `index`.

## <a name="view_as"></a>view_as

Interpretuje tę tablicę jako [array_view](array-view-class.md) innej rangi.

```cpp
template <int _New_rank>
array_view<value_type,_New_rank> view_as(
    const Concurrency::extent<_New_rank>& _View_extent) restrict(amp,cpu);

template <int _New_rank>
array_view<const value_type,_New_rank> view_as(
    const Concurrency::extent<_New_rank>& _View_extent) const restrict(amp,cpu);
```

### <a name="parameters"></a>Parametry

*_New_rank*<br/>
Ranga obiektu `extent` przeniesiona jako parametr.

*_View_extent*<br/>
Zakres, który jest używany do konstruowania nowego obiektu [array_view](array-view-class.md) .

*value_type*<br/>
Typ danych elementów w oryginalnym obiekcie `array` i zwróconym obiekcie `array_view`.

### <a name="return-value"></a>Wartość zwrócona

Obiekt [array_view](array-view-class.md) , który jest skonstruowany.

## <a name="see-also"></a>Zobacz też

[Przestrzeń nazw współbieżności (C++ AMP)](concurrency-namespace-cpp-amp.md)
