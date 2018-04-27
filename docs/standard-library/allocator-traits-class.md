---
title: allocator_traits — klasa | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: ''
ms.topic: reference
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
dev_langs:
- C++
ms.assetid: 612974b8-b5d4-4668-82fb-824bff6821d6
caps.latest.revision: 12
author: corob-msft
ms.author: corob
manager: ghogen
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
ms.workload:
- cplusplus
ms.openlocfilehash: 8e95f203cfc59d21056119701f56eb4a0084bcce
ms.sourcegitcommit: dd1a509526fa8bb18e97ab7bc7b91cbdb3ec7059
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/26/2018
---
# <a name="allocatortraits-class"></a>allocator_traits — klasa

Obiekt, który uzupełnia opisano klasy szablonu *typu alokatora*. Typ alokatora jest dowolnego typu, który opisuje alokatora obiektu, który jest używany do zarządzania przydzielone magazynu. W szczególności dla dowolnego typu alokatora `Alloc`, można użyć `allocator_traits<Alloc>` ustalenie, wszystkie informacje, które są wymagane przez kontener włączone przydzielania. Aby uzyskać więcej informacji, zobacz domyślne [Allocator — klasa](../standard-library/allocator-class.md).

## <a name="syntax"></a>Składnia

```cpp
template <class Alloc>
class allocator_traits;
```

### <a name="typedefs"></a>Typedefs

|Nazwa|Opis|
|----------|-----------------|
|`allocator_traits::allocator_type`|Ten typ jest synonimem parametru szablonu `Alloc`.|
|`allocator_traits::const_pointer`|Ten typ jest `Alloc::const_pointer`, jeśli jest poprawnie sformułowanym typu; w przeciwnym razie ten typ jest `pointer_traits<pointer>::rebind<const value_type>`.|
|`allocator_traits::const_void_pointer`|Ten typ jest `Alloc::const_void_pointer`, jeśli jest poprawnie sformułowanym typu; w przeciwnym razie ten typ jest `pointer_traits<pointer>::rebind<const void>`.|
|`allocator_traits::difference_type`|Ten typ jest `Alloc::difference_type`, jeśli jest poprawnie sformułowanym typu; w przeciwnym razie ten typ jest `pointer_traits<pointer>::difference_type`.|
|`allocator_traits::pointer`|Ten typ jest `Alloc::pointer`, jeśli jest poprawnie sformułowanym typu; w przeciwnym razie ten typ jest `value_type *`.|
|`allocator_traits::propagate_on_container_copy_assignment`|Ten typ jest `Alloc::propagate_on_container_copy_assignment`, jeśli jest poprawnie sformułowanym typu; w przeciwnym razie ten typ jest `false_type`.|
|`allocator_traits::propagate_on_container_move_assignment`|Ten typ jest `Alloc::propagate_on_container_move_assignment`, jeśli jest poprawnie sformułowanym typu; w przeciwnym razie ten typ jest `false_type`. Jeśli typ jest spełniony, kontener włączone alokatora kopiuje jego alokatora przechowywanych na przypisania przenoszenia.|
|`allocator_traits::propagate_on_container_swap`|Ten typ jest `Alloc::propagate_on_container_swap`, jeśli jest poprawnie sformułowanym typu; w przeciwnym razie ten typ jest `false_type`. Jeśli typ jest spełniony, kontener włączone alokatora zamienia jego alokatora przechowywanych na zamiana.|
|`allocator_traits::size_type`|Ten typ jest `Alloc::size_type`, jeśli jest poprawnie sformułowanym typu; w przeciwnym razie ten typ jest `make_unsigned<difference_type>::type`.|
|`allocator_traits::value_type`|Ten typ jest synonimem `Alloc::value_type`.|
|`allocator_traits::void_pointer`|Ten typ jest `Alloc::void_pointer`, jeśli jest poprawnie sformułowanym typu; w przeciwnym razie ten typ jest `pointer_traits<pointer>::rebind<void>`.|

### <a name="static-methods"></a>Metody statyczne

Następujące metody statyczne wywołania odpowiedniej metody w parametrze danego przydzielania.

