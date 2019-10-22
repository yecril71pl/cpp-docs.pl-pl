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
ms.openlocfilehash: 6d89348867982bfb86c0bf2404a017f6a448d1a1
ms.sourcegitcommit: 590e488e51389066a4da4aa06d32d4c362c23393
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/21/2019
ms.locfileid: "72687138"
---
# <a name="pointer_traits-struct"></a>pointer_traits — struktura

Dostarcza informacje, które są konieczne przez obiekt typu `allocator_traits` do opisania alokatora z typem wskaźnika `Ptr`.

## <a name="syntax"></a>Składnia

```cpp
template <class Ptr>
    struct pointer_traits;
```

## <a name="remarks"></a>Uwagi

PTR może być nieprzetworzonym wskaźnikiem typu `Ty *` lub klasy z następującymi właściwościami.

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
|`typedef T2 difference_type`|Typ `T2` jest `Ptr::difference_type`, jeśli ten typ istnieje, w przeciwnym razie `ptrdiff_t`. Jeśli `Ptr` jest wskaźnikiem nieprzetworzonym, typ jest `ptrdiff_t`.|
|`typedef T1 element_type`|Typ `T1` jest `Ptr::element_type`, jeśli ten typ istnieje, w przeciwnym razie `Ty`. Jeśli `Ptr` jest wskaźnikiem nieprzetworzonym, typ jest `Ty`.|
|`typedef Ptr pointer`|Typ jest `Ptr`.|

### <a name="structs"></a>Struktury

|||
|-|-|
|`rebind`|Próbuje skonwertować podstawowy typ wskaźnika do określonego typu.|

### <a name="methods"></a>Metody

|Nazwa|Opis|
|----------|-----------------|
|[pointer_to](#pointer_to)|Konwertuje arbitralne odwołanie do obiektu klasy `Ptr`.|

### <a name="pointer_to"></a>pointer_to

Metoda statyczna zwracająca `Ptr::pointer_to(obj)`, jeśli ta funkcja istnieje. W przeciwnym razie nie jest możliwe przekonwertowanie dowolnego odwołania do obiektu klasy `Ptr`. Jeśli `Ptr` jest wskaźnikiem surowym, ta metoda zwraca `addressof(obj)`.

```cpp
static pointer pointer_to(element_type& obj);
```
