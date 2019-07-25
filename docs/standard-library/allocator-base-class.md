---
title: allocator_base — Klasa
ms.date: 11/04/2016
f1_keywords:
- allocators/stdext::allocator_base
- allocators/stdext::allocators::allocator_base
- allocators/stdext::allocator_base::const_pointer
- allocators/stdext::allocator_base::const_reference
- allocators/stdext::allocator_base::difference_type
- allocators/stdext::allocator_base::pointer
- allocators/stdext::allocator_base::reference
- allocators/stdext::allocator_base::size_type
- allocators/stdext::allocator_base::value_type
- allocators/stdext::allocator_base::_Charalloc
- allocators/stdext::allocator_base::_Chardealloc
- allocators/stdext::allocator_base::address
- allocators/stdext::allocator_base::allocate
- allocators/stdext::allocator_base::construct
- allocators/stdext::allocator_base::deallocate
- allocators/stdext::allocator_base::destroy
- allocators/stdext::allocator_base::max_size
helpviewer_keywords:
- stdext::allocator_base [C++]
- stdext::allocators [C++], allocator_base
- stdext::allocator_base [C++], const_pointer
- stdext::allocator_base [C++], const_reference
- stdext::allocator_base [C++], difference_type
- stdext::allocator_base [C++], pointer
- stdext::allocator_base [C++], reference
- stdext::allocator_base [C++], size_type
- stdext::allocator_base [C++], value_type
- stdext::allocator_base [C++], _Charalloc
- stdext::allocator_base [C++], _Chardealloc
- stdext::allocator_base [C++], address
- stdext::allocator_base [C++], allocate
- stdext::allocator_base [C++], construct
- stdext::allocator_base [C++], deallocate
- stdext::allocator_base [C++], destroy
- stdext::allocator_base [C++], max_size
ms.assetid: f920b45f-2a88-4bb0-8ead-b6126b426ed4
ms.openlocfilehash: 115f5ad4461b98f24e3aa6756e501b91ae3a1566
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/24/2019
ms.locfileid: "68456433"
---
# <a name="allocatorbase-class"></a>allocator_base — Klasa

Definiuje klasę bazową i typowe funkcje, które są konieczne do utworzenia alokatora zdefiniowanego przez użytkownika z filtru synchronizacji.

## <a name="syntax"></a>Składnia

```cpp
template <class Type, class Sync>
class allocator_base
```

### <a name="parameters"></a>Parametry

|Parametr|Opis|
|---------------|-----------------|
|*Typ*|Typ elementów przyznanych przez alokatora.|
|*Synchronizacja*|Zasady synchronizacji dla alokatora, które są [klasy sync_none](../standard-library/sync-none-class.md), klasy [sync_per_container](../standard-library/sync-per-container-class.md), klasy [sync_per_thread](../standard-library/sync-per-thread-class.md)lub [klasy sync_shared](../standard-library/sync-shared-class.md).|

### <a name="constructors"></a>Konstruktorów

