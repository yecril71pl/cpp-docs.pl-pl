---
title: Wariant klasy
ms.date: 04/04/2019
f1_keywords:
- variant/std::variant
- variant/std::variant::emplace
- variant/std::variant::index
- variant/std::variant::valueless_by_exception
helpviewer_keywords:
- variant/std::variant
- variant/std::variant::emplace
- variant/std::variant::index
- variant/std::variant::valueless_by_exception
ms.openlocfilehash: 9bfdf644374a0b825fd0ca02bf4164a766cb42a3
ms.sourcegitcommit: 3590dc146525807500c0477d6c9c17a4a8a2d658
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/16/2019
ms.locfileid: "68268145"
---
# <a name="variant-class"></a>Wariant klasy

Dowolne wystąpienie wariant w danym momencie albo przechowuje wartość jednego z jej typów alternatywnych lub przechowuje żadnej wartości.

## <a name="syntax"></a>Składnia

```cpp
template <class... Types>
    class variant
```

## <a name="members"></a>Elementy członkowskie

### <a name="constructors"></a>Konstruktorów

|||
|-|-|
|[Variant](#variant)|Tworzy obiekt typu `variant`.|

### <a name="functions"></a>Funkcje

|||
|-|-|
|[emplace —](#emplace)|Tworzy nową wartość zawartych.|
|[index](#index)|Zwraca indeks wartości zawartych.|
|[swap](#swap)||
|[valueless_by_exception](#emplace)|Zwraca **false** Jeśli wariant przechowuje wartość.|

### <a name="operators"></a>Operatory

|||
|-|-|
|[operator=](#op_eq)|Zastępuje kopię inny wariant wariant.|

## <a name="emplace"></a> emplace —

Tworzy nową wartość zawartych.

```cpp
template <class T, class... Args>
    T& emplace(Args&&...);
template <class T, class U, class... Args>
    T& emplace(initializer_list<U>, Args&&...);
template <size_t I, class... Args>
    variant_alternative_t<I, variant<Types...>>& emplace(Args&&...);
template <size_t I, class U, class... Args>
    variant_alternative_t<I, variant<Types...>>& emplace(initializer_list<U>, Args&&...);
```

## <a name="index"></a> Indeks

Zwraca indeks wartości zawartych.

```cpp
constexpr size_t index() const noexcept;
```

## <a name="variant"></a> Variant

Tworzy obiekt typu `variant`. Zawiera także destruktora.

```cpp
constexpr variant() noexcept(see below);
variant(const variant&);
variant(variant&&) noexcept(see below);
template <class T>
    constexpr variant(T&&) noexcept(see below);
template <class T, class... Args>
    constexpr explicit variant(in_place_type_t<T>, Args&&...);
template <class T, class U, class... Args>
    constexpr explicit variant(in_place_type_t<T>, initializer_list<U>, Args&&...);
template <size_t I, class... Args>
    constexpr explicit variant(in_place_index_t<I>, Args&&...);
template <size_t I, class U, class... Args>
    constexpr explicit variant(in_place_index_t<I>, initializer_list<U>, Args&&...);

template <class Alloc>
    variant(allocator_arg_t, const Al&);
template <class Alloc>
    variant(allocator_arg_t, const Al&, const variant&);
template <class Alloc>
    variant(allocator_arg_t, const Al&, variant&&);
template <class Alloc, class T>
    variant(allocator_arg_t, const Al&, T&&);
template <class Alloc, class T, class... Args>
    variant(allocator_arg_t, const Al&, in_place_type_t<T>, Args&&...);
template <class Alloc, class T, class U, class... Args>
    variant(allocator_arg_t, const Al&, in_place_type_t<T>, initializer_list<U>, Args&&...);
template <class Alloc, size_t I, class... Args>
    variant(allocator_arg_t, const Al&, in_place_index_t<I>, Args&&...);
template <class Alloc, size_t I, class U, class... Args>
    variant(allocator_arg_t, const Al&, in_place_index_t<I>, initializer_list<U>, Args&&...);

~variant();
```

### <a name="parameters"></a>Parametry

*Al*\
Klasa alokatora do wykorzystania z tym obiektem.

## <a name="op_eq"></a> operator =

Zastępuje kopię inny wariant wariant.

```cpp
variant& operator=(const variant&);
variant& operator=(variant&&) noexcept(see below);
template <class T>
    variant& operator=(T&&) noexcept(see below);
```

## <a name="swap"></a> swap

```cpp
void swap(variant&) noexcept(see below);
```

## <a name="valueless"></a> valueless_by_exception

Zwraca **false** Jeśli wariant przechowuje wartość.

```cpp
constexpr bool valueless_by_exception() const noexcept;
```
