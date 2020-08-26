---
title: Klasa Variant
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
ms.openlocfilehash: aba121604636ebd253523acb9b630dd9ab762584
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/25/2020
ms.locfileid: "88840027"
---
# <a name="variant-class"></a>Klasa Variant

Każde wystąpienie wariantu w dowolnym momencie zawiera wartość jednego z jego typów alternatywnych lub nie ma żadnej wartości.

## <a name="syntax"></a>Składnia

```cpp
template <class... Types>
    class variant
```

## <a name="members"></a>Elementy członkowskie

### <a name="constructors"></a>Konstruktory

|Nazwa|Opis|
|-|-|
|[typu](#variant)|Konstruuje obiekt typu `variant` .|

### <a name="functions"></a>Functions

|Nazwa|Opis|
|-|-|
|[emplace](#emplace)|Tworzy nową wartość zawartej.|
|[index](#index)|Zwraca indeks zawartej wartości.|
|[wymiany](#swap)||
|[valueless_by_exception](#emplace)|Zwraca **`false`** czy wariant ma wartość.|

### <a name="operators"></a>Operatory

|Nazwa|Opis|
|-|-|
|[operator =](#op_eq)|Zastępuje wariant z kopią innego wariantu.|

## <a name="emplace"></a><a name="emplace"></a> emplace

Tworzy nową wartość zawartej.

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

## <a name="index"></a><a name="index"></a> indeks

Zwraca indeks zawartej wartości.

```cpp
constexpr size_t index() const noexcept;
```

## <a name="variant"></a><a name="variant"></a> typu

Konstruuje obiekt typu `variant` . Zawiera również destruktor.

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

*Wsp*\
Klasa alokatora do wykorzystania z tym obiektem.

## <a name="operator"></a><a name="op_eq"></a> operator =

Zastępuje wariant z kopią innego wariantu.

```cpp
variant& operator=(const variant&);
variant& operator=(variant&&) noexcept(see below);
template <class T>
    variant& operator=(T&&) noexcept(see below);
```

## <a name="swap"></a><a name="swap"></a> wymiany

```cpp
void swap(variant&) noexcept(see below);
```

## <a name="valueless_by_exception"></a><a name="valueless"></a> valueless_by_exception

Zwraca **`false`** czy wariant ma wartość.

```cpp
constexpr bool valueless_by_exception() const noexcept;
```
