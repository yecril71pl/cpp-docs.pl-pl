---
title: allocator_traits — klasa
ms.date: 11/04/2016
f1_keywords:
- memory/std::allocator_traits
- memory/std::allocator_traits::propagate_on_container_move_assignment
- memory/std::allocator_traits::const_pointer
- memory/std::allocator_traits::propagate_on_container_swap
- memory/std::allocator_traits::propagate_on_container_copy_assignment
- memory/std::allocator_traits::difference_type
- memory/std::allocator_traits::allocator_type
- memory/std::allocator_traits::value_type
- memory/std::allocator_traits::pointer
- memory/std::allocator_traits::size_type
- memory/std::allocator_traits::const_void_pointer
- memory/std::allocator_traits::void_pointer
- memory/std::allocator_traits::allocate
- memory/std::allocator_traits::construct
- memory/std::allocator_traits::deallocate
- memory/std::allocator_traits::destroy
- memory/std::allocator_traits::max_size
- memory/std::allocator_traits::select_on_container_copy_construction
ms.assetid: 612974b8-b5d4-4668-82fb-824bff6821d6
helpviewer_keywords:
- std::allocator_traits [C++]
- std::allocator_traits [C++], propagate_on_container_move_assignment
- std::allocator_traits [C++], const_pointer
- std::allocator_traits [C++], propagate_on_container_swap
- std::allocator_traits [C++], propagate_on_container_copy_assignment
- std::allocator_traits [C++], difference_type
- std::allocator_traits [C++], allocator_type
- std::allocator_traits [C++], value_type
- std::allocator_traits [C++], pointer
- std::allocator_traits [C++], size_type
- std::allocator_traits [C++], const_void_pointer
- std::allocator_traits [C++], void_pointer
- std::allocator_traits [C++], allocate
- std::allocator_traits [C++], construct
- std::allocator_traits [C++], deallocate
- std::allocator_traits [C++], destroy
- std::allocator_traits [C++], max_size
- std::allocator_traits [C++], select_on_container_copy_construction
ms.openlocfilehash: 66c8c998a91ddd3e6550b57415a513fae55856da
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50537764"
---
# <a name="allocatortraits-class"></a>allocator_traits — klasa

Klasa szablonu opisuje obiekt, który uzupełnia *typ programu przydzielania*. Typ alokatora jest dowolny typ, który opisuje obiekt alokatora, który jest używany do zarządzania przydzielonej pamięci. W szczególności dla dowolnego typu alokatora `Alloc`, możesz użyć `allocator_traits<Alloc>` ustalenie, wszystkie informacje, które są wymagane przez kontener z obsługą alokatora. Aby uzyskać więcej informacji, zobacz domyślnie [alokatora klasy](../standard-library/allocator-class.md).

## <a name="syntax"></a>Składnia

```cpp
template <class Alloc>
class allocator_traits;
```

### <a name="typedefs"></a>Typedefs

