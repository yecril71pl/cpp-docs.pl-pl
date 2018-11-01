---
title: pointer_traits — struktura
ms.date: 11/04/2016
f1_keywords:
- memory/std::pointer_traits::element_type
- memory/std::pointer_traits::pointer
- memory/std::pointer_traits
- memory/std::pointer_traits::difference_type
- memory/std::pointer_traits::rebind
- xmemory0/std::pointer_traits::element_type
- xmemory0/std::pointer_traits::pointer
- xmemory0/std::pointer_traits
- xmemory0/std::pointer_traits::difference_type
- xmemory0/std::pointer_traits::rebind
- memory/std::pointer_traits::pointer_to
ms.assetid: 545aecf1-3561-4859-8b34-603c079fe1b3
ms.openlocfilehash: b661d4b36ce48a08faba6638c5114f3f4e6981a6
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50434791"
---
# <a name="pointertraits-struct"></a>pointer_traits — struktura

Dostarcza informacje, które są wymagane przez obiekt klasy szablonu `allocator_traits` do opisania alokatora z typem wskaźnika `Ptr`.

## <a name="syntax"></a>Składnia

```cpp
template <class Ptr>
struct pointer_traits;
```

## <a name="remarks"></a>Uwagi

PTR można surowego wskaźnika typu `Ty *` lub klasie z atrybutem następujące właściwości.

```cpp
struct Ptr
   { // describes a pointer type usable by allocators
   typedef Ptr pointer;
   typedef T1 element_type; // optional
   typedef T2 difference_type; // optional
   template <class Other>
   using rebind = typename Ptr<Other, Rest...>; // optional
   static pointer pointer_to(element_type& obj);
   // optional
   };
```

### <a name="typedefs"></a>Typedefs

|Nazwa|Opis|
|----------|-----------------|
|`typedef T2 difference_type`|Typ `T2` jest `Ptr::difference_type` istnienia tego typu, w przeciwnym razie `ptrdiff_t`. Jeśli `Ptr` jest surowy wskaźnik jest typu `ptrdiff_t`.|
|`typedef T1 element_type`|Typ `T1` jest `Ptr::element_type` istnienia tego typu, w przeciwnym razie `Ty`. Jeśli `Ptr` jest surowy wskaźnik jest typu `Ty`.|
|`typedef Ptr pointer`|Typ jest `Ptr`.|

### <a name="structs"></a>Struktury

|Nazwa|Opis|
|----------|-----------------|
|`pointer_traits::rebind`|Próbuje przekonwertować podstawowego wskaźnika typu do określonego typu.|

### <a name="methods"></a>Metody

|Nazwa|Opis|
|----------|-----------------|
|[pointer_to](#pointer_to)|Konwertuje dowolnego odwołania do obiektu klasy `Ptr`.|

## <a name="requirements"></a>Wymagania

**Nagłówek:** \<pamięci >

**Namespace:** standardowe

## <a name="pointer_to"></a>  pointer_to

Metoda statyczna zwraca `Ptr::pointer_to(obj)`, jeśli istnieje w tej funkcji. W przeciwnym razie nie jest możliwe do przekonwertowania dowolnego odwołania do obiektu klasy `Ptr`. Jeśli `Ptr` jest surowy wskaźnik, Metoda ta zwraca `addressof(obj)`.

```cpp
static pointer pointer_to(element_type& obj);
```

## <a name="see-also"></a>Zobacz także

[\<memory>](../standard-library/memory.md)<br/>
[allocator_traits, klasa](../standard-library/allocator-traits-class.md)<br/>
