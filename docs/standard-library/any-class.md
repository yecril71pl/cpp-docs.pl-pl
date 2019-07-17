---
title: Każda klasa
ms.date: 04/04/2019
f1_keywords:
- any/std::any
- any/std::any::emplace
- any/std::any::has_value
- any/std::any::reset
- any/std::any::swap
- any/std::any::type
helpviewer_keywords:
- any/std::any
- any/std::any::emplace
- any/std::any::has_value
- any/std::any::reset
- any/std::any::swap
- any/std::any::type
ms.openlocfilehash: 050276da665ab6ed3eb53d9e65bfea06b88bcbea
ms.sourcegitcommit: 3590dc146525807500c0477d6c9c17a4a8a2d658
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/16/2019
ms.locfileid: "68267980"
---
# <a name="any-class"></a>Każda klasa

Magazyny wystąpienia dowolnego typu, który spełnia wymagania konstruktora lub nie ma wartości, która jest wywoływana stan klasy dowolnego obiektu.

Wystąpienie przechowywanych nosi nazwę zawartej wartość. Dwa stany są takie same, jeśli oba te produkty nie mają żadnej wartości lub mają wartości i wartości zawarte są takie same.

## <a name="syntax"></a>Składnia

```cpp
class any
```

## <a name="members"></a>Elementy członkowskie

### <a name="constructors"></a>Konstruktorów

|||
|-|-|
|[Wszystkie](#any)|Tworzy obiekt typu `any`.|

### <a name="functions"></a>Funkcje

|||
|-|-|
|[emplace —](#emplace)|Ustawia dowolną wartość.|
|[has_value](#has_value)|Zwraca **true** Jeśli którakolwiek z nich ma wartość.|
|[Resetuj](#reset)|Resetuje dowolne.|
|[swap](#swap)|Zamień dwa obiekty.|
|[type](#type)|Zwraca wartość dowolnego typu.|

### <a name="operators"></a>Operatory

|||
|-|-|
|[operator=](#op_eq)|Zastępuje wszelkie dowolny z kopią innego.|

## <a name="any"></a> Wszystkie

Tworzy obiekt typu `any`. Zawiera także destruktora.

```cpp
constexpr any() noexcept;
any(const any& other);
any(any&& other) noexcept;
template <class T>
    any(T&& value);
template <class T, class... Args>
    explicit any(in_place_type_t<T>, Args&&...);
template <class T, class U, class... Args>
    explicit any(in_place_type_t<T>, initializer_list<U>, Args&&...);

~any();
```

## <a name="emplace"></a> emplace —

Ustawia dowolną wartość.

```cpp
template <class T, class... Args>
    decay_t<T>& emplace(Args&& ...);
template <class T, class U, class... Args>
    decay_t<T>& emplace(initializer_list<U>, Args&&...);
```

## <a name="has_value"></a> has_value —

Zwraca **true** Jeśli którakolwiek z nich ma wartość.

```cpp
bool has_value() const noexcept;
```

## <a name="op_eq"></a> operator =

Zastępuje wszelkie dowolny z kopią innego.

```cpp
any& operator=(const any& right);
any& operator=(any&& right) noexcept;
template <class T>
    any& operator=(T&& right);
```

### <a name="parameters"></a>Parametry

*po prawej stronie*\
Wszystkie kopiowane do wszystkie.

## <a name="reset"></a> Resetuj

Resetuje dowolne.

```cpp
void reset() noexcept;
```

## <a name="swap"></a> swap

Zamień dwa obiekty.

```cpp
void swap(any& rhs) noexcept;
```

## <a name="type"></a> Typ

Zwraca wartość dowolnego typu.

```cpp
const type_info& type() const noexcept;
```