|Nazwa|Opis|
|----------|-----------------|
|`allocator_traits::allocator_type`|Ten typ jest synonimem dla parametru szablonu `Alloc`.|
|`allocator_traits::const_pointer`|Ten typ jest `Alloc::const_pointer`, jeśli czy typ jest poprawnie sformułowanym; w przeciwnym razie ten typ jest `pointer_traits<pointer>::rebind<const value_type>`.|
|`allocator_traits::const_void_pointer`|Ten typ jest `Alloc::const_void_pointer`, jeśli czy typ jest poprawnie sformułowanym; w przeciwnym razie ten typ jest `pointer_traits<pointer>::rebind<const void>`.|
|`allocator_traits::difference_type`|Ten typ jest `Alloc::difference_type`, jeśli czy typ jest poprawnie sformułowanym; w przeciwnym razie ten typ jest `pointer_traits<pointer>::difference_type`.|
|`allocator_traits::pointer`|Ten typ jest `Alloc::pointer`, jeśli czy typ jest poprawnie sformułowanym; w przeciwnym razie ten typ jest `value_type *`.|
|`allocator_traits::propagate_on_container_copy_assignment`|Ten typ jest `Alloc::propagate_on_container_copy_assignment`, jeśli czy typ jest poprawnie sformułowanym; w przeciwnym razie ten typ jest `false_type`.|
|`allocator_traits::propagate_on_container_move_assignment`|Ten typ jest `Alloc::propagate_on_container_move_assignment`, jeśli czy typ jest poprawnie sformułowanym; w przeciwnym razie ten typ jest `false_type`. Prawdziwe typu kontener z obsługą alokatora kopiuje jego alokatora przechowywanych na przeniesienia przypisania.|
|`allocator_traits::propagate_on_container_swap`|Ten typ jest `Alloc::propagate_on_container_swap`, jeśli czy typ jest poprawnie sformułowanym; w przeciwnym razie ten typ jest `false_type`. Jeśli prawdziwe typu kontener z obsługą alokatora zamienia jego alokatora przechowywanych na zamiany.|
|`allocator_traits::size_type`|Ten typ jest `Alloc::size_type`, jeśli czy typ jest poprawnie sformułowanym; w przeciwnym razie ten typ jest `make_unsigned<difference_type>::type`.|
|`allocator_traits::value_type`|Ten typ jest synonimem `Alloc::value_type`.|
|`allocator_traits::void_pointer`|Ten typ jest `Alloc::void_pointer`, jeśli czy typ jest poprawnie sformułowanym; w przeciwnym razie ten typ jest `pointer_traits<pointer>::rebind<void>`.|

### <a name="static-methods"></a>Metody statyczne

Następujące metody statyczne wywołać metody odpowiedniego parametru danego programu przydzielania.