|Konstruktor|Opis|
|-|-|
|[allocator_base](#allocator_base)|Konstruuje obiekt typu `allocator_base`.|

### <a name="typedefs"></a>Typedefs

|Nazwa typu|Opis|
|-|-|
|[const_pointer](#const_pointer)|Typ, który zapewnia stały wskaźnik do typu obiektu zarządzanego przez Alokator.|
|[const_reference](#const_reference)|Typ, który dostarcza stałe odwołanie do typu obiektu zarządzanego przez Alokator.|
|[difference_type](#difference_type)|Typ całkowity ze znakiem, który może reprezentować różnicę między wartościami wskaźników do typu obiektu zarządzanego przez Alokator.|
|[pointer](#pointer)|Typ, który dostarcza wskaźnik do typu obiektu zarządzanego przez Alokator.|
|[Odwołanie](#reference)|Typ, który zawiera odwołanie do typu obiektu zarządzanego przez Alokator.|
|[size_type](#size_type)|Typ całkowity bez znaku, który może reprezentować długość dowolnej sekwencji, która może być przydzielona przez obiekt klasy `allocator_base` szablonu.|
|[value_type](#value_type)|Typ, który jest zarządzany przez program przydzielający.|

### <a name="member-functions"></a>Funkcje członkowskie

|Funkcja członkowska|Opis|
|-|-|
|[_Charalloc](#charalloc)|Przydziela magazyn dla tablicy typu **char**.|
|[_Chardealloc](#chardealloc)|Zwalnia magazyn dla tablicy zawierającej elementy typu **char**.|
|[address](#address)|Znajduje adres obiektu, którego wartość jest określona.|
|[allocate](#allocate)|Przydziela blok pamięci wystarczająco duży, aby można było przechowywać co najmniej określoną liczbę elementów.|
|[construct](#construct)|Konstruuje określony typ obiektu pod określonym adresem, który jest zainicjowany z określoną wartością.|
|[alokowany](#deallocate)|Zwalnia określoną liczbę obiektów z magazynu, zaczynając od określonej pozycji.|
|[destroy](#destroy)|Wywołuje destruktor obiektów bez cofania przydziału pamięci, w której zapisano obiekt.|
|[max_size](#max_size)|Zwraca liczbę elementów typu *Type, które* mogą zostać przydzielone przez obiekt alokatora klasy przed użyciem wolnej pamięci.|

## <a name="requirements"></a>Wymagania

**Nagłówek:** \<przypisania >

**Przestrzeń nazw:** stdext

## <a name="charalloc"></a>allocator_base::_Charalloc

Przydziela magazyn dla tablicy typu **char**.

```cpp
char *_Charalloc(size_type count);
```

### <a name="parameters"></a>Parametry

|Parametr|Opis|
|---------------|-----------------|
|*liczbą*|Liczba elementów w tablicy, która ma zostać przypisana.|

### <a name="return-value"></a>Wartość zwracana

Wskaźnik do przydzielony obiekt.

### <a name="remarks"></a>Uwagi

Ta funkcja członkowska jest używana przez kontenery podczas kompilowania z kompilatorem, który nie może skompilować ponownie powiązania. Implementuje `_Charalloc` ona dla alokatora zdefiniowanego przez użytkownika, zwracając wynik wywołania `allocate` funkcji filtru synchronizacji.

## <a name="chardealloc"></a>allocator_base::_Chardealloc

Zwalnia magazyn dla tablicy zawierającej elementy typu **char**.

```cpp
void _Chardealloc(void* ptr, size_type count);
```

### <a name="parameters"></a>Parametry

|Parametr|Opis|
|---------------|-----------------|
|*ptr*|Wskaźnik do pierwszego obiektu do cofnięcia przydziału z magazynu.|
|*liczbą*|Liczba obiektów do cofnięcia przydziału z magazynu.|

### <a name="remarks"></a>Uwagi

Ta funkcja członkowska jest używana przez kontenery podczas kompilowania z kompilatorem, który nie może skompilować ponownie powiązania. Implementuje `_Chardealloc` dla alokatora zdefiniowanego przez użytkownika przez `deallocate` wywołanie funkcji filtru synchronizacji. Wskaźnik ptr musi zostać wcześniej zwrócony przez wywołanie `_Charalloc` dla obiektu alokatora, który porównuje `*this`równe, przydzielenie obiektu tablicy o tym samym rozmiarze i typie. `_Chardealloc`nigdy nie zgłasza wyjątku.

## <a name="address"></a>allocator_base:: Address

Znajduje adres obiektu, którego wartość jest określona.

```cpp
pointer address(reference val);

const_pointer address(const_reference val);
```

### <a name="parameters"></a>Parametry

*użyte*\
Wartość const lub niestała obiektu, którego adres jest wyszukiwany.

### <a name="return-value"></a>Wartość zwracana

Stała lub nadana nadana nieodpowiedniemu wskaźnikowi do obiektu, który znajduje się odpowiednio, stała lub nierówna wartość.

### <a name="remarks"></a>Uwagi

Ta funkcja członkowska jest zaimplementowana dla alokatora zdefiniowanego `&val`przez użytkownika przez zwrócenie.

## <a name="allocate"></a>allocator_base:: Allocate

Przydziela blok pamięci wystarczająco duży, aby można było przechowywać co najmniej określoną liczbę elementów.

```cpp
template <class Other>
pointer allocate(size_type _Nx, const Other* _Hint = 0);

pointer allocate(size_type _Nx);
```

### <a name="parameters"></a>Parametry

|Parametr|Opis|
|---------------|-----------------|
|*_Nx*|Liczba elementów w tablicy, która ma zostać przypisana.|
|*_Hint*|Ten parametr jest ignorowany.|

### <a name="return-value"></a>Wartość zwracana

Wskaźnik do przydzielony obiekt.

### <a name="remarks"></a>Uwagi

Funkcja członkowska implementuje alokację pamięci dla alokatora zdefiniowanego przez użytkownika, zwracając wynik wywołania `allocate` funkcji filtru synchronizacji `*` typu Type if `_Nx == 1`; w przeciwnym razie zwracając wynik Wywołanie rzutowania do typu `*`typu. `operator new(_Nx * sizeof(Type))`

## <a name="allocator_base"></a>allocator_base::allocator_base

Konstruuje obiekt typu `allocator_base`.

```cpp
allocator_base();

template <class Other>
allocator_base(const allocator_base<Other, Sync>& right);
```

### <a name="parameters"></a>Parametry

|Parametr|Opis|
|---------------|-----------------|
|*right*|Obiekt alokatora, który ma zostać skopiowany.|

### <a name="remarks"></a>Uwagi

Pierwszy Konstruktor Konstruuje wystąpienie [allocator_base](../standard-library/allocator-base-class.md) . Drugi Konstruktor konstruuje `allocator_base` wystąpienie, takie jak dla dowolnego `allocator_base<Type, _Sync>` wystąpienia `a`, `allocator_base<Type, Sync>(allocator_base<Other, Sync>(a)) == a`.

## <a name="const_pointer"></a>allocator_base::const_pointer

Typ, który zapewnia stały wskaźnik do typu obiektu zarządzanego przez Alokator.

```cpp
typedef const Type *const_pointer;
```

## <a name="const_reference"></a>allocator_base::const_reference

Typ, który dostarcza stałe odwołanie do typu obiektu zarządzanego przez Alokator.

```cpp
typedef const Type& const_reference;
```

## <a name="construct"></a>allocator_base:: konstrukcja

Konstruuje określony typ obiektu pod określonym adresem, który jest zainicjowany z określoną wartością.

```cpp
void construct(pointer ptr, const Type& val);
```

### <a name="parameters"></a>Parametry

|Parametr|Opis|
|---------------|-----------------|
|*ptr*|Wskaźnik do lokalizacji, w której obiekt ma zostać skonstruowany.|
|*użyte*|Wartość, za pomocą której tworzony jest obiekt, ma zostać zainicjowany.|

### <a name="remarks"></a>Uwagi

Ta funkcja członkowska jest zaimplementowana dla alokatora zdefiniowanego `new((void*)ptr Type(val)`przez użytkownika przez wywołanie.

## <a name="deallocate"></a>allocator_base::d eallocate

Zwalnia określoną liczbę obiektów z magazynu, zaczynając od określonej pozycji.

```cpp
void deallocate(pointer ptr, size_type _Nx);
```

### <a name="parameters"></a>Parametry

|Parametr|Opis|
|---------------|-----------------|
|*ptr*|Wskaźnik do pierwszego obiektu do cofnięcia przydziału z magazynu.|
|*_Nx*|Liczba obiektów do cofnięcia przydziału z magazynu.|

### <a name="remarks"></a>Uwagi

Ta funkcja członkowska jest zaimplementowana dla alokatora zdefiniowanego `deallocate(ptr)` przez użytkownika przez wywołanie `Sync` filtru `_Nx == 1`synchronizacji, jeśli, `operator delete(_Nx * ptr)`w przeciwnym razie, wywołując metodę.

## <a name="destroy"></a>allocator_base::d Estroy

Wywołuje destruktor obiektów bez cofania przydziału pamięci, w której zapisano obiekt.

```cpp
void destroy(pointer ptr);
```

### <a name="parameters"></a>Parametry

|Parametr|Opis|
|---------------|-----------------|
|*ptr*|Wskaźnik wyznaczający adres obiektu, który ma zostać zniszczony.|

### <a name="remarks"></a>Uwagi

Ta funkcja członkowska jest zaimplementowana dla alokatora zdefiniowanego `ptr->~Type()`przez użytkownika przez wywołanie.

## <a name="difference_type"></a>allocator_base::d ifference_type

Typ całkowity ze znakiem, który może reprezentować różnicę między wartościami wskaźników do typu obiektu zarządzanego przez Alokator.

```cpp
typedef std::ptrdiff_t difference_type;
```

## <a name="max_size"></a>allocator_base::max_size

Zwraca liczbę elementów typu `Type` , które mogą zostać przydzielone przez obiekt alokatora klasy przed użyciem wolnej pamięci.

```cpp
size_type max_size() const;
```

### <a name="return-value"></a>Wartość zwracana

Liczba elementów, które można przydzielić.

### <a name="remarks"></a>Uwagi

Ta funkcja członkowska jest zaimplementowana dla alokatora zdefiniowanego `(size_t)-1 / sizeof(Type)` przez `0 < (size_t)-1 / sizeof(Type)`użytkownika, `1`zwracając Jeśli w przeciwnym razie.

## <a name="pointer"></a>allocator_base::p ointer

Typ, który dostarcza wskaźnik do typu obiektu zarządzanego przez Alokator.

```cpp
typedef Type *pointer;
```

## <a name="reference"></a>allocator_base:: Reference

Typ, który zawiera odwołanie do typu obiektu zarządzanego przez Alokator.

```cpp
typedef Type& reference;
```

## <a name="size_type"></a>allocator_base::size_type

Typ całkowity bez znaku, który może reprezentować długość dowolnej sekwencji, która może być przydzielona przez obiekt klasy `allocator_base` szablonu.

```cpp
typedef std::size_t size_type;
```

## <a name="value_type"></a>allocator_base::value_type

Typ, który jest zarządzany przez program przydzielający.

```cpp
typedef Type value_type;
```

## <a name="see-also"></a>Zobacz także

[\<allocators>](../standard-library/allocators-header.md)
