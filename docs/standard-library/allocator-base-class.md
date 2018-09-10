---
title: allocator_base — klasa | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
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
dev_langs:
- C++
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
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: f55a332032b081cba45d2235f263adafde7e10f8
ms.sourcegitcommit: 761c5f7c506915f5a62ef3847714f43e9b815352
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/07/2018
ms.locfileid: "44101785"
---
# <a name="allocatorbase-class"></a>allocator_base — Klasa

Definiuje klasę bazową i typowe funkcje potrzebne do utworzenia programu przydzielania zdefiniowanych przez użytkownika z filtru synchronizacji.

## <a name="syntax"></a>Składnia

```cpp
template <class Type, class Sync>
class allocator_base
```

### <a name="parameters"></a>Parametry

|Parametr|Opis|
|---------------|-----------------|
|*Typ*|Typ elementów przydzielonej przez alokator.|
|*Synchronizacja*|Zasady synchronizacji dla alokatora, który jest [sync_none — klasa](../standard-library/sync-none-class.md), [sync_per_container — klasa](../standard-library/sync-per-container-class.md), [sync_per_thread — klasa](../standard-library/sync-per-thread-class.md), lub [sync_shared — Klasa](../standard-library/sync-shared-class.md).|

### <a name="constructors"></a>Konstruktorów

