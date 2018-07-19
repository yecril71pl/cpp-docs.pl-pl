---
title: scoped_allocator_adaptor, klasa | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
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
dev_langs:
- C++
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
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 7025e0d52aa882c26e2785279626959ca6b29ac1
ms.sourcegitcommit: 3614b52b28c24f70d90b20d781d548ef74ef7082
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/11/2018
ms.locfileid: "38962933"
---
# <a name="scopedallocatoradaptor-class"></a>scoped_allocator_adaptor — klasa

Przedstawia gniazdo buforów.

## <a name="syntax"></a>Składnia

```cpp
template <class Outer, class... Inner>
class scoped_allocator_adaptor;
```

## <a name="remarks"></a>Uwagi

Klasa szablonu hermetyzuje zagnieżdżonych przynajmniej jednej puli buforów. Każda takie klasa ma peryferyjnych alokatora typu `outer_allocator_type`, synonim dla `Outer`, czyli podstawa publicznych `scoped_allocator_adaptor` obiektu. `Outer` Służy do przydzielania pamięci używane przez kontener. Odwołanie do tego obiektu podstawowego alokatora można uzyskać wywołując `outer_allocator`.

W pozostałej części zestawu ma typ `inner_allocator_type`. Wewnętrzny alokatora służy do przydzielania pamięci dla elementów w kontenerze. Odwołanie do przechowywany obiekt tego typu można uzyskać wywołując `inner_allocator`. Jeśli `Inner...` nie jest pusta, `inner_allocator_type` ma typ `scoped_allocator_adaptor<Inner...>`, i `inner_allocator` wyznacza obiektu elementu członkowskiego. W przeciwnym razie `inner_allocator_type` ma typ `scoped_allocator_adaptor<Outer>`, i `inner_allocator` wyznacza cały obiekt.

Zagnieżdżanie zachowuje się tak, jakby ma dowolnego głębi replikowania jej najbardziej alokatora zhermetyzowany zgodnie z potrzebami.

Kilka koncepcji, które nie są częścią interfejsu widoczne pomocy w opisujący zachowanie tej klasy szablonu. *Peryferyjnych alokatora* pośredniczy wszystkie wywołania do konstrukcja i zniszcz metody. Efektywnie jest zdefiniowany przez funkcję cyklicznego `OUTERMOST(X)`, gdzie `OUTERMOST(X)` jest jednym z następujących czynności.

- Jeśli `X.outer_allocator()` jest poprawnie sformułowany, następnie `OUTERMOST(X)` jest `OUTERMOST(X.outer_allocator())`.

- W przeciwnym razie `OUTERMOST(X)` jest `X`.

Trzy typy są definiowane dla specyfikacji:

|Typ|Opis|
|----------|-----------------|
|`Outermost`|Typ `OUTERMOST(*this)`.|
|`Outermost_traits`|`allocator_traits<Outermost>`|
|`Outer_traits`|`allocator_traits<Outer>`|

### <a name="constructors"></a>Konstruktorów

