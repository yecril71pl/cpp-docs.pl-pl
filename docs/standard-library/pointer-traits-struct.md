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
ms.openlocfilehash: 109e51ad9eba54f31b90da9b8b85bec105c7dce6
ms.sourcegitcommit: 3590dc146525807500c0477d6c9c17a4a8a2d658
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/16/2019
ms.locfileid: "68240428"
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
   static pointer pointer_to(element_type& obj); // optional
};
```

## <a name="members"></a>Elementy członkowskie

### <a name="typedefs"></a>Typedefs

|||
|-|-|
|`typedef T2 difference_type`|Typ `T2` jest `Ptr::difference_type` istnienia tego typu, w przeciwnym razie `ptrdiff_t`. Jeśli `Ptr` jest surowy wskaźnik jest typu `ptrdiff_t`.|
|`typedef T1 element_type`|Typ `T1` jest `Ptr::element_type` istnienia tego typu, w przeciwnym razie `Ty`. Jeśli `Ptr` jest surowy wskaźnik jest typu `Ty`.|
|`typedef Ptr pointer`|Typ jest `Ptr`.|

### <a name="structs"></a>Struktury

|||
|-|-|
|`rebind`|Próbuje przekonwertować podstawowego wskaźnika typu do określonego typu.|

### <a name="methods"></a>Metody

|Nazwa|Opis|
|----------|-----------------|
|[pointer_to](#pointer_to)|Konwertuje dowolnego odwołania do obiektu klasy `Ptr`.|

### <a name="pointer_to"></a> pointer_to

Metoda statyczna zwraca `Ptr::pointer_to(obj)`, jeśli istnieje w tej funkcji. W przeciwnym razie nie jest możliwe do przekonwertowania dowolnego odwołania do obiektu klasy `Ptr`. Jeśli `Ptr` jest surowy wskaźnik, Metoda ta zwraca `addressof(obj)`.

```cpp
static pointer pointer_to(element_type& obj);
```
