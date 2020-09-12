---
title: '&lt;cstddef&gt;'
description: Opisuje <STDDEF. h>, co zapewnia, że nazwy zadeklarowane za pomocą zewnętrznego powiązania w nagłówku standardowej biblioteki C są deklarowane w `std` przestrzeni nazw.
ms.date: 9/4/2020
f1_keywords:
- <cstddef>
helpviewer_keywords:
- cstddef header
ms.assetid: be8d1e39-5974-41ee-b41d-eafa6c82ffce
ms.openlocfilehash: 186de0e893c413a25d31d4f1431c280d749e9541
ms.sourcegitcommit: 6280a4c629de0f638ebc2edd446de2a9b11f0406
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/12/2020
ms.locfileid: "90040031"
---
# <a name="ltcstddefgt"></a>&lt;cstddef&gt;

Zawiera nagłówek standardowej biblioteki C \<stddef.h> i dodaje skojarzone nazwy do `std` przestrzeni nazw. Dołączenie tego nagłówka zapewnia, że nazwy zadeklarowane za pomocą zewnętrznego powiązania w nagłówku standardowej biblioteki C są deklarowane w `std` przestrzeni nazw.

> [!NOTE]
> \<cstddef> obejmuje typ **Byte** i nie zawiera typu **`wchar_t`** .

## <a name="syntax"></a>Składnia

```cpp
#include <cstddef>
```

## <a name="namespace-and-macros"></a>Przestrzeń nazw i makra

```cpp
namespace std {
    using ptrdiff_t = see definition;
    using size_t = see definition;
    using max_align_t = see definition;
    using nullptr_t = decltype(nullptr);
}

#define NULL  // an implementation-defined null pointer constant
#define offsetof(type, member-designator)
```

### <a name="parameters"></a>Parametry

*ptrdiff_t*\
Zdefiniowany przez implementację typ Integer ze znakiem, który może zawierać różnicę dwóch indeksów dolnych w obiekcie array.

*size_t*\
Zdefiniowany w implementacji typ liczby całkowitej bez znaku, który jest wystarczająco duży, aby można było zawierać rozmiar w bajtach dowolnego obiektu.

*max_align_t*\
Typ POD, którego wymaganie wyrównania jest co najmniej tak duże, jak każdy typ skalarny, i którego wymaganie wyrównania jest obsługiwane w każdym kontekście.

*nullptr_t*\
Synonim dla typu **`nullptr`** wyrażenia. Chociaż **`nullptr`** nie można pobrać adresu, można wykonać adres innego *nullptr_t* obiektu, który jest lvalue.

## <a name="byte-class"></a>Byte — Klasa

```cpp
enum class byte : unsigned char {};

template <class IntType>
    constexpr byte& operator<<=(byte& b, IntType shift) noexcept;
    constexpr byte operator<<(byte b, IntType shift) noexcept;
    constexpr byte& operator>>=(byte& b, IntType shift) noexcept;
    constexpr byte operator>>(byte b, IntType shift) noexcept;

constexpr byte& operator|=(byte& left, byte right) noexcept;
constexpr byte operator|(byte left, byte right) noexcept;
constexpr byte& operator&=(byte& left, byte right) noexcept;
constexpr byte operator&(byte left, byte right) noexcept;
constexpr byte& operator^=(byte& left, byte right) noexcept;
constexpr byte operator^(byte left, byte right) noexcept;
constexpr byte operator~(byte b) noexcept;

template <class IntType>
    IntType to_integer(byte b) noexcept;
```

## <a name="see-also"></a>Zobacz także

[Dokumentacja plików nagłówkowych](../standard-library/cpp-standard-library-header-files.md)\
[Omówienie standardowej biblioteki języka C++](../standard-library/cpp-standard-library-overview.md)\
[Bezpieczeństwo wątku w standardowej bibliotece języka C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)
