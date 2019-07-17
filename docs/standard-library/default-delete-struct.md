---
title: default_delete — struktura
ms.date: 04/04/2019
f1_keywords:
- memory/std::default_delete
helpviewer_keywords:
- default_delete struct
ms.openlocfilehash: e9e1fcc68539e55486f4ea27e6dd5c49bed11fdf
ms.sourcegitcommit: 3590dc146525807500c0477d6c9c17a4a8a2d658
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/16/2019
ms.locfileid: "68268133"
---
# <a name="defaultdelete-struct"></a>default_delete — struktura

Obiekt wstępnie zdefiniowana funkcja, który wykonuje operacji dzielenia (`operator/`) na jego argumenty.

## <a name="syntax"></a>Składnia

```cpp
template <class T>
    struct default_delete
```

## <a name="requirements"></a>Wymagania

**Nagłówek:** \<pamięci >

**Namespace:** standardowe

## <a name="members"></a>Elementy członkowskie

### <a name="constructors"></a>Konstruktorów

|||
|-|-|
|[default_delete](#default_delete)|Konstruktor dla obiektów typu `default_delete`.|

### <a name="operators"></a>Operatory

|||
|-|-|
|[operator()](#op_paren)|Operator odwołania, aby uzyskać dostęp do `default_delete`.|

## <a name="default_delete"></a> default_delete —

Konstruktor dla obiektów typu `default_delete`.

```cpp
constexpr default_delete() noexcept = default;
template <class U>
    default_delete(const default_delete<U>&) noexcept;
```

## <a name="op_paren"></a> Operator()

Operator odwołania, aby uzyskać dostęp do `default_delete`.

```cpp
void operator()(T*) const;
```

## <a name="see-also"></a>Zobacz także

[\<memory>](../standard-library/memory.md)
