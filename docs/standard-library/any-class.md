---
title: dowolna klasa
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
ms.openlocfilehash: 66e74a7fa7f35aae9ac9e1f3ba7520e8d3f9b3f2
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/27/2020
ms.locfileid: "87203965"
---
# <a name="any-class"></a>dowolna klasa

Przechowuje wystąpienie dowolnego typu spełniające wymagania konstruktora lub nie ma wartości, która jest nazywana stanem klasy dowolnego obiektu.

Przechowywane wystąpienie jest nazywane zawartej wartości. Dwa stany są takie same, jeśli oba te osoby nie mają wartości lub obie mają wartość, a zawarte w niej wartości są takie same.

## <a name="syntax"></a>Składnia

```cpp
class any
```

## <a name="members"></a>Elementy członkowskie

### <a name="constructors"></a>Konstruktory

|||
|-|-|
|[ile](#any)|Konstruuje obiekt typu `any` .|

### <a name="functions"></a>Funkcje

|||
|-|-|
|[emplace](#emplace)|Ustawia dowolną wartość.|
|[has_value](#has_value)|Zwraca **`true`** wartość, jeśli jakakolwiek z nich jest wartością.|
|[zresetować](#reset)|Resetuje dowolny.|
|[wymiany](#swap)|Zamienia dwa obiekty.|
|[Wprowadź](#type)|Zwraca dowolny typ.|

### <a name="operators"></a>Operatory

|||
|-|-|
|[operator =](#op_eq)|Zastępuje wszystkie pozostałe.|

## <a name="any"></a><a name="any"></a>ile

Konstruuje obiekt typu `any` . Zawiera również destruktor.

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

## <a name="emplace"></a><a name="emplace"></a>emplace

Ustawia dowolną wartość.

```cpp
template <class T, class... Args>
    decay_t<T>& emplace(Args&& ...);
template <class T, class U, class... Args>
    decay_t<T>& emplace(initializer_list<U>, Args&&...);
```

## <a name="has_value"></a><a name="has_value"></a>has_value

Zwraca **`true`** wartość, jeśli jakakolwiek z nich jest wartością.

```cpp
bool has_value() const noexcept;
```

## <a name="operator"></a><a name="op_eq"></a>operator =

Zastępuje wszystkie pozostałe.

```cpp
any& operator=(const any& right);
any& operator=(any&& right) noexcept;
template <class T>
    any& operator=(T&& right);
```

### <a name="parameters"></a>Parametry

*Kliknij*\
Wszystkie są kopiowane do dowolnego.

## <a name="reset"></a><a name="reset"></a>zresetować

Resetuje dowolny.

```cpp
void reset() noexcept;
```

## <a name="swap"></a><a name="swap"></a>wymiany

Zamienia dwa obiekty.

```cpp
void swap(any& rhs) noexcept;
```

## <a name="type"></a><a name="type"></a>Wprowadź

Zwraca dowolny typ.

```cpp
const type_info& type() const noexcept;
```
