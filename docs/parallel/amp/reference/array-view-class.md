---
title: array_view — Klasa
ms.date: 11/04/2016
f1_keywords:
- array_view
- AMP/array_view
- AMP/Concurrency::array_view::array_view
- AMP/Concurrency::array_view::copy_to
- AMP/Concurrency::array_view::data
- AMP/Concurrency::array_view::discard_data
- AMP/Concurrency::array_view::get_extent
- AMP/Concurrency::array_view::get_ref
- AMP/Concurrency::array_view::get_source_accelerator_view
- AMP/Concurrency::array_view::refresh
- AMP/Concurrency::array_view::reinterpret_as
- AMP/Concurrency::array_view::section
- AMP/Concurrency::array_view::synchronize
- AMP/Concurrency::array_view::synchronize_async
- AMP/Concurrency::array_view::synchronize_to
- AMP/Concurrency::array_view::synchronize_to_async
- AMP/Concurrency::array_view::view_as
- AMP/Concurrency::array_view::rank
- AMP/Concurrency::array_view::extent
- AMP/Concurrency::array_view::source_accelerator_view
- AMP/Concurrency::array_view::value_type
helpviewer_keywords:
- array_view class
ms.assetid: 7e7ec9bc-05a2-4372-b05d-752b50006c5a
ms.openlocfilehash: a0d8fa733a5da14e8ee16acf2623df07c9974893
ms.sourcegitcommit: afd6fac7c519dbc47a4befaece14a919d4e0a8a2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/10/2018
ms.locfileid: "51523380"
---
# <a name="arrayview-class"></a>array_view — Klasa

Reprezentuje N-wymiarowy widok danych przechowywanych w innym kontenerze.

## <a name="syntax"></a>Składnia

```
template <
    typename value_type,
    int _Rank = 1
>
class array_view : public _Array_view_base<_Rank, sizeof(value_type)/sizeof(int)>;

template <
    typename value_type,
    int _Rank
>
class array_view<const value_type, _Rank> : public _Array_view_base<_Rank, sizeof(value_type)/sizeof(int)>;
```

#### <a name="parameters"></a>Parametry

*value_type*<br/>
Typ danych elementów w `array_view` obiektu.