|Nazwa|Opis|
|----------|-----------------|
|[allocate](#allocate)|Metoda statyczna przydziela pamięć przy użyciu parametru danego przydzielania.|
|[construct](#construct)|Metoda statyczna używa określonego programu przydzielania do utworzenia obiektu.|
|[Cofnięcie przydziału](#deallocate)|Metoda statyczna używa określonego alokatora można cofnąć alokacji określoną liczbę obiektów.|
|[destroy](#destroy)|Metoda statyczna używa określonego alokatora aby wywołać destruktor dla obiekt bez cofanie przydziału pamięci.|
|[max_size](#max_size)|Metoda statyczna używa określonego alokatora Aby określić maksymalną liczbę obiektów, które mogą być przydzielone.|
|[select_on_container_copy_construction](#select_on_container_copy_construction)|Statyczna metoda, która wywołuje `select_on_container_copy_construction` na określony program przydzielania.|

## <a name="requirements"></a>Wymagania

**Nagłówek:** \<pamięci >

**Namespace:** Standard

## <a name="allocate"></a>  allocator_traits::allocate

Metoda statyczna przydziela pamięć przy użyciu parametru danego przydzielania.

```cpp
static pointer allocate(Alloc& al, size_type count);

static pointer allocate(Alloc& al, size_type count,
    typename allocator_traits<void>::const_pointer* hint);
```

### <a name="parameters"></a>Parametry

`al` Obiekt programu przydzielania.

`count` Liczba elementów do przydzielenia.

`hint` A `const_pointer` który może ułatwić obiektu alokatora spełniające żądanie dla magazynu dzięki umieszczeniu adresu przydzielonego obiektu przed żądania. Pustego wskaźnika jest traktowany jako bez wskazówki.

### <a name="return-value"></a>Wartość zwracana

Każda metoda zwraca wskaźnik do przydzielonego obiektu.

Zwraca pierwszy metody statycznej `al.allocate(count)`.

Druga metoda zwraca `al.allocate(count, hint)`, jeśli wyrażenie jest być dobrze uformowany; w przeciwnym razie zwraca `al.allocate(count)`.

## <a name="construct"></a>  allocator_traits::Construct

Metoda statyczna używa określonego programu przydzielania do utworzenia obiektu.

```cpp
template <class Uty, class Types>
static void construct(Alloc& al, Uty* ptr, Types&&... args);
```

### <a name="parameters"></a>Parametry

`al` Obiekt programu przydzielania.

`ptr` Wskaźnik do lokalizacji, w którym ma być skonstruowany obiekt.

`args` Lista argumentów została przekazana do konstruktora obiektu.

### <a name="remarks"></a>Uwagi

Wywołania funkcji statyczny element członkowski `al.construct(ptr, args...)`, jeśli wyrażenie jest być dobrze uformowany; w przeciwnym razie oblicza `::new (static_cast<void *>(ptr)) Uty(std::forward<Types>(args)...)`.

## <a name="deallocate"></a>  allocator_traits::deallocate

Metoda statyczna używa określonego alokatora można cofnąć alokacji określoną liczbę obiektów.

```cpp
static void deallocate(Alloc al,
    pointer ptr,
    size_type count);
```

### <a name="parameters"></a>Parametry

`al` Obiekt programu przydzielania.

`ptr` Wskaźnik do lokalizacji początkowej obiektów do przydzielenia.

`count` Liczba obiektów można cofnąć alokacji.

### <a name="remarks"></a>Uwagi

Ta metoda wywołuje `al.deallocate(ptr, count)`.

Ta metoda zgłasza nothing.

## <a name="destroy"></a>  allocator_traits::Destroy

Metoda statyczna używa określonego alokatora aby wywołać destruktor dla obiekt bez cofanie przydziału pamięci.

```cpp
template <class Uty>
static void destroy(Alloc& al, Uty* ptr);
```

### <a name="parameters"></a>Parametry

`al` Obiekt programu przydzielania.

`ptr` Wskaźnik do lokalizacji obiektu.

### <a name="remarks"></a>Uwagi

Ta metoda wywołuje `al.destroy(ptr)`, jeśli wyrażenie jest być dobrze uformowany; w przeciwnym razie oblicza `ptr->~Uty()`.

## <a name="max_size"></a>  allocator_traits::max_size

Metoda statyczna używa określonego alokatora Aby określić maksymalną liczbę obiektów, które mogą być przydzielone.

```cpp
static size_type max_size(const Alloc& al);
```

### <a name="parameters"></a>Parametry

`al` Obiekt programu przydzielania.

### <a name="remarks"></a>Uwagi

Ta metoda zwraca `al.max_size()`, jeśli wyrażenie jest być dobrze uformowany; w przeciwnym razie zwraca `numeric_limits<size_type>::max()`.

## <a name="select_on_container_copy_construction"></a>  allocator_traits::select_on_container_copy_construction

Statyczna metoda, która wywołuje `select_on_container_copy_construction` na określony program przydzielania.

```cpp
static Alloc select_on_container_copy_construction(const Alloc& al);
```

### <a name="parameters"></a>Parametry

`al` Obiekt programu przydzielania.

### <a name="return-value"></a>Wartość zwracana

Ta metoda zwraca `al.select_on_container_copy_construction()`, jeśli; w przeciwnym razie zwraca czy typ jest poprawnie sformułowany `al`.

### <a name="remarks"></a>Uwagi

Ta metoda służy do określania przydzielania, gdy skojarzone kontenera jest tworzony kopii.

## <a name="see-also"></a>Zobacz także

[\<memory>](../standard-library/memory.md)<br/>
[pointer_traits, struktura](../standard-library/pointer-traits-struct.md)<br/>
[scoped_allocator_adaptor, klasa](../standard-library/scoped-allocator-adaptor-class.md)<br/>
