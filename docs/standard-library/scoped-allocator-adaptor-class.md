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
ms.openlocfilehash: 1fb2842df50b0e803419e3cccdeb921c9b4fa591
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/24/2019
ms.locfileid: "68458011"
---
# <a name="scopedallocatoradaptor-class"></a>scoped_allocator_adaptor — klasa

Reprezentuje zagnieżdżenie przystawek.

## <a name="syntax"></a>Składnia

```cpp
template <class Outer, class... Inner>
class scoped_allocator_adaptor;
```

## <a name="remarks"></a>Uwagi

Klasa szablonu hermetyzuje zagnieżdżenie jednego lub kilku przydzieleń. Każda taka Klasa ma najbardziej zewnętrzny Alokator typu `outer_allocator_type`, czyli synonim dla `Outer`, który jest publiczną bazą `scoped_allocator_adaptor` obiektu. `Outer`służy do przydzielania pamięci, która ma być używana przez kontener. Możesz uzyskać odwołanie do tego obiektu podstawowego alokatora, wywołując `outer_allocator`element.

Pozostała część zagnieżdżenia ma `inner_allocator_type`typ. Wewnętrzny Alokator służy do przydzielania pamięci dla elementów w kontenerze. Możesz uzyskać odwołanie do przechowywanego obiektu tego typu przez wywołanie `inner_allocator`. Jeśli `Inner...` nie jest pusty, `inner_allocator_type` ma typ `scoped_allocator_adaptor<Inner...>`i `inner_allocator` wyznacza obiekt elementu członkowskiego. W przeciwnym razie `inner_allocator` `scoped_allocator_adaptor<Outer>` `inner_allocator_type` ma typ i wyznacza cały obiekt.

Zagnieżdżanie zachowuje się tak, jakby miał arbitralną głębokość, replikować swój najbardziej zahermetyzowany Alokator w razie konieczności.

Kilka koncepcji, które nie są częścią widocznego interfejsu pomocy w opisywaniu zachowania tej klasy szablonu. *Najbardziej zewnętrzny Alokator* koryguje wszystkie wywołania konstrukcji i zniszczenia metod. Jest ona efektywnie definiowana przez funkcję `OUTERMOST(X)`cykliczną, gdzie `OUTERMOST(X)` jest jedną z następujących.

- Jeśli `X.outer_allocator()` jest poprawnie sformułowana `OUTERMOST(X)` , to `OUTERMOST(X.outer_allocator())`jest.

- W przeciwnym razie `X`jest. `OUTERMOST(X)`

Trzy typy są zdefiniowane dla celów specyfikacji:

|Typ|Opis|
|----------|-----------------|
|`Outermost`|Typ `OUTERMOST(*this)`.|
|`Outermost_traits`|`allocator_traits<Outermost>`|
|`Outer_traits`|`allocator_traits<Outer>`|

### <a name="constructors"></a>Konstruktorów

