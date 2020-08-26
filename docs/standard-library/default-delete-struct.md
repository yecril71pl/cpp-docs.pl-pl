---
title: Struktura default_delete
ms.date: 04/04/2019
f1_keywords:
- memory/std::default_delete
helpviewer_keywords:
- default_delete struct
ms.openlocfilehash: 8baa9f5d294cf083fd55414cd529e438f328d1a1
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/25/2020
ms.locfileid: "88845084"
---
# <a name="default_delete-struct"></a>Struktura default_delete

Wstępnie zdefiniowany obiekt funkcji, który wykonuje operację dzielenia ( `operator/` ) dla jej argumentów.

## <a name="syntax"></a>Składnia

```cpp
template <class T>
    struct default_delete
```

## <a name="requirements"></a>Wymagania

**Nagłówek:**\<memory>

**Przestrzeń nazw:** std

## <a name="members"></a>Elementy członkowskie

### <a name="constructors"></a>Konstruktory

|Nazwa|Opis|
|-|-|
|[default_delete](#default_delete)|Konstruktor dla obiektów typu `default_delete` .|

### <a name="operators"></a>Operatory

|Nazwa|Opis|
|-|-|
|[operator ()](#op_paren)|Operator odwołania, do którego można uzyskać dostęp `default_delete` .|

## <a name="default_delete"></a><a name="default_delete"></a> default_delete

Konstruktor dla obiektów typu `default_delete` .

```cpp
constexpr default_delete() noexcept = default;
template <class U>
    default_delete(const default_delete<U>&) noexcept;
```

## <a name="operator"></a><a name="op_paren"></a> operator ()

Operator odwołania, do którego można uzyskać dostęp `default_delete` .

```cpp
void operator()(T*) const;
```

## <a name="see-also"></a>Zobacz też

[\<memory>](../standard-library/memory.md)
