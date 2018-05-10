---
title: pointer_traits — struktura | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
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
dev_langs:
- C++
ms.assetid: 545aecf1-3561-4859-8b34-603c079fe1b3
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: d1485441dbea92f534314dafd9d86ab0ef8a4e69
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/08/2018
---
# <a name="pointertraits-struct"></a>pointer_traits — struktura

Dostarcza informacje, które są wymagane przez obiekt klasy szablonu `allocator_traits` do opisywania alokatora z typu wskaźnika `Ptr`.

## <a name="syntax"></a>Składnia

```cpp
template <class Ptr>
struct pointer_traits;
```

## <a name="remarks"></a>Uwagi

PTR można raw wskaźnika typu `Ty *` lub klasie z następujących właściwości.

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
|`typedef T2 difference_type`|Typ `T2` jest `Ptr::difference_type` Jeśli istnieje tego typu, w przeciwnym razie `ptrdiff_t`. Jeśli `Ptr` raw wskaźnik jest typu `ptrdiff_t`.|
|`typedef T1 element_type`|Typ `T1` jest `Ptr::element_type` Jeśli istnieje tego typu, w przeciwnym razie `Ty`. Jeśli `Ptr` raw wskaźnik jest typu `Ty`.|
|`typedef Ptr pointer`|Typ jest `Ptr`.|

### <a name="structs"></a>Struktury

|Nazwa|Opis|
|----------|-----------------|
|`pointer_traits::rebind`|Typ próbuje przekonwertować podstawowy wskaźnik do określonego typu.|

### <a name="methods"></a>Metody

|Nazwa|Opis|
|----------|-----------------|
|[pointer_to](#pointer_to)|Konwertuje dowolną odwołaniem do obiektu klasy `Ptr`.|

## <a name="requirements"></a>Wymagania

**Nagłówek:** \<pamięci >

**Namespace:** Standard

## <a name="pointer_to"></a>  pointer_to

Statyczna metoda, która zwraca `Ptr::pointer_to(obj)`, jeśli istnieje tej funkcji. W przeciwnym razie nie jest możliwe do przekonwertowania dowolną odwołaniem do obiektu klasy `Ptr`. Jeśli `Ptr` jest wskaźnik raw, ta metoda zwraca `addressof(obj)`.

```cpp
static pointer pointer_to(element_type& obj);
```

## <a name="see-also"></a>Zobacz także

[\<memory>](../standard-library/memory.md)<br/>
[allocator_traits, klasa](../standard-library/allocator-traits-class.md)<br/>