|Nazwa|Opis|
|----------|-----------------|
|[scoped_allocator_adaptor](#scoped_allocator_adaptor)|Konstruuje `scoped_allocator_adaptor` obiektu.|

### <a name="typedefs"></a>Typedefs

|Nazwa|Opis|
|----------|-----------------|
|`const_pointer`|Ten typ jest synonimem `const_pointer` skojarzonego z alokator `Outer`.|
|`const_void_pointer`|Ten typ jest synonimem `const_void_pointer` skojarzonego z alokator `Outer`.|
|`difference_type`|Ten typ jest synonimem `difference_type` skojarzonego z alokator `Outer`.|
|`inner_allocator_type`|Ten typ jest synonimem typu zagnieżdżonego adaptera `scoped_allocator_adaptor<Inner...>`.|
|`outer_allocator_type`|Ten typ jest synonimem typu podstawowego alokatora `Outer`.|
|`pointer`|Ten typ jest synonimem `pointer` skojarzone z alokator `Outer`.|
|`propagate_on_container_copy_assignment`|Typ ma wartość true tylko wtedy, gdy `Outer_traits::propagate_on_container_copy_assignment` prawdziwe lub `inner_allocator_type::propagate_on_container_copy_assignment` prawdziwe.|
|`propagate_on_container_move_assignment`|Typ ma wartość true tylko wtedy, gdy `Outer_traits::propagate_on_container_move_assignment` prawdziwe lub `inner_allocator_type::propagate_on_container_move_assignment` prawdziwe.|
|`propagate_on_container_swap`|Typ ma wartość true tylko wtedy, gdy `Outer_traits::propagate_on_container_swap` prawdziwe lub `inner_allocator_type::propagate_on_container_swap` prawdziwe.|
|`size_type`|Ten typ jest synonimem `size_type` skojarzone z alokator `Outer`.|
|`value_type`|Ten typ jest synonimem `value_type` skojarzone z alokator `Outer`.|
|`void_pointer`|Ten typ jest synonimem `void_pointer` skojarzone z alokator `Outer`.|

### <a name="structs"></a>Struktury

|Nazwa|Opis|
|----------|-----------------|
|[scoped_allocator_adaptor::rebind Struct](#rebind_struct)|Definiuje typ `Outer::rebind\<Other>::other` jako synonim dla `scoped_allocator_adaptor\<Other, Inner...>`.|

### <a name="methods"></a>Metody

|Nazwa|Opis|
|----------|-----------------|
|[allocate](#allocate)|Przydziela pamięć przy użyciu `Outer` alokatora.|
|[construct](#construct)|Tworzy obiekt.|
|[Cofnij Przydział](#deallocate)|Zwalnia obiektów za pomocą zewnętrznego programu przydzielania.|
|[destroy](#destroy)|Niszczy określonego obiektu.|
|[inner_allocator](#inner_allocator)|Pobiera odwołanie do przechowywany obiekt typu `inner_allocator_type`.|
|[max_size](#max_size)|Określa maksymalną liczbę obiektów, które mogą zostać przydzieleni przez zewnętrzne alokatora.|
|[outer_allocator](#outer_allocator)|Pobiera odwołanie do przechowywany obiekt typu `outer_allocator_type`.|
|[select_on_container_copy_construction](#select_on_container_copy_construction)|Tworzy nową `scoped_allocator_adaptor` obiektu z każdego przechowywany obiekt alokatora inicjowany przez wywołanie `select_on_container_copy_construction` dla każdego odpowiedniego programu przydzielania.|

## <a name="requirements"></a>Wymagania

**Nagłówek:** \<scoped_allocator >

**Namespace:** standardowe

## <a name="allocate"></a>  scoped_allocator_adaptor::allocate —

Przydziela pamięć przy użyciu `Outer` alokatora.

```cpp
pointer allocate(size_type count);pointer allocate(size_type count, const_void_pointer hint);
```

### <a name="parameters"></a>Parametry

*Liczba* liczbę elementów, dla których ma można przydzielić wystarczającej ilości miejsca.

*Wskazówka* wskaźnika, który może pomóc obiekt alokatora, znajdując adres obiektu, przydzielany przed żądaniem.

### <a name="return-value"></a>Wartość zwracana

Pierwsza funkcja elementu członkowskiego zwraca `Outer_traits::allocate(outer_allocator(), count)`. Druga funkcja elementu członkowskiego zwraca `Outer_traits::allocate(outer_allocator(), count, hint)`.

## <a name="construct"></a>  scoped_allocator_adaptor::Construct —

Tworzy obiekt.

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

*PTR* wskaźnik do lokalizacji pamięci, której obiekt ma zostać skonstruowane.

*argumenty* listy argumentów.

*pierwszy* obiektu pierwszego typu w parze.

*drugi* obiekt drugi typ w parze.

*prawy* istniejącego obiektu do przeniesienia lub skopiowania.

### <a name="remarks"></a>Uwagi

Pierwsza metoda tworzy obiekt pod *ptr* przez wywołanie metody `Outermost_traits::construct(OUTERMOST(*this), ptr, xargs...)`, gdzie `xargs...` jest jednym z następujących czynności.

- Jeśli `uses_allocator<Ty, inner_allocator_type>` fałszywy, następnie `xargs...` jest `args...`.

- Jeśli `uses_allocator<Ty, inner_allocator_type>` prawdziwe, a `is_constructible<Ty, allocator_arg_t, inner_allocator_type, args...>` prawdziwe, następnie `xargs...` jest `allocator_arg, inner_allocator(), args...`.

- Jeśli `uses_allocator<Ty, inner_allocator_type>` prawdziwe, a `is_constructible<Ty, args..., inner_allocator()>` prawdziwe, następnie `xargs...` jest `args..., inner_allocator()`.

Druga metoda tworzy obiekt pary pod *ptr* przez wywołanie metody `Outermost_traits::construct(OUTERMOST(*this), &ptr->first, xargs...)`, gdzie `xargs...` jest `first...` zmodyfikowane tak jak w powyższej listy i `Outermost_traits::construct(OUTERMOST(*this), &ptr->second, xargs...)`, gdzie `xargs...` jest `second...` zmodyfikowane Podobnie jak na powyższej liście.

Trzecia metoda, zachowuje się taka sama jak `this->construct(ptr, piecewise_construct, tuple<>, tuple<>)`.

Czwarty metoda, zachowuje się taka sama jak `this->construct(ptr, piecewise_construct, forward_as_tuple(std::forward<Uy1>(first), forward_as_tuple(std::forward<Uy2>(second))`.

Piąty metoda, zachowuje się taka sama jak `this->construct(ptr, piecewise_construct, forward_as_tuple(right.first), forward_as_tuple(right.second))`.

Szósty metoda, zachowuje się taka sama jak `this->construct(ptr, piecewise_construct, forward_as_tuple(std::forward<Uy1>(right.first), forward_as_tuple(std::forward<Uy2>(right.second))`.

## <a name="deallocate"></a>  scoped_allocator_adaptor::deallocate —

Zwalnia obiektów za pomocą zewnętrznego programu przydzielania.

```cpp
void deallocate(pointer ptr, size_type count);
```

### <a name="parameters"></a>Parametry

*PTR* wskaźnika, począwszy od lokalizacji obiektów, które można cofnąć przydziału.

*Liczba* liczbę obiektów, które można cofnąć alokacji.

## <a name="destroy"></a>  scoped_allocator_adaptor::Destroy —

Niszczy określonego obiektu.

```cpp
template <class Ty>
void destroy(Ty* ptr)
```

### <a name="parameters"></a>Parametry

*PTR* wskaźnik do obiektu, które mają zostać zniszczone.

### <a name="return-value"></a>Wartość zwracana

`Outermost_traits::destroy(OUTERMOST(*this), ptr)`

## <a name="inner_allocator"></a>  scoped_allocator_adaptor::inner_allocator —

Pobiera odwołanie do przechowywany obiekt typu `inner_allocator_type`.

```cpp
inner_allocator_type& inner_allocator() noexcept;
const inner_allocator_type& inner_allocator() const noexcept;
```

### <a name="return-value"></a>Wartość zwracana

Odwołanie do przechowywany obiekt typu `inner_allocator_type`.

## <a name="max_size"></a>  scoped_allocator_adaptor::max_size —

Określa maksymalną liczbę obiektów, które mogą zostać przydzieleni przez zewnętrzne alokatora.

```cpp
size_type max_size();
```

### <a name="return-value"></a>Wartość zwracana

`Outer_traits::max_size(outer_allocator())`

## <a name="outer_allocator"></a>  scoped_allocator_adaptor::outer_allocator —

Pobiera odwołanie do przechowywany obiekt typu `outer_allocator_type`.

```cpp
outer_allocator_type& outer_allocator() noexcept;
const outer_allocator_type& outer_allocator() const noexcept;
```

### <a name="return-value"></a>Wartość zwracana

Odwołanie do przechowywany obiekt typu `outer_allocator_type`.

## <a name="rebind_struct"></a>  scoped_allocator_adaptor::rebind — struktura

Definiuje typ `Outer::rebind\<Other>::other` jako synonim dla `scoped_allocator_adaptor\<Other, Inner...>`.

ponowne wiązanie struktury {typedef Other_traits::rebind\<innych > Other_alloc; scoped_allocator_adaptor — typedef\<Other_alloc, wewnętrzny... > inne;};

## <a name="scoped_allocator_adaptor"></a>  scoped_allocator_adaptor::scoped_allocator_adaptor — Konstruktor

Konstruuje `scoped_allocator_adaptor` obiektu.

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
```

### <a name="parameters"></a>Parametry

*prawy* istniejące `scoped_allocator_adaptor`.

*Al* istniejących alokatora ma być używany jako zewnętrzne alokatora.

*REST* listy buforów, które ma być używany jako wewnętrzny buforów.

### <a name="remarks"></a>Uwagi

Pierwszy domyślny konstruktor konstruuje jej obiektów przechowywanych alokatora. Każdy następne trzy konstruktory tworzy jej obiektów przechowywanych alokatora z odpowiednimi obiektami w *prawo*. Ostatni Konstruktor konstruuje jej obiektów przechowywanych alokatora z odpowiednie argumenty na liście argumentów.

## <a name="select_on_container_copy_construction"></a>  scoped_allocator_adaptor::select_on_container_copy_construction

Tworzy nową `scoped_allocator_adaptor` obiektu z każdego przechowywany obiekt alokatora inicjowany przez wywołanie `select_on_container_copy_construction` dla każdego odpowiedniego programu przydzielania.

```cpp
scoped_allocator_adaptor select_on_container_copy_construction();
```

### <a name="return-value"></a>Wartość zwracana

Ta metoda zwróci wartość skutecznie `scoped_allocator_adaptor(Outer_traits::select_on_container_copy_construction(*this), inner_allocator().select_on_container_copy_construction())`. Wynik to nowa `scoped_allocator_adaptor` obiektu z każdego przechowywany obiekt alokatora inicjowany przez wywołanie `al.select_on_container_copy_construction()` dla odpowiedniego programu przydzielania *al*.

## <a name="see-also"></a>Zobacz także

[Odwołanie do plików nagłówkowych](../standard-library/cpp-standard-library-header-files.md)<br/>