|Nazwa|Opis|
|----------|-----------------|
|[allocate](#allocate)|Statyczna metoda, która przydziela pamięć przy użyciu parametru danego programu przydzielania.|
|[construct](#construct)|Metoda statyczna, który używa określonego alokatora do konstruowania obiektu.|
|[Cofnij Przydział](#deallocate)|Metoda statyczna, która używa określonego alokatora można cofnąć alokacji określoną liczbę obiektów.|
|[destroy](#destroy)|Metoda statyczna, który używa określonego programu przydzielania może wywołać destruktor obiektu bez Trwa cofanie alokacji pamięci.|
|[max_size](#max_size)|Metoda statyczna, który używa określonego programu przydzielania, aby określić maksymalną liczbę obiektów, które mogą być przydzielone.|
|[select_on_container_copy_construction](#select_on_container_copy_construction)|Statyczna metoda, która wywołuje `select_on_container_copy_construction` na określonego alokatora.|

## <a name="requirements"></a>Wymagania

**Nagłówek:** \<pamięci >

**Namespace:** standardowe

## <a name="allocate"></a>  allocator_traits::allocate —

Statyczna metoda, która przydziela pamięć przy użyciu parametru danego programu przydzielania.

```cpp
static pointer allocate(Alloc& al, size_type count);

static pointer allocate(Alloc& al, size_type count,
    typename allocator_traits<void>::const_pointer* hint);
```

### <a name="parameters"></a>Parametry

*Al*<br/>
Obiekt programu przydzielania.

*Liczba*<br/>
Liczba elementów do przydzielenia.

*Wskazówka*<br/>
Element `const_pointer` może ułatwiającymi obiekt alokatora który spełnia żądanie dla magazynu, znajdując adres przydzielonego obiektu przed żądaniem. Wskaźnikiem typu null, jest traktowany jako bez wskazówki.

### <a name="return-value"></a>Wartość zwracana

Każda metoda zwraca wskaźnik do przydzielonego obiektu.

Zwraca pierwszy statycznej metody `al.allocate(count)`.

Druga metoda zwraca `al.allocate(count, hint)`, jeśli, wyrażenie jest dobrze sformułowany; w przeciwnym razie zwraca `al.allocate(count)`.

## <a name="construct"></a>  allocator_traits::Construct

Metoda statyczna, który używa określonego alokatora do konstruowania obiektu.

```cpp
template <class Uty, class Types>
static void construct(Alloc& al, Uty* ptr, Types&&... args);
```

### <a name="parameters"></a>Parametry

*Al*<br/>
Obiekt programu przydzielania.

*ptr*<br/>
Wskaźnik do lokalizacji, w której obiekt ma zostać skonstruowane.

*argumenty*<br/>
Lista argumentów jest przekazywany do konstruktora obiektu.

### <a name="remarks"></a>Uwagi

Wywołania funkcji członka statycznego `al.construct(ptr, args...)`, jeśli, wyrażenie jest dobrze sformułowany; w przeciwnym razie oblicza `::new (static_cast<void *>(ptr)) Uty(std::forward<Types>(args)...)`.

## <a name="deallocate"></a>  allocator_traits::deallocate —

Metoda statyczna, która używa określonego alokatora można cofnąć alokacji określoną liczbę obiektów.

```cpp
static void deallocate(Alloc al,
    pointer ptr,
    size_type count);
```

### <a name="parameters"></a>Parametry

*Al*<br/>
Obiekt programu przydzielania.

*ptr*<br/>
Wskaźnik do począwszy od lokalizacji obiektów, które można cofnąć przydziału.

*Liczba*<br/>
Liczba obiektów, które można cofnąć alokacji.

### <a name="remarks"></a>Uwagi

Ta metoda wywołuje `al.deallocate(ptr, count)`.

Ta metoda wyrzuca nothing.

## <a name="destroy"></a>  allocator_traits::Destroy —

Metoda statyczna, który używa określonego programu przydzielania może wywołać destruktor obiektu bez Trwa cofanie alokacji pamięci.

```cpp
template <class Uty>
static void destroy(Alloc& al, Uty* ptr);
```

### <a name="parameters"></a>Parametry

*Al*<br/>
Obiekt programu przydzielania.

*ptr*<br/>
Wskaźnik do lokalizacji obiektu.

### <a name="remarks"></a>Uwagi

Ta metoda wywołuje `al.destroy(ptr)`, jeśli, wyrażenie jest dobrze sformułowany; w przeciwnym razie oblicza `ptr->~Uty()`.

## <a name="max_size"></a>  allocator_traits::max_size —

Metoda statyczna, który używa określonego programu przydzielania, aby określić maksymalną liczbę obiektów, które mogą być przydzielone.

```cpp
static size_type max_size(const Alloc& al);
```

### <a name="parameters"></a>Parametry

*Al*<br/>
Obiekt programu przydzielania.

### <a name="remarks"></a>Uwagi

Ta metoda zwraca `al.max_size()`, jeśli, wyrażenie jest dobrze sformułowany; w przeciwnym razie zwraca `numeric_limits<size_type>::max()`.

## <a name="select_on_container_copy_construction"></a>  allocator_traits::select_on_container_copy_construction

Statyczna metoda, która wywołuje `select_on_container_copy_construction` na określonego alokatora.

```cpp
static Alloc select_on_container_copy_construction(const Alloc& al);
```

### <a name="parameters"></a>Parametry

*Al*<br/>
Obiekt programu przydzielania.

### <a name="return-value"></a>Wartość zwracana

Ta metoda zwraca `al.select_on_container_copy_construction()`, jeśli czy typ jest dobrze sformułowany; w przeciwnym razie zwraca *al*.

### <a name="remarks"></a>Uwagi

Ta metoda jest używana do określania alokatora, gdy skojarzony kontener jest konstruowany przez kopiowanie.

## <a name="see-also"></a>Zobacz także

[\<memory>](../standard-library/memory.md)<br/>
[pointer_traits, struktura](../standard-library/pointer-traits-struct.md)<br/>
[scoped_allocator_adaptor, klasa](../standard-library/scoped-allocator-adaptor-class.md)<br/>
