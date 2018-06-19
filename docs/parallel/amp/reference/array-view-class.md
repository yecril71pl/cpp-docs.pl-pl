---
title: array_view — klasa | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-amp
ms.topic: reference
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
dev_langs:
- C++
helpviewer_keywords:
- array_view class
ms.assetid: 7e7ec9bc-05a2-4372-b05d-752b50006c5a
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 2e53b4927b102fc64a32f73ca5be78e71954b45f
ms.sourcegitcommit: 7019081488f68abdd5b2935a3b36e2a5e8c571f8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/07/2018
ms.locfileid: "33694423"
---
# <a name="arrayview-class"></a>array_view — Klasa
Reprezentuje N-wielowymiarowy widok przez dane przechowywane w innym kontenerze.  
  
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
 `value_type`  
 Typ danych elementów w `array_view` obiektu.  
  
 `_Rank`  
 Rangę `array_view` obiektu.  
  
## <a name="members"></a>Elementy członkowskie  
  
### <a name="public-constructors"></a>Konstruktory publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[array_view — Konstruktor](#ctor)|Inicjuje nowe wystąpienie klasy `array_view` klasy. Nie istnieje ma domyślnego konstruktora dla `array<T,N>`. Wszystkie konstruktory są ograniczone do uruchamiania tylko procesora i nie można wykonać w celu Direct3D.|  
|[~ array_view — destruktor](#ctor)|Niszczy `array_view` obiektu.|  
  
### <a name="public-methods"></a>Metody publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[copy_to](#copy_to)|Kopiuje zawartość `array_view` obiektu do określonej lokalizacji docelowej, wywołując `copy(*this, dest)`.|  
|[Dane](#data)|Zwraca wskaźnik do dane pierwotne `array_view`.|  
|[discard_data](#discard_data)|Spowoduje odrzucenie bieżącej danych podstawowych tego widoku.|  
|[get_extent](#get_extent)|Zwraca obiekt Zakres obiektu array_view —.|  
|[get_ref](#get_ref)|Zwraca odwołanie do elementu indeksowanego.|  
|[get_source_accelerator_view](#get_source_accelerator_view)|Zwraca [accelerator_view](accelerator-view-class.md) gdy źródło danych `array_view` znajduje się.|  
|[refresh](#refresh)|Powiadamia `array_view` obiekt, który powiązanej pamięci został zmodyfikowany poza `array_view` interfejsu. Wywołanie tej metody renderuje starych wszystkich buforowanych informacji.|  
|[reinterpret_as](#reinterpret_as)|Zwraca Jednowymiarowa tablica, która zawiera wszystkie elementy w `array_view` obiektu.|  
|[sekcja](#section)|Zwraca podsekcją `array_view` obiektu, który znajduje się w określonym pochodzenia i, opcjonalnie, który ma określony zakres.|  
|[synchronize](#synchronize)|Synchronizuje wszystkie modyfikacje `array_view` obiektu do jej dane źródłowe.|  
|[synchronize_async](#synchronize_async)|Asynchronicznie synchronizuje wszelkie modyfikacje `array_view` obiektu do jej dane źródłowe.|  
|[synchronize_to](#synchronize_to)|Synchronizuje wszystkie modyfikacje `array_view` obiektu do określonego [accelerator_view](accelerator-view-class.md).|  
|[synchronize_to_async](#synchronize_to_async)|Asynchronicznie synchronizuje wszelkie modyfikacje `array_view` obiektu do określonego [accelerator_view](accelerator-view-class.md).|  
|[view_as](#view_as)|Tworzy `array_view` obiektu różnych pozycji za pomocą tej `array_view` danych obiektu.|  
  
### <a name="public-operators"></a>Operatory publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[operator()](#operator_call)|Zwraca wartość elementu określonego przez parametr lub parametrów.|  
|[Operator]](#operator_at)|Zwraca element, który jest określona przez parametry.|  
|[operator=](#operator_eq)|Kopiuje zawartość określonego `array_view` obiektu do tego.|  
  
### <a name="public-constants"></a>Publiczny — stałe  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[Rank — stała](#rank)|Przechowuje rangę `array_view` obiektu.|  
  
### <a name="data-members"></a>Elementy członkowskie danych  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[extent](#extent)|Pobiera `extent` obiektu, który definiuje kształt `array_view` obiektu.|  
|[source_accelerator_view](#source_accelerator_view)|Pobiera [accelerator_view](accelerator-view-class.md) gdy źródło danych `array_view` znajduje się|  
|[value_type](#value_type)|Typ wartości `array_view` i powiązane tablicy.|  
  
## <a name="remarks"></a>Uwagi  
 `array_view` Klasa reprezentuje zapewnia wgląd w dane zawarte w [tablicy](array-class.md) obiektu lub podsekcją `array` obiektu.  
  
 Dostęp można uzyskać `array_view` obiekt w przypadku, gdy źródło danych znajduje się (lokalnie) lub w innej akceleratora lub w domenie spójności (zdalnego). Podczas zdalnego dostępu do obiektu widoki są kopiowane i w razie potrzeby w pamięci podręcznej. Z wyjątkiem efekty buforowania automatycznego `array_view` obiekty mają podobny do profilu wydajności `array` obiektów. Gdy uzyskujesz dostęp do danych za pośrednictwem widoków jest zmniejszenie wydajności małych.  
  
 Istnieją trzy scenariusze użycia zdalnego:  
  
-   Widok na wskaźnik pamięci systemu jest przekazywany za pomocą klasy [parallel_for_each](../../../parallel/concrt/reference/concurrency-namespace-functions.md#parallel_for_each) wywołanie akceleratora i uzyskać dostęp do na akceleratora.  
  
-   Widok do tablicy znajdującego się na akceleratora jest przekazywany za pomocą klasy `parallel_for_each` wywołanie innego akceleratora i dostępne.  
  
-   Widok do tablicy znajdującego się na akceleratora jest dostępny na Procesor.  
  
 W jednym z tych scenariuszy, widoki, do którego istnieje odwołanie są kopiowane przez środowisko uruchomieniowe do zdalnej lokalizacji i w przypadku modyfikacji wywołań `array_view` obiektów, są kopiowane do lokalizacji lokalnej. Środowisko uruchomieniowe może zoptymalizować proces kopiowania zmian z powrotem, może kopiować tylko zmienione elementy lub może również skopiować fragmenty bez zmian. Nakładające się `array_view` obiektów na jedno źródło danych nie ma gwarancji utrzymanie integralności referencyjnej w lokalizacji zdalnej.  
  
 Należy przeprowadzić synchronizację wielowątkowych dostęp do tego samego źródła danych.  
  
 Środowisko uruchomieniowe sprawia, że następujące gwarancje buforowania danych w `array_view` obiektów:  
  
-   Wszystkich dobrze zsynchronizowanych operacji uzyskania dostępu do `array` obiektu i `array_view` obiektu na nim w kolejności program przestrzegać szeregowego sytuacji — przed relacji.  
  
-   Wszystkie dobrze zsynchronizowanych operacji uzyskania dostępu do nakładających się `array_view` obiektów w tej samej akceleratora w ramach jednej `array` obiektu są używane z aliasem za pośrednictwem `array` obiektu. One wywołać łącznie występuje — przed relacji, które przestrzega kolejności program. Nie ma żadnych buforowania. Jeśli `array_view` obiekty są wykonywane na różnych akceleratorów, kolejność dostępu jest niezdefiniowana, tworzenie wyścigu.  
  
 Po utworzeniu `array_view` przy użyciu wskaźnika w pamięci, należy zmienić widok `array_view` tylko za pomocą obiektu `array_view` wskaźnika. Alternatywnie, należy wywołać `refresh()` na jednym z `array_view` obiektów, które są dołączone do wskaźnika systemu, zmiana podstawowej natywnej pamięci bezpośrednio, zamiast za pomocą `array_view` obiektu.  
  
 Każda z tych operacji powiadamia `array_view` obiekt zmiana podstawowej natywnej pamięci oraz czy wszystkie kopie, które znajdują się na akceleratora są nieaktualne. Jeśli przestrzegać następujących wytycznych widoków opartych na wskaźnik są identyczne z udostępnianych z widokami danych równoległe tablic.  
  
## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia  
 `_Array_view_shape`  
  
 `_Array_view_base`  
  
 `array_view`  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** amp.h  
  
 **Namespace:** współbieżności  
  
##  <a name="dtor"></a> ~ array_view — 

 Niszczy `array_view` obiektu.  
  
```  
~array_view()restrict(amp,cpu);
```  
  
##  <a name="ctor"></a> array_view — 

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
 `_Arr_type`  
 Typ elementu tablicy stylu języka C, z którego dane są dostarczane.  
  
 `_Container`  
 Argument szablonu, który należy określić kontener liniowy, który obsługuje `data()` i `size()` elementów członkowskich.  
  
 `_E0`  
 Najbardziej znaczący składnik zakres w tej sekcji.  
  
 `_E1`  
 Składnik dalej do większość — znaczące zakresu w tej sekcji.  
  
 `_E2`  
 Najmniej znaczący składnik zakres w tej sekcji.  
  
 `_Extent`  
 Zakres w każdego wymiaru `array_view`.  
  
 `_Other`  
 Obiekt typu `array_view<T,N>` z którego można zainicjować nowe `array_view`.  
  
 `_Size`  
 Rozmiar tablicy stylu języka C, z którego dane są dostarczane.  
  
 `_Src`  
 Wskaźnik do danych źródłowych, które zostaną skopiowane do nowego Tablicy.  
  
##  <a name="copy_to"></a> copy_to 

 Kopiuje zawartość `array_view` obiektu do obiektu docelowego określonego przez wywołanie metody `copy(*this, dest)`.  
  
```  
void copy_to(
    array<value_type, _Rank>& _Dest) const;

 
 
void copy_to(
    array_view<value_type, _Rank>& _Dest) const;

 
```  
  
### <a name="parameters"></a>Parametry  
 `_Dest`  
 Obiekt przeznaczony do skopiowania do.  
  
##  <a name="data"></a> Dane 

 Zwraca wskaźnik do dane pierwotne `array_view`.  
  
```  
value_type* data() const restrict(amp,
    cpu);

 
const value_type* data() const restrict(amp,
    cpu);
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Wskaźnik do dane pierwotne `array_view`.  
  
##  <a name="discard_data"></a> discard_data 

 Spowoduje odrzucenie bieżącej danych podstawowych tego widoku. Jest to wskazówki optymalizacji do środowiska wykonawczego pozwala unikać kopiowania zawartość bieżącego widoku do obiektu docelowego `accelerator_view` , który jest dostępny na, wykorzystanie przez niego jest zalecane, jeśli istniejąca zawartość nie jest wymagana. Ta metoda jest pusta w przypadku używania w kontekście restrict(amp)  
  
```  
void discard_data() const restrict(cpu);
```  
  
##  <a name="extent"></a> zakres 

 Pobiera `extent` obiektu, który definiuje kształt `array_view` obiektu.  
  
```  
__declspec(property(get= get_extent)) Concurrency::extent<_Rank> extent;  
```  
  
##  <a name="get_extent"></a> get_extent 

 Zwraca [zakres](extent-class.md) obiektu `array_view` obiektu.  
  
```  
Concurrency::extent<_Rank> get_extent() const restrict(cpu, amp);
```  
  
### <a name="return-value"></a>Wartość zwracana  
 `extent` Obiektu `array_view` obiektu  
  
##  <a name="get_ref"></a> get_ref 

 Pobierz odwołanie do elementu indeksowane według _Index. W przeciwieństwie do innych indeksowania operatorów do uzyskiwania dostępu do array_view — procesora ta metoda nie niejawnie synchronizować zawartość tego array_view — procesora. Po dostęp do array_view — w lokalizacji zdalnej lub operacji kopiowania, obejmujące tego array_view — użytkownicy są odpowiedzialne jawnie synchronizacji array_view — procesora przed wywołaniem tej metody. Błąd w tym celu powoduje niezdefiniowane zachowanie.  
  
```  
value_type& get_ref(
    const index<_Rank>& _Index) const restrict(amp, cpu);
```  
  
### <a name="parameters"></a>Parametry  
 `_Index`  
 Indeks.  
  
### <a name="return-value"></a>Wartość zwracana  
 Odwołanie do elementu indeksowane według _Index  
  
##  <a name="get_source_accelerator_view"></a> get_source_accelerator_view 

 Zwraca accelerator_view, w którym znajduje się źródło danych array_view —. Jeśli array_view — nie ma źródła danych, ten interfejs API zgłasza runtime_exception —  
  
```  
accelerator_view get_source_accelerator_view() const;

 
```  
  
### <a name="return-value"></a>Wartość zwracana  
  
##  <a name="operator_call"></a> Operator() 

 Zwraca wartość elementu określonego przez parametr lub parametrów.  
  
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
 `_Index`  
 Lokalizacja elementu.  
  
 `_I0`  
 Indeks w pierwszym wymiarze.  
  
 `_I1`  
 Indeks w drugim wymiarze.  
  
 `_I2`  
 Indeks w wymiarze innych.  
  
 `_I`  
 Lokalizacja elementu.  
  
### <a name="return-value"></a>Wartość zwracana  
 Wartość elementu, który jest określony przez parametr lub parametrów.  
  
##  <a name="operator_at"></a> Operator] 

 Zwraca element, który jest określona przez parametry.  
  
```  
typename details::_Projection_result_type<value_type,_Rank>::_Const_result_type operator[] (
    int _I) const restrict(amp,cpu);

 
value_type& operator[] (
    const index<_Rank>& _Index) const restrict(amp,cpu);
```  
  
### <a name="parameters"></a>Parametry  
 `_Index`  
 Indeks.  
  
 `_I`  
 Indeks.  
  
### <a name="return-value"></a>Wartość zwracana  
 Wartość elementu o indeksie, lub `array_view` rzutowana na najbardziej znaczących wymiaru.  
  
##  <a name="operator_eq"></a> operator = 

 Kopiuje zawartość określonego `array_view` obiektu do tego.  
  
```  
array_view& operator= (
    const array_view& _Other) restrict(amp,cpu);

 
array_view& operator= (
    const array_view<value_type, _Rank>& _Other) restrict(amp,cpu);
```  
  
### <a name="parameters"></a>Parametry  
 `_Other`  
 `array_view` Obiektu do skopiowania.  
  
### <a name="return-value"></a>Wartość zwracana  
 Odwołanie do tego `array_view` obiektu.  
  
##  <a name="rank"></a> Ranga 

 Przechowuje rangę `array_view` obiektu.  
  
```  
static const int rank = _Rank;  
```  
  
##  <a name="refresh"></a> Odśwież 

 Powiadamia `array_view` obiekt, który powiązanej pamięci został zmodyfikowany poza `array_view` interfejsu. Wywołanie tej metody renderuje starych wszystkich buforowanych informacji.  
  
```  
void refresh() const restrict(cpu);
```  
## <a name="reinterpret_as"></a> reinterpret_as 

Reinterprets array_view — za pośrednictwem jednowymiarowa array_view —, która opcja może mieć typu wartości innego niż array_view — źródło.  
  
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
 `_Value_type2`  
 Typ danych nowego `array_view` obiektu.  
  
### <a name="return-value"></a>Wartość zwracana  
 `array_view` Obiektu lub typu const `array_view` obiekt, który jest oparty na tym `array_view`, z typem elementu skonwertowane z `T` do `_Value_type2`, i pozycję zmniejszony z *N* do 1.  
  
### <a name="remarks"></a>Uwagi  
 Czasami jest wygodne wyświetlić tablicy wielowymiarowej jako liniowych, Jednowymiarowa tablica, który może mieć typu wartość inną niż źródłowa tablica. Można to osiągnąć w `array_view` za pomocą tej metody.  
  
**Ostrzeżenie** Reinterpeting obiektu array_view — za pomocą innej wartości typu jest potencjalnie niebezpieczna operacja. Tej funkcji należy używać ostrożnie.  
  
 Oto przykład:  
  
```cpp  
struct RGB { float r; float g; float b; };  
  
array<RGB,3>  a = ...;   
array_view<float,1> v = a.reinterpret_as<float>();   
  
assert(v.extent == 3*a.extent);  
```  
    
##  <a name="section"></a> Sekcja 

 Zwraca podsekcją `array_view` obiektu, który znajduje się w określonym pochodzenia i, opcjonalnie, który ma określony zakres.  
  
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
  
### <a name="return-value"></a>Wartość zwracana  
 Podsekcją `array_view` obiektu, który znajduje się w określonym pochodzenia i, opcjonalnie, który ma określony zakres. Gdy tylko `index` obiektu jest określony, podsekcji zawiera wszystkie elementy w zakresie skojarzony, które mają indeksy, które są większe niż indeksów elementów w `index` obiektu.  
  
##  <a name="source_accelerator_view"></a> source_accelerator_view 

 Pobiera accelerator_view źródła, skojarzonego z tym array_view —.  
  
```  
__declspec(property(get= get_source_accelerator_view)) accelerator_view source_accelerator_view;  
```  
  
##  <a name="synchronize"></a> Synchronizuj 

 Synchronizuje wszystkie modyfikacje `array_view` obiektu do jej dane źródłowe.  
  
```  
void synchronize(access_type _Access_type = access_type_read) const restrict(cpu);

 
void synchronize() const restrict(cpu);
```  
  
### <a name="parameters"></a>Parametry  
 `_Access_type`  
 Żądane [access_type](concurrency-namespace-enums-amp.md#access_type) w celu [accelerator_view](accelerator-view-class.md). Ten parametr ma wartość domyślną `access_type_read`.  
  
##  <a name="synchronize_async"></a> synchronize_async 

 Asynchronicznie synchronizuje wszelkie modyfikacje `array_view` obiektu do jej dane źródłowe.  
  
```  
concurrency::completion_future synchronize_async(access_type _Access_type = access_type_read) const restrict(cpu);

 
concurrency::completion_future synchronize_async() const restrict(cpu);
```  
  
### <a name="parameters"></a>Parametry  
 `_Access_type`  
 Żądane [access_type](concurrency-namespace-enums-amp.md#access_type) w celu [accelerator_view](accelerator-view-class.md). Ten parametr ma wartość domyślną `access_type_read`.  
  
### <a name="return-value"></a>Wartość zwracana  
 Przyszłe umożliwiającego Zaczekaj na ukończenie tej operacji.  
  
##  <a name="synchronize_to"></a> synchronize_to 

 Synchronizuje wszelkie modyfikacje tego array_view — do określonego accelerator_view.  
  
```  
void synchronize_to(
    const accelerator_view& _Accl_view,  
    access_type _Access_type = access_type_read) const restrict(cpu);

 
void synchronize_to(
    const accelerator_view& _Accl_view) const restrict(cpu);
```  
  
### <a name="parameters"></a>Parametry  
 `_Accl_view`  
 Accelerator_view docelowych, które mają być synchronizowane.  
  
 `_Access_type`  
 Żądany access_type na accelerator_view docelowej. Ten parametr ma wartość domyślną access_type_read.  
  
##  <a name="synchronize_to_async"></a> synchronize_to_async 

 Asynchronicznie synchronizuje wszelkie modyfikacje tego array_view — do określonego accelerator_view.  
  
```  
concurrency::completion_future synchronize_to_async(
    const accelerator_view& _Accl_view,  
    access_type _Access_type = access_type_read) const restrict(cpu);

 
concurrency::completion_future synchronize_to_async(
    const accelerator_view& _Accl_view) const restrict(cpu);
```  
  
### <a name="parameters"></a>Parametry  
 `_Accl_view`  
 Accelerator_view docelowych, które mają być synchronizowane.  
  
 `_Access_type`  
 Żądany access_type na accelerator_view docelowej. Ten parametr ma wartość domyślną access_type_read.  
  
### <a name="return-value"></a>Wartość zwracana  
 Przyszłe umożliwiającego Zaczekaj na ukończenie tej operacji.  
  
##  <a name="value_type"></a> value_type 

 Typ wartości array_view — i powiązane tablicy.  
  
```  
typedef typenamevalue_type value_type;  
```  
  
##  <a name="view_as"></a> view_as 

 To reinterprets `array_view` jako `array_view` różnych rangi.  
  
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
 `_New_rank`  
 Ranga nowej `array_view` obiektu.  
  
 `_View_extent`  
 Przekształcanie `extent`.  
  
 `value_type`  
 Typ danych elementów w oryginalnym zarówno [tablicy](array-class.md) obiekt i zwrócona `array_view` obiektu.  
  
### <a name="return-value"></a>Wartość zwracana  
 `array_view` Obiektu, który jest tworzony.  
  
## <a name="see-also"></a>Zobacz też  
 [Przestrzeń nazw współbieżności (C++ AMP)](concurrency-namespace-cpp-amp.md)