|Nazwa|Opis|
|----------|-----------------|
|[scoped_allocator_adaptor](#scoped_allocator_adaptor)|Konstruuje `scoped_allocator_adaptor` obiekt.|

### <a name="typedefs"></a>Typedefs

|Nazwa|Opis|
|----------|-----------------|
|`const_pointer`|Ten typ jest synonimem dla `const_pointer` , który jest skojarzony z alokatorem. `Outer`|
|`const_void_pointer`|Ten typ jest synonimem dla `const_void_pointer` , który jest skojarzony z alokatorem. `Outer`|
|`difference_type`|Ten typ jest synonimem dla `difference_type` , który jest skojarzony z alokatorem. `Outer`|
|`inner_allocator_type`|Ten typ jest synonimem dla typu zagnieżdżonego adaptera `scoped_allocator_adaptor<Inner...>`.|
|`outer_allocator_type`|Ten typ jest synonimem dla typu podstawowego alokatora `Outer`.|
|`pointer`|Ten typ jest synonimem `pointer` skojarzonym z alokatorem. `Outer`|
|`propagate_on_container_copy_assignment`|Typ ma wartość true tylko wtedy `Outer_traits::propagate_on_container_copy_assignment` , gdy ma `inner_allocator_type::propagate_on_container_copy_assignment` wartość true lub ma wartość true.|
|`propagate_on_container_move_assignment`|Typ ma wartość true tylko wtedy `Outer_traits::propagate_on_container_move_assignment` , gdy ma `inner_allocator_type::propagate_on_container_move_assignment` wartość true lub ma wartość true.|
|`propagate_on_container_swap`|Typ ma wartość true tylko wtedy `Outer_traits::propagate_on_container_swap` , gdy ma `inner_allocator_type::propagate_on_container_swap` wartość true lub ma wartość true.|
|`size_type`|Ten typ jest synonimem `size_type` skojarzonym z alokatorem. `Outer`|
|`value_type`|Ten typ jest synonimem `value_type` skojarzonym z alokatorem. `Outer`|
|`void_pointer`|Ten typ jest synonimem `void_pointer` skojarzonym z alokatorem. `Outer`|

### <a name="structs"></a>Struktury

|Nazwa|Opis|
|----------|-----------------|
|[scoped_allocator_adaptor::rebind Struct](#rebind_struct)|Definiuje typ `Outer::rebind\<Other>::other` jako synonim dla `scoped_allocator_adaptor\<Other, Inner...>`.|

### <a name="methods"></a>Metody

|Nazwa|Opis|
|----------|-----------------|
|[allocate](#allocate)|Przydziela pamięć przy użyciu `Outer` alokatora.|
|[construct](#construct)|Konstruuje obiekt.|
|[alokowany](#deallocate)|Cofa alokację obiektów przy użyciu alokatora zewnętrznego.|
|[destroy](#destroy)|Niszczy określony obiekt.|
|[inner_allocator](#inner_allocator)|Pobiera odwołanie do przechowywanego obiektu typu `inner_allocator_type`.|
|[max_size](#max_size)|Określa maksymalną liczbę obiektów, które mogą zostać przydzielone przez alokatora zewnętrznego.|
|[outer_allocator](#outer_allocator)|Pobiera odwołanie do przechowywanego obiektu typu `outer_allocator_type`.|
|[select_on_container_copy_construction](#select_on_container_copy_construction)|Tworzy nowy `scoped_allocator_adaptor` obiekt z każdym przechowywanym obiektem alokatora, `select_on_container_copy_construction` który jest inicjowany przez wywołanie dla każdego odpowiedniego alokatora.|

### <a name="operators"></a>Operatory

|Operator|Opis|
|-|-|
|[operator=](#op_as)||
|[operator==](#op_eq_eq)||
|[operator!=](#op_noeq)||

## <a name="requirements"></a>Wymagania

**Nagłówek:** \<scoped_allocator >

**Przestrzeń nazw:** std

## <a name="allocate"></a>scoped_allocator_adaptor:: Allocate

Przydziela pamięć przy użyciu `Outer` alokatora.

```cpp
pointer allocate(size_type count);pointer allocate(size_type count, const_void_pointer hint);
```

### <a name="parameters"></a>Parametry

*liczbą*\
Liczba elementów, dla których należy przydzielyć wystarczającą ilość miejsca do magazynowania.

*Hint*\
Wskaźnik, który może pomóc obiektowi alokatora, lokalizowanie adresu obiektu przydzielonego przed żądaniem.

### <a name="return-value"></a>Wartość zwracana

Pierwsza funkcja elementu członkowskiego `Outer_traits::allocate(outer_allocator(), count)`zwraca. Druga funkcja członkowska zwraca `Outer_traits::allocate(outer_allocator(), count, hint)`wartość.

## <a name="construct"></a>scoped_allocator_adaptor:: konstrukcja

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

*PTR*\
Wskaźnik do lokalizacji pamięci, w której ma zostać skonstruowany obiekt.

*argumentów*\
Lista argumentów.

*pierwszego*\
Obiekt pierwszego typu w parze.

*drugi*\
Obiekt drugiego typu w parze.

*Kliknij*\
Istniejący obiekt do przeniesienia lub skopiowania.

### <a name="remarks"></a>Uwagi

Pierwsza metoda konstruuje obiekt w *PTR* przez wywołanie `Outermost_traits::construct(OUTERMOST(*this), ptr, xargs...)`, gdzie `xargs...` jest jedną z następujących.

- Jeśli `uses_allocator<Ty, inner_allocator_type>` `xargs...` ma wartość false, to `args...`jest.

- Jeśli `uses_allocator<Ty, inner_allocator_type>` ma wartość true i `is_constructible<Ty, allocator_arg_t, inner_allocator_type, args...>` ma wartość true, `xargs...` to `allocator_arg, inner_allocator(), args...`.

- Jeśli `uses_allocator<Ty, inner_allocator_type>` ma wartość true i `is_constructible<Ty, args..., inner_allocator()>` ma wartość true, `xargs...` to `args..., inner_allocator()`.

Druga metoda konstruuje obiekt pary o wartości *PTR* przez wywołanie `Outermost_traits::construct(OUTERMOST(*this), &ptr->first, xargs...)`, gdzie `xargs...` jest `first...` modyfikowany zgodnie z powyższej listy `Outermost_traits::construct(OUTERMOST(*this), &ptr->second, xargs...)`i, `xargs...` gdzie `second...` jest modyfikowany zgodnie z powyższą listą.

Trzecia metoda zachowuje się tak samo jak `this->construct(ptr, piecewise_construct, tuple<>, tuple<>)`.

Czwarta metoda zachowuje się tak samo jak `this->construct(ptr, piecewise_construct, forward_as_tuple(std::forward<Uy1>(first), forward_as_tuple(std::forward<Uy2>(second))`.

Piąta metoda zachowuje się tak samo jak `this->construct(ptr, piecewise_construct, forward_as_tuple(right.first), forward_as_tuple(right.second))`.

Szósta metoda zachowuje się tak samo jak `this->construct(ptr, piecewise_construct, forward_as_tuple(std::forward<Uy1>(right.first), forward_as_tuple(std::forward<Uy2>(right.second))`.

## <a name="deallocate"></a>scoped_allocator_adaptor::d eallocate

Cofa alokację obiektów przy użyciu alokatora zewnętrznego.

```cpp
void deallocate(pointer ptr, size_type count);
```

### <a name="parameters"></a>Parametry

*PTR*\
Wskaźnik do początkowej lokalizacji obiektów, które mają zostać cofnięte.

*liczbą*\
Liczba obiektów do cofnięcia alokacji.

## <a name="destroy"></a>scoped_allocator_adaptor::d Estroy

Niszczy określony obiekt.

```cpp
template <class Ty>
void destroy(Ty* ptr)
```

### <a name="parameters"></a>Parametry

*PTR*\
Wskaźnik do obiektu, który ma zostać zniszczony.

### <a name="return-value"></a>Wartość zwracana

`Outermost_traits::destroy(OUTERMOST(*this), ptr)`

## <a name="inner_allocator"></a>scoped_allocator_adaptor::inner_allocator

Pobiera odwołanie do przechowywanego obiektu typu `inner_allocator_type`.

```cpp
inner_allocator_type& inner_allocator() noexcept;
const inner_allocator_type& inner_allocator() const noexcept;
```

### <a name="return-value"></a>Wartość zwracana

Odwołanie do przechowywanego obiektu typu `inner_allocator_type`.

## <a name="max_size"></a>scoped_allocator_adaptor::max_size

Określa maksymalną liczbę obiektów, które mogą zostać przydzielone przez alokatora zewnętrznego.

```cpp
size_type max_size();
```

### <a name="return-value"></a>Wartość zwracana

`Outer_traits::max_size(outer_allocator())`

## <a name="a-nameopas--scopedallocatoradaptoroperator"></a><a name="op_as">scoped_allocator_adaptor:: operator =

```cpp
scoped_allocator_adaptor& operator=(const scoped_allocator_adaptor&) = default;
scoped_allocator_adaptor& operator=(scoped_allocator_adaptor&&) = default;
```

## <a name="a-nameopeqeq--scopedallocatoradaptoroperator"></a><a name="op_eq_eq">scoped_allocator_adaptor:: operator = =

```cpp
template <class OuterA1, class OuterA2, class... InnerAllocs>
bool operator==(const scoped_allocator_adaptor<OuterA1, InnerAllocs...>& a,
const scoped_allocator_adaptor<OuterA2, InnerAllocs...>& b) noexcept;
```

## <a name="a-nameopnoeq--scopedallocatoradaptoroperator"></a><a name="op_noeq">scoped_allocator_adaptor:: operator! =

```cpp
template <class OuterA1, class OuterA2, class... InnerAllocs>
bool operator!=(const scoped_allocator_adaptor<OuterA1, InnerAllocs...>& a,
const scoped_allocator_adaptor<OuterA2, InnerAllocs...>& b) noexcept;
```

## <a name="outer_allocator"></a>scoped_allocator_adaptor::outer_allocator

Pobiera odwołanie do przechowywanego obiektu typu `outer_allocator_type`.

```cpp
outer_allocator_type& outer_allocator() noexcept;
const outer_allocator_type& outer_allocator() const noexcept;
```

### <a name="return-value"></a>Wartość zwracana

Odwołanie do przechowywanego obiektu typu `outer_allocator_type`.

## <a name="rebind_struct"></a>scoped_allocator_adaptor:: rebind struct

Definiuje typ `Outer::rebind\<Other>::other` jako synonim dla `scoped_allocator_adaptor\<Other, Inner...>`.

rebind struktury {typedef Other_traits:: rebind\<inne > Other_alloc; typedef scoped_allocator_adaptor\<Other_alloc, Inner... > inne; };

## <a name="scoped_allocator_adaptor"></a>scoped_allocator_adaptor:: scoped_allocator_adaptor — Konstruktor

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

*Kliknij*\
Istniejący `scoped_allocator_adaptor`.

*wsp*\
Istniejący Alokator, który będzie używany jako Alokator zewnętrzny.

*część*\
Lista przylistów, które mają być używane jako wewnętrzne przypisania.

### <a name="remarks"></a>Uwagi

Pierwszy Konstruktor domyślnie konstruuje swoje przechowywane obiekty alokatora. Każdy z następnych trzech konstruktorów konstruuje swoje przechowywane obiekty alokatora z odpowiednich obiektów w *prawo*. Ostatni Konstruktor konstruuje przechowywane obiekty alokatora z odpowiednich argumentów na liście argumentów.

## <a name="select_on_container_copy_construction"></a>  scoped_allocator_adaptor::select_on_container_copy_construction

Tworzy nowy `scoped_allocator_adaptor` obiekt z każdym przechowywanym obiektem alokatora, `select_on_container_copy_construction` który jest inicjowany przez wywołanie dla każdego odpowiedniego alokatora.

```cpp
scoped_allocator_adaptor select_on_container_copy_construction();
```

### <a name="return-value"></a>Wartość zwracana

Ta metoda efektywnie zwraca `scoped_allocator_adaptor(Outer_traits::select_on_container_copy_construction(*this), inner_allocator().select_on_container_copy_construction())`wartość. Wynikiem jest nowy `scoped_allocator_adaptor` obiekt z każdym przechowywanym obiektem alokatora, który `al.select_on_container_copy_construction()` jest inicjowany przez wywołanie dla odpowiedniego alokatora *Al*.

## <a name="see-also"></a>Zobacz także

[Dokumentacja plików nagłówkowych](../standard-library/cpp-standard-library-header-files.md)
