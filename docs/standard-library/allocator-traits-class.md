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
ms.openlocfilehash: 470b3086b4bdfa776558122eda9e496fa6c4bcdc
ms.sourcegitcommit: 590e488e51389066a4da4aa06d32d4c362c23393
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/21/2019
ms.locfileid: "72690072"
---
# <a name="allocator_traits-class"></a>allocator_traits — klasa

Szablon klasy opisuje obiekt, który uzupełnia *Typ alokatora*. Typ alokatora to dowolny typ opisujący obiekt alokatora, który jest używany do zarządzania przydzielonym magazynem. W przypadku każdego typu alokatora `Alloc` można użyć `allocator_traits<Alloc>` do określenia wszystkich informacji, które są potrzebne przez kontener z włączonym alokatorem. Aby uzyskać więcej informacji, zobacz Domyślna [Klasa alokatora](../standard-library/allocator-class.md).

## <a name="syntax"></a>Składnia

```cpp
template <class Alloc>
    class allocator_traits;
```

## <a name="members"></a>Elementy członkowskie

### <a name="typedefs"></a>Typedefs

|||
|-|-|
|`allocator_type`|Ten typ jest synonimem dla parametru szablonu `Alloc`.|
|`const_pointer`|Ten typ jest `Alloc::const_pointer`, jeśli ten typ jest poprawnie sformułowany; w przeciwnym razie ten typ jest `pointer_traits<pointer>::rebind<const value_type>`.|
|`const_void_pointer`|Ten typ jest `Alloc::const_void_pointer`, jeśli ten typ jest poprawnie sformułowany; w przeciwnym razie ten typ jest `pointer_traits<pointer>::rebind<const void>`.|
|`difference_type`|Ten typ jest `Alloc::difference_type`, jeśli ten typ jest poprawnie sformułowany; w przeciwnym razie ten typ jest `pointer_traits<pointer>::difference_type`.|
|`pointer`|Ten typ jest `Alloc::pointer`, jeśli ten typ jest poprawnie sformułowany; w przeciwnym razie ten typ jest `value_type *`.|
|`propagate_on_container_copy_assignment`|Ten typ jest `Alloc::propagate_on_container_copy_assignment`, jeśli ten typ jest poprawnie sformułowany; w przeciwnym razie ten typ jest `false_type`.|
|`propagate_on_container_move_assignment`|Ten typ jest `Alloc::propagate_on_container_move_assignment`, jeśli ten typ jest poprawnie sformułowany; w przeciwnym razie ten typ jest `false_type`. Jeśli typ ma wartość true, kontener z włączoną obsługą alokatora kopiuje swój magazyn, który jest przechowywany w przypisaniu.|
|`propagate_on_container_swap`|Ten typ jest `Alloc::propagate_on_container_swap`, jeśli ten typ jest poprawnie sformułowany; w przeciwnym razie ten typ jest `false_type`. Jeśli typ ma wartość true, kontener z włączonym alokatorem zamienia swój składowany Alokator na wymianę.|
|`size_type`|Ten typ jest `Alloc::size_type`, jeśli ten typ jest poprawnie sformułowany; w przeciwnym razie ten typ jest `make_unsigned<difference_type>::type`.|
|`value_type`|Ten typ jest synonimem dla `Alloc::value_type`.|
|`void_pointer`|Ten typ jest `Alloc::void_pointer`, jeśli ten typ jest poprawnie sformułowany; w przeciwnym razie ten typ jest `pointer_traits<pointer>::rebind<void>`.|

### <a name="static-methods"></a>Metody statyczne

Następujące metody statyczne wywołują odpowiednią metodę dla danego parametru alokatora.

