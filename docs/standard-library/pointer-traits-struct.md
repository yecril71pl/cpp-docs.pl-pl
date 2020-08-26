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
ms.openlocfilehash: 1ed8d61a52c11ab48fe6f762ff342ea88d107b14
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/25/2020
ms.locfileid: "88832701"
---
# <a name="pointer_traits-struct"></a>pointer_traits — struktura

Dostarcza informacje, które są konieczne przez obiekt typu `allocator_traits` do opisania alokatora z typem wskaźnika `Ptr` .

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

|Nazwa|Opis|
|-|-|
|`typedef T2 difference_type`|Typ `T2` to `Ptr::difference_type` , czy ten typ istnieje, w przeciwnym razie `ptrdiff_t` . Jeśli `Ptr` jest wskaźnikiem nieprzetworzonym, typem jest `ptrdiff_t` .|
|`typedef T1 element_type`|Typ `T1` to `Ptr::element_type` , czy ten typ istnieje, w przeciwnym razie `Ty` . Jeśli `Ptr` jest wskaźnikiem nieprzetworzonym, typem jest `Ty` .|
|`typedef Ptr pointer`|Typ to `Ptr` .|

### <a name="structs"></a>Struktury

|Nazwa|Opis|
|-|-|
|`rebind`|Próbuje skonwertować podstawowy typ wskaźnika do określonego typu.|

### <a name="methods"></a>Metody

|Nazwa|Opis|
|----------|-----------------|
|[pointer_to](#pointer_to)|Konwertuje arbitralne odwołanie do obiektu klasy `Ptr` .|

### <a name="pointer_to"></a><a name="pointer_to"></a> pointer_to

Metoda statyczna, która zwraca `Ptr::pointer_to(obj)` , jeśli ta funkcja istnieje. W przeciwnym razie nie jest możliwe przekonwertowanie dowolnego odwołania do obiektu klasy `Ptr` . Jeśli `Ptr` jest wskaźnikiem nieprzetworzonym, ta metoda zwraca `addressof(obj)` .

```cpp
static pointer pointer_to(element_type& obj);
```