|Konstruktor|Opis|
|-|-|
|[allocator_base](#allocator_base)|Tworzy obiekt typu `allocator_base`.|

### <a name="typedefs"></a>Typedefs

|Nazwa typu|Opis|
|-|-|
|[const_pointer](#const_pointer)|Typ, który zapewnia stały wskaźnik do typu obiektu zarządzanego przez program przydzielania.|
|[const_reference](#const_reference)|Typ, który zawiera stałe odwołanie do typu obiektu zarządzanego przez program przydzielania.|
|[difference_type](#difference_type)|Podpisany typ całkowity, który może reprezentować różnicy między wartościami wskaźniki do typu obiektu zarządzanego przez program przydzielania.|
|[pointer](#pointer)|Typ, który dostarcza wskaźnik do typu obiektu zarządzanego przez program przydzielania.|
|[Odwołanie](#reference)|Typ, który zawiera odwołanie do typu obiektu zarządzanego przez program przydzielania.|
|[size_type](#size_type)|Sekwencja nieoznaczoną liczbę całkowitą reprezentujące długość każdego obiekt klasy szablonu `allocator_base` można przydzielić.|
|[value_type](#value_type)|Typ, który jest zarządzany przez program przydzielania.|

### <a name="member-functions"></a>Funkcje Członkowskie

|Funkcja elementu członkowskiego|Opis|
|-|-|
|[_Charalloc](#charalloc)|Przydziela pamięć dla tablicy typu **char**.|
|[_Chardealloc](#chardealloc)|Zwalnia pamięć dla tablicę zawierającą elementy typu **char**.|
|[Adres](#address)|Wyszukuje adres obiektu, którego wartość jest określona.|
|[allocate](#allocate)|Przydziela blok pamięci jest wystarczająco duży, aby zapisać co najmniej określonej liczby elementów.|
|[construct](#construct)|Tworzy określonego typu obiektu pod określony adres, który jest inicjowany z określoną wartością.|
|[Cofnij Przydział](#deallocate)|Zwalnia określoną liczbę obiektów z pamięci masowej rozpoczynający się od określonej pozycji.|
|[destroy](#destroy)|Wywołuje destruktora obiektów bez Trwa cofanie alokacji pamięci, do przechowywania obiektu.|
|[max_size](#max_size)|Zwraca liczbę elementów typu *typu* , może zostać przydzielone przez obiekt alokatora klas, zanim zostaną użyte wolnej pamięci w.|

## <a name="requirements"></a>Wymagania

**Nagłówek:** \<buforów >

**Namespace:** stdext

## <a name="charalloc"></a>  allocator_base::_Charalloc

Przydziela pamięć dla tablicy typu **char**.

```cpp
char *_Charalloc(size_type count);
```

### <a name="parameters"></a>Parametry

|Parametr|Opis|
|---------------|-----------------|
|*Liczba*|Liczba elementów w tablicy do przydzielenia.|

### <a name="return-value"></a>Wartość zwracana

Wskaźnik do przydzielonego obiektu.

### <a name="remarks"></a>Uwagi

Ta funkcja członkowska jest używanych przez kontenery, gdy skompilowano z opcją kompilatora, które nie można skompilować ponowne wiązanie. Implementuje `_Charalloc` do przydzielania zdefiniowanych przez użytkownika, zwracając wynik wywołania `allocate` funkcja filtr synchronizacji.

## <a name="chardealloc"></a>  allocator_base::_Chardealloc

Zwalnia pamięć dla tablicę zawierającą elementy typu **char**.

```cpp
void _Chardealloc(void* ptr, size_type count);
```

### <a name="parameters"></a>Parametry

|Parametr|Opis|
|---------------|-----------------|
|*ptr*|Wskaźnik do pierwszego obiektu można cofnąć przydziału z magazynu.|
|*Liczba*|Liczba obiektów, które można cofnąć przydziału z magazynu.|

### <a name="remarks"></a>Uwagi

Ta funkcja członkowska jest używanych przez kontenery, gdy skompilowano z opcją kompilatora, które nie można skompilować ponowne wiązanie. Implementuje `_Chardealloc` do przydzielania zdefiniowanych przez użytkownika, wywołując `deallocate` funkcja filtr synchronizacji. Ptr wskaźnik musi zostały wcześniej zwrócone przez wywołanie `_Charalloc` dla obiekt alokatora, który porównuje równa `*this`, przydzielania tablicy obiektu tego samego rozmiaru i typu. `_Chardealloc` nigdy nie zgłasza wyjątek.

## <a name="address"></a>  allocator_base::Address

Wyszukuje adres obiektu, którego wartość jest określona.

```cpp
pointer address(reference val);

const_pointer address(const_reference val);
```

### <a name="parameters"></a>Parametry

*Val*<br/>
Const lub nonconst wartość obiektu, którego adres są wyszukiwane.

### <a name="return-value"></a>Wartość zwracana

"Const" lub nonconst wskaźnik do obiektu znaleźć wartości, odpowiednio, const lub nonconst.

### <a name="remarks"></a>Uwagi

Ta funkcja elementu członkowskiego został zaimplementowany dla alokatora zdefiniowanych przez użytkownika, zwracając `&val`.

## <a name="allocate"></a>  allocator_base::allocate

Przydziela blok pamięci jest wystarczająco duży, aby zapisać co najmniej określonej liczby elementów.

```cpp
template <class Other>
pointer allocate(size_type _Nx, const Other* _Hint = 0);

pointer allocate(size_type _Nx);
```

### <a name="parameters"></a>Parametry

|Parametr|Opis|
|---------------|-----------------|
|*_Nx*|Liczba elementów w tablicy do przydzielenia.|
|*_Hint*|Ten parametr jest ignorowany.|

### <a name="return-value"></a>Wartość zwracana

Wskaźnik do przydzielonego obiektu.

### <a name="remarks"></a>Uwagi

Funkcja elementu członkowskiego implementuje alokacji pamięci dla programu przydzielania zdefiniowanych przez użytkownika, zwracając wynik wywołania `allocate` funkcji filtru synchronizacji typu typ `*` Jeśli `_Nx == 1`, inaczej, zwracając wynik wywołanie `operator new(_Nx * sizeof(Type))` Rzutowanie na typ typu `*`.

## <a name="allocator_base"></a>  allocator_base::allocator_base

Tworzy obiekt typu `allocator_base`.

```cpp
allocator_base();

template <class Other>
allocator_base(const allocator_base<Other, Sync>& right);
```

### <a name="parameters"></a>Parametry

|Parametr|Opis|
|---------------|-----------------|
|*right*|Obiekt alokatora, który ma być skopiowany.|

### <a name="remarks"></a>Uwagi

Pierwszy Konstruktor konstruuje [allocator_base —](../standard-library/allocator-base-class.md) wystąpienia. Drugi Konstruktor konstruuje `allocator_base` takie wystąpienie, dla każdego `allocator_base<Type, _Sync>` wystąpienia `a`, `allocator_base<Type, Sync>(allocator_base<Other, Sync>(a)) == a`.

## <a name="const_pointer"></a>  allocator_base::const_pointer

Typ, który zapewnia stały wskaźnik do typu obiektu zarządzanego przez program przydzielania.

```cpp
typedef const Type *const_pointer;
```

## <a name="const_reference"></a>  allocator_base::const_reference

Typ, który zawiera stałe odwołanie do typu obiektu zarządzanego przez program przydzielania.

```cpp
typedef const Type& const_reference;
```

## <a name="construct"></a>  allocator_base::Construct

Tworzy określonego typu obiektu pod określony adres, który jest inicjowany z określoną wartością.

```cpp
void construct(pointer ptr, const Type& val);
```

### <a name="parameters"></a>Parametry

|Parametr|Opis|
|---------------|-----------------|
|*ptr*|Wskaźnik do lokalizacji, w której obiekt ma zostać skonstruowane.|
|*Val*|Wartość za pomocą którego generowana jest zainicjowane.|

### <a name="remarks"></a>Uwagi

Ta funkcja elementu członkowskiego został zaimplementowany dla alokatora zdefiniowanych przez użytkownika, wywołując `new((void*)ptr Type(val)`.

## <a name="deallocate"></a>  allocator_base::deallocate

Zwalnia określoną liczbę obiektów z pamięci masowej rozpoczynający się od określonej pozycji.

```cpp
void deallocate(pointer ptr, size_type _Nx);
```

### <a name="parameters"></a>Parametry

|Parametr|Opis|
|---------------|-----------------|
|*ptr*|Wskaźnik do pierwszego obiektu można cofnąć przydziału z magazynu.|
|*_Nx*|Liczba obiektów, które można cofnąć przydziału z magazynu.|

### <a name="remarks"></a>Uwagi

Ta funkcja elementu członkowskiego został zaimplementowany dla alokatora zdefiniowanych przez użytkownika, wywołując `deallocate(ptr)` filtr synchronizacji `Sync` Jeśli `_Nx == 1`, w przeciwnym razie, wywołując `operator delete(_Nx * ptr)`.

## <a name="destroy"></a>  allocator_base::Destroy

Wywołuje destruktora obiektów bez Trwa cofanie alokacji pamięci, do przechowywania obiektu.

```cpp
void destroy(pointer ptr);
```

### <a name="parameters"></a>Parametry

|Parametr|Opis|
|---------------|-----------------|
|*ptr*|Wskaźnik, wyznaczanie adres obiektu, które mają zostać zniszczone.|

### <a name="remarks"></a>Uwagi

Ta funkcja elementu członkowskiego został zaimplementowany dla alokatora zdefiniowanych przez użytkownika, wywołując `ptr->~Type()`.

## <a name="difference_type"></a>  allocator_base::difference_type

Podpisany typ całkowity, który może reprezentować różnicy między wartościami wskaźniki do typu obiektu zarządzanego przez program przydzielania.

```cpp
typedef std::ptrdiff_t difference_type;
```

## <a name="max_size"></a>  allocator_base::max_size

Zwraca liczbę elementów typu `Type` , może zostać przydzielone przez obiekt alokatora klas, zanim zostaną użyte wolnej pamięci w.

```cpp
size_type max_size() const;
```

### <a name="return-value"></a>Wartość zwracana

Liczba elementów, które może zostać przydzielone.

### <a name="remarks"></a>Uwagi

Ta funkcja elementu członkowskiego został zaimplementowany dla alokatora zdefiniowanych przez użytkownika, zwracając `(size_t)-1 / sizeof(Type)` Jeśli `0 < (size_t)-1 / sizeof(Type)`, w przeciwnym razie `1`.

## <a name="pointer"></a>  allocator_base::Pointer

Typ, który dostarcza wskaźnik do typu obiektu zarządzanego przez program przydzielania.

```cpp
typedef Type *pointer;
```

## <a name="reference"></a>  allocator_base::Reference

Typ, który zawiera odwołanie do typu obiektu zarządzanego przez program przydzielania.

```cpp
typedef Type& reference;
```

## <a name="size_type"></a>  allocator_base::size_type

Sekwencja nieoznaczoną liczbę całkowitą reprezentujące długość każdego obiekt klasy szablonu `allocator_base` można przydzielić.

```cpp
typedef std::size_t size_type;
```

## <a name="value_type"></a>  allocator_base::value_type

Typ, który jest zarządzany przez program przydzielania.

```cpp
typedef Type value_type;
```

## <a name="see-also"></a>Zobacz także

[\<allocators — >](../standard-library/allocators-header.md)<br/>
