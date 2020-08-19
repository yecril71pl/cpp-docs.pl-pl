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
ms.openlocfilehash: f642c21f2b1060dd5adc5c3d98144592c3413777
ms.sourcegitcommit: 1839405b97036891b6e4d37c99def044d6f37eff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/18/2020
ms.locfileid: "88562639"
---
# <a name="allocator_base-class"></a>allocator_base — Klasa

Definiuje klasę bazową i typowe funkcje, które są konieczne do utworzenia alokatora zdefiniowanego przez użytkownika z filtru synchronizacji.

## <a name="syntax"></a>Składnia

```cpp
template <class Type, class Sync>
class allocator_base
```

### <a name="parameters"></a>Parametry

*Wprowadź*\
Typ elementów przyznanych przez alokatora.

*Synchronizacji*\
Zasady synchronizacji dla alokatora, który jest klasą [sync_none](sync-none-class.md), klasą [sync_per_container](sync-per-container-class.md), [klasą sync_per_thread](sync-per-thread-class.md)lub [klasą sync_shared](sync-shared-class.md).

### <a name="constructors"></a>Konstruktory

|Konstruktor|Opis|
|-|-|
|[allocator_base](#allocator_base)|Konstruuje obiekt typu `allocator_base` .|

### <a name="typedefs"></a>Typedefs

|Nazwa typu|Opis|
|-|-|
|[const_pointer](#const_pointer)|Typ, który zapewnia stały wskaźnik do typu obiektu zarządzanego przez Alokator.|
|[const_reference](#const_reference)|Typ, który dostarcza stałe odwołanie do typu obiektu zarządzanego przez Alokator.|
|[difference_type](#difference_type)|Typ całkowity ze znakiem, który może reprezentować różnicę między wartościami wskaźników do typu obiektu zarządzanego przez Alokator.|
|[pointer](#pointer)|Typ, który dostarcza wskaźnik do typu obiektu zarządzanego przez Alokator.|
|[odwoła](#reference)|Typ, który zawiera odwołanie do typu obiektu zarządzanego przez Alokator.|
|[size_type](#size_type)|Typ całkowity bez znaku, który może reprezentować długość dowolnej sekwencji, którą obiekt typu `allocator_base` może przydzielić.|
|[value_type](#value_type)|Typ, który jest zarządzany przez program przydzielający.|

### <a name="member-functions"></a>Funkcje członkowskie

|Funkcja członkowska|Opis|
|-|-|
|[_Charalloc](#charalloc)|Przydziela magazyn dla tablicy typu **`char`** .|
|[_Chardealloc](#chardealloc)|Zwalnia magazyn dla tablicy zawierającej elementy typu **`char`** .|
|[Ulica](#address)|Znajduje adres obiektu, którego wartość jest określona.|
|[allocate](#allocate)|Przydziela blok pamięci wystarczająco duży, aby można było przechowywać co najmniej określoną liczbę elementów.|
|[Konstruuj](#construct)|Konstruuje określony typ obiektu pod określonym adresem, który jest zainicjowany z określoną wartością.|
|[alokowany](#deallocate)|Zwalnia określoną liczbę obiektów z magazynu, zaczynając od określonej pozycji.|
|[usunięcie](#destroy)|Wywołuje destruktor obiektów bez cofania przydziału pamięci, w której zapisano obiekt.|
|[max_size](#max_size)|Zwraca liczbę *elementów typu Type, które* mogą zostać przydzielone przez obiekt alokatora klasy przed użyciem wolnej pamięci.|

## <a name="requirements"></a>Wymagania

**Nagłówek:**\<allocators>

**Przestrzeń nazw:** stdext

## <a name="allocator_base_charalloc"></a><a name="charalloc"></a> allocator_base:: _Charalloc

Przydziela magazyn dla tablicy typu **`char`** .

```cpp
char *_Charalloc(size_type count);
```

### <a name="parameters"></a>Parametry

*liczbą*\
Liczba elementów w tablicy, która ma zostać przypisana.

### <a name="return-value"></a>Wartość zwracana

Wskaźnik do przydzielony obiekt.

### <a name="remarks"></a>Uwagi

Ta funkcja członkowska jest używana przez kontenery podczas kompilowania z kompilatorem, który nie może skompilować ponownie powiązania. Implementuje ona `_Charalloc` dla alokatora zdefiniowanego przez użytkownika, zwracając wynik wywołania `allocate` funkcji filtru synchronizacji.

## <a name="allocator_base_chardealloc"></a><a name="chardealloc"></a> allocator_base:: _Chardealloc

Zwalnia magazyn dla tablicy zawierającej elementy typu **`char`** .

```cpp
void _Chardealloc(void* ptr, size_type count);
```

### <a name="parameters"></a>Parametry

*PTR*\
Wskaźnik do pierwszego obiektu do cofnięcia przydziału z magazynu.

*liczbą*\
Liczba obiektów do cofnięcia przydziału z magazynu.

### <a name="remarks"></a>Uwagi

Ta funkcja członkowska jest używana przez kontenery podczas kompilowania z kompilatorem, który nie może skompilować ponownie powiązania. Implementuje `_Chardealloc` dla alokatora zdefiniowanego przez użytkownika przez wywołanie `deallocate` funkcji filtru synchronizacji. Wskaźnik ptr musi zostać wcześniej zwrócony przez wywołanie `_Charalloc` dla obiektu alokatora, który porównuje równe **`*this`** , przydzielenie obiektu tablicy o tym samym rozmiarze i typie. `_Chardealloc` nigdy nie zgłasza wyjątku.

## <a name="allocator_baseaddress"></a><a name="address"></a> allocator_base:: Address

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

Ta funkcja członkowska jest zaimplementowana dla alokatora zdefiniowanego przez użytkownika przez zwrócenie `&val` .

## <a name="allocator_baseallocate"></a><a name="allocate"></a> allocator_base:: Allocate

Przydziela blok pamięci wystarczająco duży, aby można było przechowywać co najmniej określoną liczbę elementów.

```cpp
template <class Other>
pointer allocate(size_type _Nx, const Other* _Hint = 0);

pointer allocate(size_type _Nx);
```

### <a name="parameters"></a>Parametry

*_Nx*\
Liczba elementów w tablicy, która ma zostać przypisana.

*_Hint*\
Ten parametr jest ignorowany.

### <a name="return-value"></a>Wartość zwracana

Wskaźnik do przydzielony obiekt.

### <a name="remarks"></a>Uwagi

Funkcja członkowska implementuje alokację pamięci dla alokatora zdefiniowanego przez użytkownika przez zwrócenie wyniku wywołania `allocate` funkcji filtru synchronizacji typu Type `*` if `_Nx == 1` , w przeciwnym razie zwracając wynik wywołania na typ `operator new(_Nx * sizeof(Type))` typu `*` .

## <a name="allocator_baseallocator_base"></a><a name="allocator_base"></a> allocator_base:: allocator_base

Konstruuje obiekt typu `allocator_base` .

```cpp
allocator_base();

template <class Other>
allocator_base(const allocator_base<Other, Sync>& right);
```

### <a name="parameters"></a>Parametry

*Kliknij*\
Obiekt alokatora, który ma zostać skopiowany.

### <a name="remarks"></a>Uwagi

Pierwszy Konstruktor Konstruuje wystąpienie [allocator_base](allocator-base-class.md) . Drugi Konstruktor konstruuje `allocator_base` wystąpienie, takie jak dla dowolnego `allocator_base<Type, _Sync>` wystąpienia `a` , `allocator_base<Type, Sync>(allocator_base<Other, Sync>(a)) == a` .

## <a name="allocator_baseconst_pointer"></a><a name="const_pointer"></a> allocator_base:: const_pointer

Typ, który zapewnia stały wskaźnik do typu obiektu zarządzanego przez Alokator.

```cpp
typedef const Type *const_pointer;
```

## <a name="allocator_baseconst_reference"></a><a name="const_reference"></a> allocator_base:: const_reference

Typ, który dostarcza stałe odwołanie do typu obiektu zarządzanego przez Alokator.

```cpp
typedef const Type& const_reference;
```

## <a name="allocator_baseconstruct"></a><a name="construct"></a> allocator_base:: konstrukcja

Konstruuje określony typ obiektu pod określonym adresem, który jest zainicjowany z określoną wartością.

```cpp
void construct(pointer ptr, const Type& val);
```

### <a name="parameters"></a>Parametry

*PTR*\
Wskaźnik do lokalizacji, w której obiekt ma zostać skonstruowany.

*użyte*\
Wartość, za pomocą której tworzony jest obiekt, ma zostać zainicjowany.

### <a name="remarks"></a>Uwagi

Ta funkcja członkowska jest zaimplementowana dla alokatora zdefiniowanego przez użytkownika przez wywołanie `new((void*)ptr Type(val)` .

## <a name="allocator_basedeallocate"></a><a name="deallocate"></a> allocator_base::d eallocate

Zwalnia określoną liczbę obiektów z magazynu, zaczynając od określonej pozycji.

```cpp
void deallocate(pointer ptr, size_type _Nx);
```

### <a name="parameters"></a>Parametry

*PTR*\
Wskaźnik do pierwszego obiektu do cofnięcia przydziału z magazynu.

*_Nx*\
Liczba obiektów do cofnięcia przydziału z magazynu.

### <a name="remarks"></a>Uwagi

Ta funkcja członkowska jest zaimplementowana dla alokatora zdefiniowanego przez użytkownika przez wywołanie `deallocate(ptr)` filtru synchronizacji `Sync` `_Nx == 1` , jeśli, w przeciwnym razie, wywołując metodę `operator delete(_Nx * ptr)` .

## <a name="allocator_basedestroy"></a><a name="destroy"></a> allocator_base::d Estroy

Wywołuje destruktor obiektów bez cofania przydziału pamięci, w której zapisano obiekt.

```cpp
void destroy(pointer ptr);
```

### <a name="parameters"></a>Parametry

*PTR*\
Wskaźnik wyznaczający adres obiektu, który ma zostać zniszczony.

### <a name="remarks"></a>Uwagi

Ta funkcja członkowska jest zaimplementowana dla alokatora zdefiniowanego przez użytkownika przez wywołanie `ptr->~Type()` .

## <a name="allocator_basedifference_type"></a><a name="difference_type"></a> allocator_base::d ifference_type

Typ całkowity ze znakiem, który może reprezentować różnicę między wartościami wskaźników do typu obiektu zarządzanego przez Alokator.

```cpp
typedef std::ptrdiff_t difference_type;
```

## <a name="allocator_basemax_size"></a><a name="max_size"></a> allocator_base:: max_size

Zwraca liczbę elementów typu `Type` , które mogą zostać przydzielone przez obiekt alokatora klasy przed użyciem wolnej pamięci.

```cpp
size_type max_size() const;
```

### <a name="return-value"></a>Wartość zwracana

Liczba elementów, które można przydzielić.

### <a name="remarks"></a>Uwagi

Ta funkcja członkowska jest zaimplementowana dla alokatora zdefiniowanego przez użytkownika, zwracając `(size_t)-1 / sizeof(Type)` Jeśli w `0 < (size_t)-1 / sizeof(Type)` przeciwnym razie `1` .

## <a name="allocator_basepointer"></a><a name="pointer"></a> allocator_base::p ointer

Typ, który dostarcza wskaźnik do typu obiektu zarządzanego przez Alokator.

```cpp
typedef Type *pointer;
```

## <a name="allocator_basereference"></a><a name="reference"></a> allocator_base:: Reference

Typ, który zawiera odwołanie do typu obiektu zarządzanego przez Alokator.

```cpp
typedef Type& reference;
```

## <a name="allocator_basesize_type"></a><a name="size_type"></a> allocator_base:: size_type

Typ całkowity bez znaku, który może reprezentować długość dowolnej sekwencji, którą obiekt typu `allocator_base` może przydzielić.

```cpp
typedef std::size_t size_type;
```

## <a name="allocator_basevalue_type"></a><a name="value_type"></a> allocator_base:: value_type

Typ, który jest zarządzany przez program przydzielający.

```cpp
typedef Type value_type;
```

## <a name="see-also"></a>Zobacz też

[\<allocators>](allocators-header.md)
