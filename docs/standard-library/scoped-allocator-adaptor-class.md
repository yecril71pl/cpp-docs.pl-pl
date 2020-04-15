---
title: scoped_allocator_adaptor — klasa
ms.date: 11/04/2016
f1_keywords:
- scoped_allocator/std::scoped_allocator_adaptor
- scoped_allocator/std::scoped_allocator_adaptor::rebind Struct
- scoped_allocator/std::scoped_allocator_adaptor::allocate
- scoped_allocator/std::scoped_allocator_adaptor::construct
- scoped_allocator/std::scoped_allocator_adaptor::deallocate
- scoped_allocator/std::scoped_allocator_adaptor::destroy
- scoped_allocator/std::scoped_allocator_adaptor::inner_allocator
- scoped_allocator/std::scoped_allocator_adaptor::max_size
- scoped_allocator/std::scoped_allocator_adaptor::outer_allocator
- scoped_allocator/std::scoped_allocator_adaptor::select_on_container_copy_construction
helpviewer_keywords:
- std::scoped_allocator_adaptor
- std::scoped_allocator_adaptor::allocate
- std::scoped_allocator_adaptor::construct
- std::scoped_allocator_adaptor::deallocate
- std::scoped_allocator_adaptor::destroy
- std::scoped_allocator_adaptor::inner_allocator
- std::scoped_allocator_adaptor::max_size
- std::scoped_allocator_adaptor::outer_allocator
- std::scoped_allocator_adaptor::select_on_container_copy_construction
ms.assetid: 0d9b06a1-9a4a-4669-9470-8805cae48e89
ms.openlocfilehash: b08cf1858cb0f9bf4dc6201edc2502d48754ff77
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81373398"
---
# <a name="scoped_allocator_adaptor-class"></a>scoped_allocator_adaptor — klasa

Reprezentuje gniazdo alokatorów.

## <a name="syntax"></a>Składnia

```cpp
template <class Outer, class... Inner>
class scoped_allocator_adaptor;
```

## <a name="remarks"></a>Uwagi

Szablon klasy hermetyzuje gniazdo jednego lub więcej alokatorów. Każda taka klasa ma najbardziej zewnętrzny `outer_allocator_type`alokator `Outer`typu , synonim dla `scoped_allocator_adaptor` , który jest publiczną bazą obiektu. `Outer`służy do przydzielania pamięci do użycia przez kontener. Odwołanie do tego obiektu bazowego alokatora można uzyskać, wywołując program `outer_allocator`.

Pozostała część gniazda ma `inner_allocator_type`typ . Wewnętrzny alokator jest używany do przydzielania pamięci dla elementów w kontenerze. Odwołanie do przechowywanego obiektu tego typu można `inner_allocator`uzyskać, wywołując program . Jeśli `Inner...` nie jest `inner_allocator_type` pusty, ma typ `scoped_allocator_adaptor<Inner...>`i `inner_allocator` wyznacza obiekt elementu członkowskiego. W `inner_allocator_type` przeciwnym `scoped_allocator_adaptor<Outer>`razie `inner_allocator` ma typ i wyznacza cały obiekt.

Gniazdo zachowuje się tak, jakby miało dowolną głębokość, replikując w razie potrzeby swój najbardziej zhermetyzowany alokator.

Kilka pojęć, które nie są częścią pomocy interfejsu widoczne w opisie zachowania tego szablonu klasy. *Najbardziej zewnętrzny alokator* pośredniczy wszystkie wywołania metody konstruowania i niszczenia. Jest skutecznie definiowany przez funkcję `OUTERMOST(X)`cykliczną, gdzie `OUTERMOST(X)` jest jedną z następujących czynności.

- Jeśli `X.outer_allocator()` jest dobrze `OUTERMOST(X)` uformowany, to jest `OUTERMOST(X.outer_allocator())`.

- W `OUTERMOST(X)` przeciwnym `X`razie jest .