*_Rank*<br/>
Ranga `array_view` obiektu.

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[array_view konstruktora](#ctor)|Inicjuje nowe wystąpienie klasy `array_view` klasy. Brak domyślnego konstruktora dla `array<T,N>`. Wszystkie konstruktory są ograniczone do uruchomienia tylko na Procesorze i nie może być wykonywane docelowo na Direct3D.|
|[~ array_view — destruktor](#ctor)|Niszczy `array_view` obiektu.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[copy_to](#copy_to)|Kopiuje zawartość `array_view` obiekt do określonego miejsca docelowego, wywołując `copy(*this, dest)`.|
|[Dane](#data)|Zwraca wskaźnik do danych pierwotnych `array_view`.|
|[discard_data](#discard_data)|Odrzuca bieżące dane temu widokowi.|
|[get_extent](#get_extent)|Zwraca obiekt extent z obiektu array_view.|
|[get_ref](#get_ref)|Zwraca odwołanie do elementu indeksowanego.|
|[get_source_accelerator_view](#get_source_accelerator_view)|Zwraca [accelerator_view](accelerator-view-class.md) gdzie źródło danych `array_view` znajduje się.|
|[refresh](#refresh)|Powiadamia `array_view` obiektu, że jego pamięć związana została zmodyfikowana poza `array_view` interfejsu. Wywołanie tej metody renderuje wszystkie buforowane informacje starych.|
|[reinterpret_as](#reinterpret_as)|Zwraca jednowymiarową tablicę, która zawiera wszystkie elementy w `array_view` obiektu.|
|[sekcja](#section)|Zwraca podsekcję obiektu `array_view` obiektu, który znajduje się w określonej lokalizacji i, opcjonalnie, który ma określony zakres.|
|[synchronize](#synchronize)|Synchronizuje wszelkie modyfikacje wprowadzone do `array_view` obiektu do jego danych źródłowych.|
|[synchronize_async](#synchronize_async)|Synchronizuje asynchronicznie wszelkie modyfikacje wprowadzone do `array_view` obiektu do jego danych źródłowych.|
|[synchronize_to](#synchronize_to)|Synchronizuje wszelkie modyfikacje wprowadzone do `array_view` obiektu do określonego [accelerator_view](accelerator-view-class.md).|
|[synchronize_to_async](#synchronize_to_async)|Synchronizuje asynchronicznie wszelkie modyfikacje wprowadzone do `array_view` obiektu do określonego [accelerator_view](accelerator-view-class.md).|
|[view_as](#view_as)|Tworzy `array_view` obiektu innej randze, za pomocą `array_view` danych obiektu.|

### <a name="public-operators"></a>Operatory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[operator()](#operator_call)|Zwraca wartość elementu, który jest określony przez parametr lub parametry.|
|[operator[]](#operator_at)|Zwraca element, który jest określony przez parametry.|
|[operator=](#operator_eq)|Kopiuje zawartość określonego `array_view` obiektu do wskazanego.|

### <a name="public-constants"></a>Publiczne stałe

|Nazwa|Opis|
|----------|-----------------|
|[Rank — stała](#rank)|Przechowuje rangę `array_view` obiektu.|

### <a name="data-members"></a>Elementy członkowskie danych

|Nazwa|Opis|
|----------|-----------------|
|[extent](#extent)|Pobiera `extent` obiekt, który definiuje kształt `array_view` obiektu.|
|[source_accelerator_view](#source_accelerator_view)|Pobiera [accelerator_view](accelerator-view-class.md) gdzie źródło danych `array_view` znajduje się|
|[value_type](#value_type)|Typ wartości `array_view` i tablicy powiązania.|

## <a name="remarks"></a>Uwagi

`array_view` Klasa reprezentuje widok danych, który jest zawarty w [tablicy](array-class.md) obiektu lub podsekcji obiektu `array` obiektu.

Możesz uzyskać dostęp `array_view` obiekt w przypadku, gdy znajdują się dane źródłowe (lokalnie) lub na innym akceleratorze lub w domenie spójności (zdalnie). Podczas zdalnego dostępu do obiektu widoki są kopiowane i buforowane zgodnie z potrzebami. Z wyjątkiem skutków buforowania automatycznego `array_view` obiekty mają profil wydajności podobny do `array` obiektów. Istnieje mały spadek wydajności, gdy uzyskujesz dostęp do danych za pośrednictwem widoków.

Istnieją trzy scenariusze użycia zdalnego:

- Widok wskaźnika pamięci systemu jest przekazywany przez [parallel_for_each](../../../parallel/concrt/reference/concurrency-namespace-functions.md#parallel_for_each) wywołania do akceleratora i dostęp do akceleratora.

- Widok tablicy znajdujący się na akceleratorze, który jest przekazywany przez `parallel_for_each` wywołania do innego akceleratora i tam jest dostępny.

- Widok tablicy znajdujący się na akceleratorze, który jest dostępny na procesorze CPU.

W jednym z tych scenariuszy, widoki odwołania są kopiowane w czasie wykonywania do lokalizacji zdalnej i jeśli są modyfikowane przez wywołanie `array_view` obiektów, są kopiowane z powrotem do lokalizacji lokalnej. Środowisko wykonawcze może zoptymalizować proces kopiowania zmian z powrotem, może kopiować tylko zmienione elementy lub może kopiować również fragmenty niezmienione. Nakładające się `array_view` obiektów w jednym źródle danych nie ma gwarancji utrzymania integralności referencyjnej w lokalizacji zdalnej.

Należy zsynchronizować każdy dostęp wielowątkowy do tego samego źródła danych.

Środowisko wykonawcze zapewnia następujące gwarancje, dotyczące buforowania danych w `array_view` obiektów:

- Każdy dobrze zsynchronizowany dostęp do `array` obiektu i `array_view` obiekt w porządku program przestrzegają szeregowego się dzieje — przed relacji.

- Każdy dobrze zsynchronizowany dostęp do nakładających się `array_view` obiektów na tym samym akceleratorze, na jednym `array` obiektu jest aliasowany przez `array` obiektu. Wywołują one razem występuje — przed relacji, które przestrzegają kolejność programu. Nie występuje buforowanie. Jeśli `array_view` obiekty są wykonywane na różnych akceleratorach, kolejność dostępu jest niezdefiniowana, tworząc warunki sytuacji wyścigu.

Po utworzeniu `array_view` obiektu za pomocą wskaźnika w pamięci systemu, należy zmienić widok `array_view` tylko przez obiekt `array_view` wskaźnika. Alternatywnie należy wywołać `refresh()` na jednym z `array_view` obiektów, które są dołączone do wskaźnika systemowego, jeśli podstawowa pamięć macierzysta jest zmieniana bezpośrednio, a nie poprzez `array_view` obiektu.

Każda akcja powiadamia `array_view` obiektu, że podstawowa pamięć macierzysta zostało zmienione, i że wszelkie kopie, które znajdują się na akceleratorze, są nieaktualne. Jeśli należy przestrzegać następujących wytycznych, widoki oparte na wskaźnikach są identyczne do tych dostarczonych do widoków tablic danych równoległych.

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

`_Array_view_shape`

`_Array_view_base`

`array_view`

## <a name="requirements"></a>Wymagania

**Nagłówek:** amp.h

**Namespace:** współbieżności

##  <a name="dtor"></a> ~ array_view

Niszczy `array_view` obiektu.

```
~array_view()restrict(amp,cpu);
```

##  <a name="ctor"></a> array_view

Inicjuje nowe wystąpienie klasy `array_view` klasy.

```
array_view(
    array<value_type, _Rank>& _Src)restrict(amp,cpu);

array_view(
    const array_view& _Other)restrict(amp,cpu);

explicit array_view(
    const Concurrency::extent<_Rank>& _Extent) restrict(cpu);

template <
    typename _Container
>
array_view(
    const Concurrency::extent<_Rank>& _Extent,
    _Container& _Src) restrict(cpu);

array_view(
    const Concurrency::extent<_Rank>& _Extent,
    value_type* _Src)restrict(amp,cpu);

explicit array_view(
    int _E0) restrict(cpu);

template <
    typename _Container
>
explicit array_view(
    _Container& _Src,
    typename std::enable_if<details::_Is_container<_Container>::type::value, void **>::type = 0) restrict(cpu);

template <
    typename _Container
>
explicit array_view(
    int _E0,
    _Container& _Src) restrict(cpu);

explicit array_view(
    int _E0,
    int _E1) __CPU_ONLY;

template <
    typename _Container
>
explicit array_view(
    int _E0,
    int _E1,
    _Container& _Src) restrict(cpu);

explicit array_view(
    int _E0,
    int _E1,
    int _E2) __CPU_ONLY;

template <
    typename _Container
>
explicit array_view(
    int _E0,
    int _E1,
    int _E2,
    _Container& _Src);

explicit array_view(
    int _E0,
    _In_ value_type* _Src)restrict(amp,cpu);

template <
    typename _Arr_type,
    int _Size
>
explicit array_view(
    _In_ _Arr_type (& _Src) [_Size]) restrict(amp,cpu);

explicit array_view(
    int _E0,
    int _E1,
    _In_ value_type* _Src)restrict(amp,cpu);

explicit array_view(
    int _E0,
    int _E1,
    int _E2,
    _In_ value_type* _Src)restrict(amp,cpu);

array_view(
    const array<value_type, _Rank>& _Src)restrict(amp,cpu);

array_view(
    const array_view<value_type, _Rank>& _Src)restrict(amp,cpu);

array_view(
    const array_view<const value_type, _Rank>& _Src)restrict(amp,cpu);

template <
    typename _Container
>
array_view(
    const Concurrency::extent<_Rank>& _Extent,
    const _Container& _Src) restrict(cpu);

template <
    typename _Container
>
explicit array_view(
    const _Container& _Src,
    typename std::enable_if<details::_Is_container<_Container>::type::value, void **>::type = 0) restrict(cpu);

array_view(
    const Concurrency::extent<_Rank>& _Extent,
    const value_type* _Src)restrict(amp,cpu);

template <
    typename _Arr_type,
    int _Size
>
explicit array_view(
    const _In_ _Arr_type (& _Src) [_Size]) restrict(amp,cpu);

template <
    typename _Container
>
array_view(
    int _E0,
    const _Container& _Src);

template <
    typename _Container
>
array_view(
    int _E0,
    int _E1,
    const _Container& _Src);

template <
    typename _Container
>
array_view(
    int _E0,
    int _E1,
    int _E2,
    const _Container& _Src);

array_view(
    int _E0,
    const value_type* _Src)restrict(amp,cpu);

array_view(
    int _E0,
    int _E1,
    const value_type* _Src) restrict(amp,cpu);

array_view(
    int _E0,
    int _E1,
    int _E2,
    const value_type* _Src) restrict(amp,cpu);
```

### <a name="parameters"></a>Parametry

*_Arr_type*<br/>
Typ elementu tablicy stylu C, z którego dane są dostarczane.

*_Container*<br/>
Argument szablonu, który musi określać liniowy kontener, który obsługuje `data()` i `size()` elementów członkowskich.

*_E0*<br/>
Najbardziej znaczący składnik z zakresu sekcji.

*_E1*<br/>
Dalej do najbardziej znaczący składnik z zakresu sekcji.

*_E2*<br/>
Najmniej znaczący składnik z zakresu sekcji.

*_Extent*<br/>
Zakres każdego wymiaru `array_view`.

*_Inne*<br/>
Obiekt typu `array_view<T,N>` z którego należy zainicjować nowy `array_view`.

*_Rozmiar*<br/>
Rozmiar tablicy stylu C, z którego dane są dostarczane.

*_Src*<br/>
Wskaźnik do danych źródłowych, które mają zostać skopiowane do nowej tablicy.

##  <a name="copy_to"></a> copy_to —

Kopiuje zawartość `array_view` obiekt do określonego obiektu docelowego przez wywołanie metody `copy(*this, dest)`.

```
void copy_to(
    array<value_type, _Rank>& _Dest) const;

void copy_to(
    array_view<value_type, _Rank>& _Dest) const;
```

### <a name="parameters"></a>Parametry

*_Dest*<br/>
Obiekt, który można skopiować do.

##  <a name="data"></a> Dane

Zwraca wskaźnik do danych pierwotnych `array_view`.

```
value_type* data() const restrict(amp,
    cpu);

const value_type* data() const restrict(amp,
    cpu);
```

### <a name="return-value"></a>Wartość zwracana

Wskaźnik do danych pierwotnych `array_view`.

##  <a name="discard_data"></a> discard_data

Odrzuca bieżące dane temu widokowi. Jest to wskazówka dotycząca optymalizacji dla środowiska uruchomieniowego użytego w celu uniknięcia kopiowania aktualnej zawartości widoku do obiektu docelowego `accelerator_view` jest on dostępny, a jego użycie jest polecane, jeśli istniejąca zawartość nie jest wymagana. Ta metoda jest pusta w kontekście restrict(amp)

```
void discard_data() const restrict(cpu);
```

##  <a name="extent"></a> zakres

Pobiera `extent` obiekt, który definiuje kształt `array_view` obiektu.

```
__declspec(property(get= get_extent)) Concurrency::extent<_Rank> extent;
```

##  <a name="get_extent"></a> get_extent —

Zwraca [zakres](extent-class.md) obiektu `array_view` obiektu.

```
Concurrency::extent<_Rank> get_extent() const restrict(cpu, amp);
```

### <a name="return-value"></a>Wartość zwracana

`extent` Obiektu `array_view` obiektu

##  <a name="get_ref"></a> get_ref

Pobierz odwołanie do elementu indeksowane przez _Index. W odróżnieniu od innych operatorów indeksowania do uzyskiwania dostępu do array_view na CPU metoda ta nie synchronizuje niejawnie zawartość tej array_view do Procesora. Po uzyskiwanie dostępu do array_view w lokalizacji zdalnej lub wykonaniu operacji kopiowania obejmujących ten array_view użytkownicy są odpowiedzialni za jawne zsynchronizowanie array_view z procesorem przed wywołaniem tej metody. Niewykonanie tej czynności powoduje zachowanie niezdefiniowane.

```
value_type& get_ref(
    const index<_Rank>& _Index) const restrict(amp, cpu);
```

### <a name="parameters"></a>Parametry

*Parametr _Index*<br/>
Indeks.

### <a name="return-value"></a>Wartość zwracana

Odwołanie do elementu indeksowane przez _Index

##  <a name="get_source_accelerator_view"></a> get_source_accelerator_view

Zwraca accelerator_view, w którym znajduje się źródło danych array_view. Jeśli array_view nie ma źródła danych, ten interfejs API zgłasza wyjątek czasu wykonywania

```
accelerator_view get_source_accelerator_view() const;
```

### <a name="return-value"></a>Wartość zwracana

##  <a name="operator_call"></a> Operator()

Zwraca wartość elementu, który jest określony przez parametr lub parametry.

```
value_type& operator() (
    const index<_Rank>& _Index) const restrict(amp,cpu);

typename details::_Projection_result_type<value_type,_Rank>::_Result_type operator() (
    int _I) const restrict(amp,cpu);

value_type& operator() (
    int _I0,
    int _I1) const restrict(amp,cpu);

value_type& operator() (
    int _I0,
    int _I1,
    int _I2) const restrict(amp,cpu);

typename details::_Projection_result_type<value_type,_Rank>::_Const_result_type operator() (
    int _I) const restrict(amp,cpu);
```

### <a name="parameters"></a>Parametry

*Parametr _Index*<br/>
Lokalizacja elementu.

*_I0*<br/>
Indeks pierwszego wymiaru.

*_I1*<br/>
Indeks w drugim wymiarze.

*_I2*<br/>
Indeks w trzecim wymiarze.

*_I*<br/>
Lokalizacja elementu.

### <a name="return-value"></a>Wartość zwracana

Wartość elementu, który jest określony przez parametr lub parametry.

##  <a name="operator_at"></a> Operator]

Zwraca element, który jest określony przez parametry.

```
typename details::_Projection_result_type<value_type,_Rank>::_Const_result_type operator[] (
    int _I) const restrict(amp,cpu);

value_type& operator[] (
    const index<_Rank>& _Index) const restrict(amp,cpu);
```

### <a name="parameters"></a>Parametry

*Parametr _Index*<br/>
Indeks.

*_I*<br/>
Indeks.

### <a name="return-value"></a>Wartość zwracana

Wartość elementu wskazywanego przez indeks, lub `array_view` przewidywana na najbardziej znaczący wymiar.

##  <a name="operator_eq"></a> operator =

Kopiuje zawartość określonego `array_view` obiektu do wskazanego.

```
array_view& operator= (
    const array_view& _Other) restrict(amp,cpu);

array_view& operator= (
    const array_view<value_type, _Rank>& _Other) restrict(amp,cpu);
```

### <a name="parameters"></a>Parametry

*_Inne*<br/>
`array_view` Obiektu do skopiowania.

### <a name="return-value"></a>Wartość zwracana

Odwołanie do `array_view` obiektu.

##  <a name="rank"></a> Ranga

Przechowuje rangę `array_view` obiektu.

```
static const int rank = _Rank;
```

##  <a name="refresh"></a> Odśwież

Powiadamia `array_view` obiektu, że jego pamięć związana została zmodyfikowana poza `array_view` interfejsu. Wywołanie tej metody renderuje wszystkie buforowane informacje starych.

```
void refresh() const restrict(cpu);
```

## <a name="reinterpret_as"></a> reinterpret_as —

Reinterpretuje obiekt array_view za pośrednictwem jednowymiarowego obiektu array_view, który opcjonalnie może mieć inny typ wartości niż źródłowy obiekt array_view.

### <a name="syntax"></a>Składnia

```
template <
    typename _Value_type2
>
array_view< _Value_type2, _Rank> reinterpret_as() const restrict(amp,cpu);

template <
    typename _Value_type2
>
array_view<const _Value_type2, _Rank> reinterpret_as() const restrict(amp,cpu);
```

### <a name="parameters"></a>Parametry

*_Value_type2*<br/>
Typ danych nowego `array_view` obiektu.

### <a name="return-value"></a>Wartość zwracana

`array_view` Lub stała `array_view` obiekt, który jest oparty na tym `array_view`, o typie elementu skonwertowanego z `T` do `_Value_type2`, i randze zmniejszonej z *N* 1.

### <a name="remarks"></a>Uwagi

Czasami wygodne jest wyświetlanie tablicy wielowymiarowej jako liniowego, jednowymiarową tablicę, która może mieć inny typ wartości niż tablica źródłowa. Można to osiągnąć na `array_view` za pomocą tej metody.

**Ostrzeżenie** Reinterpretacja obiektu array_view przy użyciu innego typu wartości jest operacją potencjalnie niebezpieczną. Ta funkcja powinna być stosowana z rozwagą.

Oto przykład:

```cpp
struct RGB { float r; float g; float b; };

array<RGB,3>  a = ...;
array_view<float,1> v = a.reinterpret_as<float>();

assert(v.extent == 3*a.extent);
```

##  <a name="section"></a> Sekcja

Zwraca podsekcję obiektu `array_view` obiektu, który znajduje się w określonej lokalizacji i, opcjonalnie, który ma określony zakres.

```
array_view section(
    const Concurrency::index<_Rank>& _Section_origin,
    const Concurrency::extent<_Rank>& _Section_extent) const restrict(amp,cpu);

array_view section(
    const Concurrency::index<_Rank>& _Idx) const restrict(amp,cpu);

array_view section(
    const Concurrency::extent<_Rank>& _Ext) const restrict(amp,cpu);

array_view section(
    int _I0,
    int _E0) const restrict(amp,cpu);

array_view section(
    int _I0,
    int _I1,
    int _E0,
    int _E1) const restrict(amp,cpu);

array_view section(
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

### <a name="return-value"></a>Wartość zwracana

Podsekcja `array_view` obiektu, który znajduje się w określonej lokalizacji i, opcjonalnie, który ma określony zakres. Gdy tylko `index` obiektu jest określony, podsekcja zawiera wszystkie elementy w skojarzonym zakresie, które mają indeksy są większe niż indeksy elementów w `index` obiektu.

##  <a name="source_accelerator_view"></a> source_accelerator_view

Pobiera źródłowy obiekt accelerator_view, który jest skojarzony ten obiekt array_view.

```
__declspec(property(get= get_source_accelerator_view)) accelerator_view source_accelerator_view;
```

##  <a name="synchronize"></a> Synchronizuj

Synchronizuje wszelkie modyfikacje wprowadzone do `array_view` obiektu do jego danych źródłowych.

```
void synchronize(access_type _Access_type = access_type_read) const restrict(cpu);

void synchronize() const restrict(cpu);
```

### <a name="parameters"></a>Parametry

*_Access_type*<br/>
Żądane [access_type](concurrency-namespace-enums-amp.md#access_type) w elemencie docelowym [accelerator_view](accelerator-view-class.md). Ten parametr ma wartość domyślną `access_type_read`.

##  <a name="synchronize_async"></a> synchronize_async

Synchronizuje asynchronicznie wszelkie modyfikacje wprowadzone do `array_view` obiektu do jego danych źródłowych.

```
concurrency::completion_future synchronize_async(access_type _Access_type = access_type_read) const restrict(cpu);

concurrency::completion_future synchronize_async() const restrict(cpu);
```

### <a name="parameters"></a>Parametry

*_Access_type*<br/>
Żądane [access_type](concurrency-namespace-enums-amp.md#access_type) w elemencie docelowym [accelerator_view](accelerator-view-class.md). Ten parametr ma wartość domyślną `access_type_read`.

### <a name="return-value"></a>Wartość zwracana

Przyszłe oczekiwanie na zakończenie operacji.

##  <a name="synchronize_to"></a> synchronize_to

Synchronizuje wszelkie modyfikacje wprowadzone do array_view na określony accelerator_view.

```
void synchronize_to(
    const accelerator_view& _Accl_view,
    access_type _Access_type = access_type_read) const restrict(cpu);

void synchronize_to(
    const accelerator_view& _Accl_view) const restrict(cpu);
```

### <a name="parameters"></a>Parametry

*_Accl_view*<br/>
Accelerator_view do zsynchronizowania się.

*_Access_type*<br/>
Żądany access_type na docelowym accelerator_view. Ten parametr ma wartość domyślna to access_type_read.

##  <a name="synchronize_to_async"></a> synchronize_to_async

Synchronizuje asynchronicznie wszelkie modyfikacje wprowadzone do array_view na określony accelerator_view.

```
concurrency::completion_future synchronize_to_async(
    const accelerator_view& _Accl_view,
    access_type _Access_type = access_type_read) const restrict(cpu);

concurrency::completion_future synchronize_to_async(
    const accelerator_view& _Accl_view) const restrict(cpu);
```

### <a name="parameters"></a>Parametry

*_Accl_view*<br/>
Accelerator_view do zsynchronizowania się.

*_Access_type*<br/>
Żądany access_type na docelowym accelerator_view. Ten parametr ma wartość domyślna to access_type_read.

### <a name="return-value"></a>Wartość zwracana

Przyszłe oczekiwanie na zakończenie operacji.

##  <a name="value_type"></a> value_type

Typ wartości array_view i tablicy powiązania.

```
typedef typenamevalue_type value_type;
```

##  <a name="view_as"></a> view_as —

Reinterpretuje ten obiekt `array_view` jako `array_view` innej rangi.

```
template <
    int _New_rank
>
array_view<value_type,_New_rank> view_as(
    const Concurrency::extent<_New_rank>& _View_extent) const restrict(amp,cpu);

template <
    int _New_rank
>
array_view<const value_type,_New_rank> view_as(
    const Concurrency::extent<_New_rank> _View_extent) const restrict(amp,cpu);
```

### <a name="parameters"></a>Parametry

*_New_rank*<br/>
Ranga nowego `array_view` obiektu.

*_View_extent*<br/>
Przekształcanie `extent`.

*value_type*<br/>
Typ danych elementów w pierwotnym [tablicy](array-class.md) obiektu i zwracanym `array_view` obiektu.

### <a name="return-value"></a>Wartość zwracana

`array_view` Obiektu, który jest konstruowany.

## <a name="see-also"></a>Zobacz też

[Przestrzeń nazw współbieżności (C++ AMP)](concurrency-namespace-cpp-amp.md)
