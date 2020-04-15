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
ms.openlocfilehash: f93c8ff53452fc98415e194966960254e7b44143
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81364982"
---
# <a name="allocator_base-class"></a>allocator_base — Klasa

Definiuje klasę podstawową i typowe funkcje potrzebne do utworzenia alokatora zdefiniowanego przez użytkownika z filtru synchronizacji.

## <a name="syntax"></a>Składnia

```cpp
template <class Type, class Sync>
class allocator_base
```

### <a name="parameters"></a>Parametry

|Parametr|Opis|
|---------------|-----------------|
|*Typ*|Typ elementów przydzielonych przez alokatora.|
|*Synchronizuj*|Zasady synchronizacji dla alokatora, który jest [sync_none Class](../standard-library/sync-none-class.md), [sync_per_container Class](../standard-library/sync-per-container-class.md), sync_per_thread [Class](../standard-library/sync-per-thread-class.md)lub [sync_shared Class](../standard-library/sync-shared-class.md).|

### <a name="constructors"></a>Konstruktorów

|Konstruktor|Opis|
|-|-|
|[allocator_base](#allocator_base)|Konstruuje obiekt `allocator_base`typu .|

### <a name="typedefs"></a>Typedefs

|Nazwa typu|Opis|
|-|-|
|[const_pointer](#const_pointer)|Typ, który zapewnia stały wskaźnik do typu obiektu zarządzanego przez alokatora.|
|[const_reference](#const_reference)|Typ, który zapewnia stałe odwołanie do typu obiektu zarządzanego przez alokatora.|
|[difference_type](#difference_type)|Podpisany typ integralny, który może reprezentować różnicę między wartościami wskaźników do typu obiektu zarządzanego przez alokatora.|
|[pointer](#pointer)|Typ, który udostępnia wskaźnik do typu obiektu zarządzanego przez alokatora.|
|[Odwołanie](#reference)|Typ, który zapewnia odwołanie do typu obiektu zarządzanego przez alokatora.|
|[size_type](#size_type)|Niepodpisany typ całka, który może reprezentować `allocator_base` długość dowolnej sekwencji, którą obiekt typu może przydzielić.|
|[value_type](#value_type)|Typ, który jest zarządzany przez alokatora.|

### <a name="member-functions"></a>Funkcje członkowskie

|Funkcja członkowce|Opis|
|-|-|
|[_Charalloc](#charalloc)|Przydziela magazyn dla tablicy typu **char**.|
|[_Chardealloc](#chardealloc)|Zwalnia magazyn dla tablicy zawierającej elementy typu **char**.|
|[Adres](#address)|Znajduje adres obiektu, którego wartość jest określona.|
|[allocate](#allocate)|Przydziela blok pamięci wystarczająco duży, aby przechowywać co najmniej określoną liczbę elementów.|
|[Konstruowania](#construct)|Konstruuje określony typ obiektu pod określonym adresem, który jest inicjowany z określoną wartością.|
|[Deallocate](#deallocate)|Zwalnia określoną liczbę obiektów z magazynu, począwszy od określonej pozycji.|
|[zniszcz](#destroy)|Wywołuje destruktora obiektów bez przydzielania alokacji pamięci, w której obiekt był przechowywany.|
|[Max_size](#max_size)|Zwraca liczbę elementów *typu Type,* które mogą być alokowane przez obiekt alokatora klasy przed użyciem wolnej pamięci.|

## <a name="requirements"></a>Wymagania

**Nagłówek:** \<alokatory>

**Obszar nazw:** stdext

## <a name="allocator_base_charalloc"></a><a name="charalloc"></a>allocator_base::_Charalloc

Przydziela magazyn dla tablicy typu **char**.

```cpp
char *_Charalloc(size_type count);
```

### <a name="parameters"></a>Parametry

|Parametr|Opis|
|---------------|-----------------|
|*Liczba*|Liczba elementów w tablicy, które mają zostać przydzielone.|

### <a name="return-value"></a>Wartość zwracana

Wskaźnik do przydzielonego obiektu.

### <a name="remarks"></a>Uwagi

Ta funkcja elementu członkowskiego jest używana przez kontenery podczas kompilowania z kompilatorem, który nie może skompilować rebind. Implementuje `_Charalloc` dla alokatora zdefiniowanego przez użytkownika, zwracając wynik `allocate` wywołania funkcji filtru synchronizacji.

## <a name="allocator_base_chardealloc"></a><a name="chardealloc"></a>allocator_base::_Chardealloc

Zwalnia magazyn dla tablicy zawierającej elementy typu **char**.

```cpp
void _Chardealloc(void* ptr, size_type count);
```

### <a name="parameters"></a>Parametry

|Parametr|Opis|
|---------------|-----------------|
|*Ptr*|Wskaźnik do pierwszego obiektu, który ma zostać cofnięty z magazynu.|
|*Liczba*|Liczba obiektów, które mają zostać przydzielone z magazynu.|

### <a name="remarks"></a>Uwagi

Ta funkcja elementu członkowskiego jest używana przez kontenery podczas kompilowania z kompilatorem, który nie może skompilować rebind. Implementuje `_Chardealloc` dla alokatora zdefiniowanego przez `deallocate` użytkownika, wywołując funkcję filtru synchronizacji. Wskaźnik ptr musi być wcześniej zwrócony `_Charalloc` przez wywołanie dla obiektu alokatora, który porównuje się równy `*this`, przydzielając obiekt tablicy o tym samym rozmiarze i typie. `_Chardealloc`nigdy nie zgłasza wyjątku.

## <a name="allocator_baseaddress"></a><a name="address"></a>allocator_base::adres

Znajduje adres obiektu, którego wartość jest określona.

```cpp
pointer address(reference val);

const_pointer address(const_reference val);
```

### <a name="parameters"></a>Parametry

*Val*\
Wartość const lub nonconst obiektu, którego adres jest przeszukiwany.

### <a name="return-value"></a>Wartość zwracana

Wskaźnik const lub nonconst do znalezionego obiektu, odpowiednio, const lub nonconst wartości.

### <a name="remarks"></a>Uwagi

Ta funkcja elementu członkowskiego jest zaimplementowana dla `&val`alokatora zdefiniowanego przez użytkownika przez zwrócenie .

## <a name="allocator_baseallocate"></a><a name="allocate"></a>allocator_base::przydziel

Przydziela blok pamięci wystarczająco duży, aby przechowywać co najmniej określoną liczbę elementów.

```cpp
template <class Other>
pointer allocate(size_type _Nx, const Other* _Hint = 0);

pointer allocate(size_type _Nx);
```

### <a name="parameters"></a>Parametry

|Parametr|Opis|
|---------------|-----------------|
|*_Nx*|Liczba elementów w tablicy, które mają zostać przydzielone.|
|*_Hint*|Ten parametr jest ignorowany.|

### <a name="return-value"></a>Wartość zwracana

Wskaźnik do przydzielonego obiektu.

### <a name="remarks"></a>Uwagi

Funkcja elementu członkowskiego implementuje alokację pamięci dla alokatora zdefiniowanego przez `allocate` użytkownika, zwracając wynik wywołania `_Nx == 1`do funkcji filtru synchronizacji `operator new(_Nx * sizeof(Type))` typu Typ, `*` `*` jeśli , w przeciwnym razie, zwracając wynik wywołania rzutowania do typu Type .

## <a name="allocator_baseallocator_base"></a><a name="allocator_base"></a>allocator_base::allocator_base

Konstruuje obiekt `allocator_base`typu .

```cpp
allocator_base();

template <class Other>
allocator_base(const allocator_base<Other, Sync>& right);
```

### <a name="parameters"></a>Parametry

|Parametr|Opis|
|---------------|-----------------|
|*Prawo*|Obiekt alokatora do skopiowania.|

### <a name="remarks"></a>Uwagi

Pierwszy konstruktor tworzy [allocator_base](../standard-library/allocator-base-class.md) wystąpienie. Drugi konstruktor tworzy `allocator_base` wystąpienie takie, `a` `allocator_base<Type, Sync>(allocator_base<Other, Sync>(a)) == a`że dla każdego `allocator_base<Type, _Sync>` wystąpienia . .

## <a name="allocator_baseconst_pointer"></a><a name="const_pointer"></a>allocator_base::const_pointer

Typ, który zapewnia stały wskaźnik do typu obiektu zarządzanego przez alokatora.

```cpp
typedef const Type *const_pointer;
```

## <a name="allocator_baseconst_reference"></a><a name="const_reference"></a>allocator_base::const_reference

Typ, który zapewnia stałe odwołanie do typu obiektu zarządzanego przez alokatora.

```cpp
typedef const Type& const_reference;
```

## <a name="allocator_baseconstruct"></a><a name="construct"></a>allocator_base::konstrukcja

Konstruuje określony typ obiektu pod określonym adresem, który jest inicjowany z określoną wartością.

```cpp
void construct(pointer ptr, const Type& val);
```

### <a name="parameters"></a>Parametry

|Parametr|Opis|
|---------------|-----------------|
|*Ptr*|Wskaźnik do lokalizacji, w której ma zostać skonstruowany obiekt.|
|*Val*|Wartość, za pomocą której obiekt jest konstruowany ma zostać zainicjowany.|

### <a name="remarks"></a>Uwagi

Ta funkcja elementu członkowskiego jest zaimplementowana `new((void*)ptr Type(val)`dla alokatora zdefiniowanego przez użytkownika przez wywołanie .

## <a name="allocator_basedeallocate"></a><a name="deallocate"></a>allocator_base::dlokalizuj

Zwalnia określoną liczbę obiektów z magazynu, począwszy od określonej pozycji.

```cpp
void deallocate(pointer ptr, size_type _Nx);
```

### <a name="parameters"></a>Parametry

|Parametr|Opis|
|---------------|-----------------|
|*Ptr*|Wskaźnik do pierwszego obiektu, który ma zostać cofnięty z magazynu.|
|*_Nx*|Liczba obiektów, które mają zostać przydzielone z magazynu.|

### <a name="remarks"></a>Uwagi

Ta funkcja elementu członkowskiego jest zaimplementowana `deallocate(ptr)` dla alokatora zdefiniowanego przez użytkownika, wywołując filtr `Sync` synchronizacji, jeśli `_Nx == 1`w przeciwnym razie przez wywołanie `operator delete(_Nx * ptr)`.

## <a name="allocator_basedestroy"></a><a name="destroy"></a>allocator_base::destroy

Wywołuje destruktora obiektów bez przydzielania alokacji pamięci, w której obiekt był przechowywany.

```cpp
void destroy(pointer ptr);
```

### <a name="parameters"></a>Parametry

|Parametr|Opis|
|---------------|-----------------|
|*Ptr*|Wskaźnik wskazujący adres obiektu, który ma zostać zniszczony.|

### <a name="remarks"></a>Uwagi

Ta funkcja elementu członkowskiego jest zaimplementowana `ptr->~Type()`dla alokatora zdefiniowanego przez użytkownika przez wywołanie .

## <a name="allocator_basedifference_type"></a><a name="difference_type"></a>allocator_base::dfference_type

Podpisany typ integralny, który może reprezentować różnicę między wartościami wskaźników do typu obiektu zarządzanego przez alokatora.

```cpp
typedef std::ptrdiff_t difference_type;
```

## <a name="allocator_basemax_size"></a><a name="max_size"></a>allocator_base::max_size

Zwraca liczbę elementów `Type` typu, które mogą być przydzielone przez obiekt alokatora klasy przed użyciem wolnej pamięci.

```cpp
size_type max_size() const;
```

### <a name="return-value"></a>Wartość zwracana

Liczba elementów, które mogą być przydzielone.

### <a name="remarks"></a>Uwagi

Ta funkcja elementu członkowskiego jest zaimplementowana dla `(size_t)-1 / sizeof(Type)` `0 < (size_t)-1 / sizeof(Type)`alokatora zdefiniowanego przez użytkownika przez zwrócenie, jeśli , w przeciwnym razie `1`.

## <a name="allocator_basepointer"></a><a name="pointer"></a>allocator_base::pointer

Typ, który udostępnia wskaźnik do typu obiektu zarządzanego przez alokatora.

```cpp
typedef Type *pointer;
```

## <a name="allocator_basereference"></a><a name="reference"></a>allocator_base::odwołanie

Typ, który zapewnia odwołanie do typu obiektu zarządzanego przez alokatora.

```cpp
typedef Type& reference;
```

## <a name="allocator_basesize_type"></a><a name="size_type"></a>allocator_base::size_type

Niepodpisany typ całka, który może reprezentować `allocator_base` długość dowolnej sekwencji, którą obiekt typu może przydzielić.

```cpp
typedef std::size_t size_type;
```

## <a name="allocator_basevalue_type"></a><a name="value_type"></a>allocator_base::value_type

Typ, który jest zarządzany przez alokatora.

```cpp
typedef Type value_type;
```

## <a name="see-also"></a>Zobacz też

[\<>alokatorów](../standard-library/allocators-header.md)