|||
|-|-|
|[allocate](#allocate)|Metoda statyczna, która przydziela pamięć przy użyciu danego parametru alokatora.|
|[Konstruuj](#construct)|Metoda statyczna, która używa określonego alokatora do konstruowania obiektu.|
|[alokowany](#deallocate)|Metoda statyczna, która używa określonego alokatora do cofnięcia alokacji określonej liczby obiektów.|
|[usunięcie](#destroy)|Metoda statyczna, która używa określonego alokatora do wywoływania destruktora na obiekcie bez cofania przydziału pamięci.|
|[max_size](#max_size)|Metoda statyczna, która używa określonego alokatora do określenia maksymalnej liczby obiektów, które można przydzielić.|
|[select_on_container_copy_construction](#select_on_container_copy_construction)|Metoda statyczna, która wywołuje `select_on_container_copy_construction` w ramach określonego alokatora.|

### <a name="allocate"></a>alokacji

Metoda statyczna, która przydziela pamięć przy użyciu danego parametru alokatora.

```cpp
static pointer allocate(Alloc& al, size_type count);

static pointer allocate(Alloc& al, size_type count,
    typename allocator_traits<void>::const_pointer* hint);
```

#### <a name="parameters"></a>Parametry

*al* \
Obiekt alokatora.

*liczba* \
Liczba elementów do przydzielenia.

\ *wskazówki*
@No__t_0, która może pomóc obiektowi alokatora w spełnianiu żądania dotyczącego magazynu, lokalizowanie adresu przydzielonego obiektu przed żądaniem. Wskaźnik o wartości null jest traktowany jako brak wskazówki.

#### <a name="return-value"></a>Wartość zwracana

Każda metoda zwraca wskaźnik do przydzielony obiekt.

Pierwsza metoda statyczna zwraca `al.allocate(count)`.

Druga metoda zwraca `al.allocate(count, hint)`, jeśli to wyrażenie jest dobrze sformułowane; w przeciwnym razie zwraca `al.allocate(count)`.

### <a name="construct"></a>Konstruuj

Metoda statyczna, która używa określonego alokatora do konstruowania obiektu.

```cpp
template <class Uty, class Types>
static void construct(Alloc& al, Uty* ptr, Types&&... args);
```

#### <a name="parameters"></a>Parametry

*al* \
Obiekt alokatora.

\ *PTR*
Wskaźnik do lokalizacji, w której obiekt ma zostać skonstruowany.

*argumenty* \
Lista argumentów, które są przekazane do konstruktora obiektów.

#### <a name="remarks"></a>Uwagi

Statyczna funkcja członkowska wywołuje `al.construct(ptr, args...)`, jeśli to wyrażenie jest dobrze sformułowane; w przeciwnym razie szacuje `::new (static_cast<void *>(ptr)) Uty(std::forward<Types>(args)...)`.

### <a name="deallocate"></a>alokowany

Metoda statyczna, która używa określonego alokatora do cofnięcia alokacji określonej liczby obiektów.

```cpp
static void deallocate(Alloc al,
    pointer ptr,
    size_type count);
```

#### <a name="parameters"></a>Parametry

*al* \
Obiekt alokatora.

\ *PTR*
Wskaźnik do początkowej lokalizacji obiektów, które mają zostać cofnięte.

*liczba* \
Liczba obiektów do cofnięcia alokacji.

#### <a name="remarks"></a>Uwagi

Ta metoda wywołuje `al.deallocate(ptr, count)`.

Ta metoda nie zgłasza żadnych operacji.

### <a name="destroy"></a>usunięcie

Metoda statyczna, która używa określonego alokatora do wywoływania destruktora na obiekcie bez cofania przydziału pamięci.

```cpp
template <class Uty>
    static void destroy(Alloc& al, Uty* ptr);
```

#### <a name="parameters"></a>Parametry

*al* \
Obiekt alokatora.

\ *PTR*
Wskaźnik do lokalizacji obiektu.

#### <a name="remarks"></a>Uwagi

Ta metoda wywołuje `al.destroy(ptr)`, jeśli to wyrażenie jest dobrze sformułowane; w przeciwnym razie szacuje `ptr->~Uty()`.

### <a name="max_size"></a>max_size

Metoda statyczna, która używa określonego alokatora do określenia maksymalnej liczby obiektów, które można przydzielić.

```cpp
static size_type max_size(const Alloc& al);
```

#### <a name="parameters"></a>Parametry

*al* \
Obiekt alokatora.

#### <a name="remarks"></a>Uwagi

Ta metoda zwraca `al.max_size()`, jeśli to wyrażenie jest poprawnie sformułowane; w przeciwnym razie zwraca `numeric_limits<size_type>::max()`.

### <a name="select_on_container_copy_construction"></a>select_on_container_copy_construction

Metoda statyczna, która wywołuje `select_on_container_copy_construction` w ramach określonego alokatora.

```cpp
static Alloc select_on_container_copy_construction(const Alloc& al);
```

#### <a name="parameters"></a>Parametry

*al* \
Obiekt alokatora.

#### <a name="return-value"></a>Wartość zwracana

Ta metoda zwraca `al.select_on_container_copy_construction()`, jeśli ten typ jest poprawnie sformułowany; w przeciwnym razie zwraca *Al*.

#### <a name="remarks"></a>Uwagi

Ta metoda służy do określania alokatora, gdy skojarzony kontener jest skonstruowany do kopiowania.