Dla celów ekspozycji zdefiniowano trzy typy:

|Typ|Opis|
|----------|-----------------|
|`Outermost`|Typ . `OUTERMOST(*this)`|
|`Outermost_traits`|`allocator_traits<Outermost>`|
|`Outer_traits`|`allocator_traits<Outer>`|

### <a name="constructors"></a>Konstruktorów

|Nazwa|Opis|
|----------|-----------------|
|[scoped_allocator_adaptor](#scoped_allocator_adaptor)|Konstruuje `scoped_allocator_adaptor` obiekt.|

### <a name="typedefs"></a>Typedefs

|Nazwa|Opis|
|----------|-----------------|
|`const_pointer`|Ten typ jest synonimem, `const_pointer` który jest skojarzony `Outer`z alokatora .|
|`const_void_pointer`|Ten typ jest synonimem, `const_void_pointer` który jest skojarzony `Outer`z alokatora .|
|`difference_type`|Ten typ jest synonimem, `difference_type` który jest skojarzony `Outer`z alokatora .|
|`inner_allocator_type`|Ten typ jest synonimem typu adaptera zagnieżdżonego `scoped_allocator_adaptor<Inner...>`.|
|`outer_allocator_type`|Ten typ jest synonimem typu alokatora `Outer`podstawowego .|
|`pointer`|Ten typ jest synonimem `pointer` skojarzonego z alokatorem `Outer`.|
|`propagate_on_container_copy_assignment`|Typ ma wartość `Outer_traits::propagate_on_container_copy_assignment` true tylko `inner_allocator_type::propagate_on_container_copy_assignment` wtedy, gdy posiada true lub posiada true.|
|`propagate_on_container_move_assignment`|Typ ma wartość `Outer_traits::propagate_on_container_move_assignment` true tylko `inner_allocator_type::propagate_on_container_move_assignment` wtedy, gdy posiada true lub posiada true.|
|`propagate_on_container_swap`|Typ ma wartość `Outer_traits::propagate_on_container_swap` true tylko `inner_allocator_type::propagate_on_container_swap` wtedy, gdy posiada true lub posiada true.|
|`size_type`|Ten typ jest synonimem `size_type` skojarzonego z alokatorem `Outer`.|
|`value_type`|Ten typ jest synonimem `value_type` skojarzonego z alokatorem `Outer`.|
|`void_pointer`|Ten typ jest synonimem `void_pointer` skojarzonego z alokatorem `Outer`.|

### <a name="structs"></a>Struktury

|Nazwa|Opis|
|----------|-----------------|
|[scoped_allocator_adaptor::ponowna struktura](#rebind_struct)|Definiuje typ `Outer::rebind\<Other>::other` jako synonim . `scoped_allocator_adaptor\<Other, Inner...>`|

### <a name="methods"></a>Metody

|Nazwa|Opis|
|----------|-----------------|
|[allocate](#allocate)|Przydziela pamięć przy `Outer` użyciu alokatora.|
|[Konstruowania](#construct)|Konstruuje obiekt.|
|[Deallocate](#deallocate)|Przydziela obiekty przy użyciu zewnętrznego alokatora.|
|[zniszcz](#destroy)|Niszczy określony obiekt.|
|[inner_allocator](#inner_allocator)|Pobiera odwołanie do przechowywanego obiektu `inner_allocator_type`typu .|
|[Max_size](#max_size)|Określa maksymalną liczbę obiektów, które mogą być przydzielane przez zewnętrznego alokatora.|
|[outer_allocator](#outer_allocator)|Pobiera odwołanie do przechowywanego obiektu `outer_allocator_type`typu .|
|[select_on_container_copy_construction](#select_on_container_copy_construction)|Tworzy nowy `scoped_allocator_adaptor` obiekt z każdym przechowywanym obiektem `select_on_container_copy_construction` alokatora zainicjowanym przez wywołanie dla każdego odpowiedniego alokatora.|

### <a name="operators"></a>Operatory

|Operator|Opis|
|-|-|
|[operator=](#op_as)||
|[operator==](#op_eq_eq)||
|[operator!=](#op_noeq)||

## <a name="requirements"></a>Wymagania

**Nagłówek:** \<scoped_allocator>

**Przestrzeń nazw:** std

## <a name="scoped_allocator_adaptorallocate"></a><a name="allocate"></a>scoped_allocator_adaptor::przydziel

Przydziela pamięć przy `Outer` użyciu alokatora.

```cpp
pointer allocate(size_type count);pointer allocate(size_type count, const_void_pointer hint);
```

### <a name="parameters"></a>Parametry

*Liczba*\
Liczba elementów, dla których ma być przydzielona wystarczająca ilość miejsca do magazynowania.

*Wskazówka*\
Wskaźnik, który może pomóc obiekt alokatora przez zlokalizowanie adresu obiektu przydzielonego przed żądaniem.

### <a name="return-value"></a>Wartość zwracana

Zwraca pierwszą `Outer_traits::allocate(outer_allocator(), count)`funkcję elementu członkowskiego . Druga funkcja elementu `Outer_traits::allocate(outer_allocator(), count, hint)`członkowskiego zwraca .

## <a name="scoped_allocator_adaptorconstruct"></a><a name="construct"></a>scoped_allocator_adaptor::konstrukcja

Konstruuje obiekt.

```cpp
template <class Ty, class... Atypes>
void construct(Ty* ptr, Atypes&&... args);

template <class Ty1, class Ty2, class... Atypes1, class... Atypes2>
void construct(pair<Ty1, Ty2>* ptr, piecewise_construct_t,
    tuple<Atypes1&&...>
first, tuple<Atypes1&&...> second);

template <class Ty1, class Ty2>
void construct(pair<Ty1, Ty2>* ptr);

template <class Ty1, class Ty2, class Uy1, class Uy2>
void construct(pair<Ty1, Ty2>* ptr,
    class Uy1&& first, class Uy2&& second);

template <class Ty1, class Ty2, class Uy1, class Uy2>
void construct(pair<Ty1, Ty2>* ptr, const pair<Uy1, Uy2>& right);

template <class Ty1, class Ty2, class Uy1, class Uy2>
void construct(pair<Ty1, Ty2>* ptr, pair<Uy1, Uy2>&& right);
```

### <a name="parameters"></a>Parametry

*Ptr*\
Wskaźnik do lokalizacji pamięci, w której ma zostać skonstruowany obiekt.

*Args*\
Lista argumentów.

*Pierwszym*\
Obiekt pierwszego typu w parze.

*Drugi*\
Obiekt drugiego typu w parze.

*Prawo*\
Istniejący obiekt, który ma zostać przeniesiony lub skopiowany.

### <a name="remarks"></a>Uwagi

Pierwsza metoda konstruuje obiekt w `Outermost_traits::construct(OUTERMOST(*this), ptr, xargs...)` *ptr* wywołując , gdzie `xargs...` jest jednym z następujących.

- Jeśli `uses_allocator<Ty, inner_allocator_type>` posiada false, a następnie `xargs...` jest `args...`.

- Jeśli `uses_allocator<Ty, inner_allocator_type>` posiada prawdziwe, i `is_constructible<Ty, allocator_arg_t, inner_allocator_type, args...>` `xargs...` posiada `allocator_arg, inner_allocator(), args...`prawdziwe, to jest .

- Jeśli `uses_allocator<Ty, inner_allocator_type>` posiada prawdziwe, i `is_constructible<Ty, args..., inner_allocator()>` `xargs...` posiada `args..., inner_allocator()`prawdziwe, to jest .

Druga metoda konstruuje obiekt pary w `Outermost_traits::construct(OUTERMOST(*this), &ptr->first, xargs...)` *ptr* wywołując , gdzie `xargs...` `first...` jest `Outermost_traits::construct(OUTERMOST(*this), &ptr->second, xargs...)`modyfikowany `xargs...` `second...` jak na powyższej liście i , gdzie jest modyfikowany jak na powyższej liście.

Trzecia metoda zachowuje się `this->construct(ptr, piecewise_construct, tuple<>, tuple<>)`tak samo jak .

Czwarta metoda zachowuje się `this->construct(ptr, piecewise_construct, forward_as_tuple(std::forward<Uy1>(first), forward_as_tuple(std::forward<Uy2>(second))`tak samo jak .

Piąta metoda zachowuje się `this->construct(ptr, piecewise_construct, forward_as_tuple(right.first), forward_as_tuple(right.second))`tak samo jak .

Szósta metoda zachowuje się `this->construct(ptr, piecewise_construct, forward_as_tuple(std::forward<Uy1>(right.first), forward_as_tuple(std::forward<Uy2>(right.second))`tak samo jak .

## <a name="scoped_allocator_adaptordeallocate"></a><a name="deallocate"></a>scoped_allocator_adaptor::dlokalizuj

Przydziela obiekty przy użyciu zewnętrznego alokatora.

```cpp
void deallocate(pointer ptr, size_type count);
```

### <a name="parameters"></a>Parametry

*Ptr*\
Wskaźnik do początkowej lokalizacji obiektów, które mają zostać cofnięte.

*Liczba*\
Liczba obiektów do przydzielenia.

## <a name="scoped_allocator_adaptordestroy"></a><a name="destroy"></a>scoped_allocator_adaptor::destroy

Niszczy określony obiekt.

```cpp
template <class Ty>
void destroy(Ty* ptr)
```

### <a name="parameters"></a>Parametry

*Ptr*\
Wskaźnik do obiektu, który ma zostać zniszczony.

### <a name="return-value"></a>Wartość zwracana

`Outermost_traits::destroy(OUTERMOST(*this), ptr)`

## <a name="scoped_allocator_adaptorinner_allocator"></a><a name="inner_allocator"></a>scoped_allocator_adaptor::inner_allocator

Pobiera odwołanie do przechowywanego obiektu `inner_allocator_type`typu .

```cpp
inner_allocator_type& inner_allocator() noexcept;
const inner_allocator_type& inner_allocator() const noexcept;
```

### <a name="return-value"></a>Wartość zwracana

Odwołanie do przechowywanego obiektu `inner_allocator_type`typu .

## <a name="scoped_allocator_adaptormax_size"></a><a name="max_size"></a>scoped_allocator_adaptor::max_size

Określa maksymalną liczbę obiektów, które mogą być przydzielane przez zewnętrznego alokatora.

```cpp
size_type max_size();
```

### <a name="return-value"></a>Wartość zwracana

`Outer_traits::max_size(outer_allocator())`

## <a name="a-nameop_as--scoped_allocator_adaptoroperator"></a><a name="op_as">scoped_allocator_adaptor::operator=

```cpp
scoped_allocator_adaptor& operator=(const scoped_allocator_adaptor&) = default;
scoped_allocator_adaptor& operator=(scoped_allocator_adaptor&&) = default;
```

## <a name="a-nameop_eq_eq--scoped_allocator_adaptoroperator"></a><a name="op_eq_eq">scoped_allocator_adaptor::operator==

```cpp
template <class OuterA1, class OuterA2, class... InnerAllocs>
bool operator==(const scoped_allocator_adaptor<OuterA1, InnerAllocs...>& a,
const scoped_allocator_adaptor<OuterA2, InnerAllocs...>& b) noexcept;
```

## <a name="a-nameop_noeq--scoped_allocator_adaptoroperator"></a><a name="op_noeq">scoped_allocator_adaptor::operator!=

```cpp
template <class OuterA1, class OuterA2, class... InnerAllocs>
bool operator!=(const scoped_allocator_adaptor<OuterA1, InnerAllocs...>& a,
const scoped_allocator_adaptor<OuterA2, InnerAllocs...>& b) noexcept;
```

## <a name="scoped_allocator_adaptorouter_allocator"></a><a name="outer_allocator"></a>scoped_allocator_adaptor::outer_allocator

Pobiera odwołanie do przechowywanego obiektu `outer_allocator_type`typu .

```cpp
outer_allocator_type& outer_allocator() noexcept;
const outer_allocator_type& outer_allocator() const noexcept;
```

### <a name="return-value"></a>Wartość zwracana

Odwołanie do przechowywanego obiektu `outer_allocator_type`typu .

## <a name="scoped_allocator_adaptorrebind-struct"></a><a name="rebind_struct"></a>scoped_allocator_adaptor::ponowna struktura

Definiuje typ `Outer::rebind\<Other>::other` jako synonim . `scoped_allocator_adaptor\<Other, Inner...>`

struct rebind{ typedef Other_traits::rebind\<Inne Other_alloc>; typedef scoped_allocator_adaptor\<Other_alloc, Inner...> inne; };

## <a name="scoped_allocator_adaptorscoped_allocator_adaptor-constructor"></a><a name="scoped_allocator_adaptor"></a>scoped_allocator_adaptor::scoped_allocator_adaptor konstruktor

Konstruuje `scoped_allocator_adaptor` obiekt. Zawiera również destruktor.

```cpp
scoped_allocator_adaptor();

scoped_allocator_adaptor(const scoped_allocator_adaptor& right) noexcept;
template <class Outer2>
scoped_allocator_adaptor(
const scoped_allocator_adaptor<Outer2, Inner...>& right) noexcept;
template <class Outer2>
scoped_allocator_adaptor(
scoped_allocator_adaptor<Outer2, Inner...>&& right) noexcept;
template <class Outer2>
scoped_allocator_adaptor(Outer2&& al,
    const Inner&... rest) noexcept;

~scoped_allocator_adaptor();
```

### <a name="parameters"></a>Parametry

*Prawo*\
Istniejący `scoped_allocator_adaptor`plik .

*Al*\
Istniejący alokator ma być używany jako zewnętrzny alokator.

*Reszta*\
Lista alokatorów, które mają być używane jako alokatory wewnętrzne.

### <a name="remarks"></a>Uwagi

Pierwszy konstruktor domyślnie konstruuje swoje przechowywane obiekty alokatora. Każdy z następnych trzech konstruktorów konstruuje swoje przechowywane obiekty alokatora z odpowiednich obiektów *w prawo*. Ostatni konstruktor konstruuje swoje przechowywane obiekty alokatora z odpowiednich argumentów na liście argumentów.

## <a name="scoped_allocator_adaptorselect_on_container_copy_construction"></a><a name="select_on_container_copy_construction"></a>scoped_allocator_adaptor::select_on_container_copy_construction

Tworzy nowy `scoped_allocator_adaptor` obiekt z każdym przechowywanym obiektem `select_on_container_copy_construction` alokatora zainicjowanym przez wywołanie dla każdego odpowiedniego alokatora.

```cpp
scoped_allocator_adaptor select_on_container_copy_construction();
```

### <a name="return-value"></a>Wartość zwracana

Ta metoda `scoped_allocator_adaptor(Outer_traits::select_on_container_copy_construction(*this), inner_allocator().select_on_container_copy_construction())`skutecznie zwraca . Wynikiem jest nowy `scoped_allocator_adaptor` obiekt z każdym zapisanym obiektem `al.select_on_container_copy_construction()` alokatora zainicjowanym przez wywołanie odpowiedniego alokatora *al.*

## <a name="see-also"></a>Zobacz też

[Odwołanie do plików nagłówkowych](../standard-library/cpp-standard-library-header-files.md)
