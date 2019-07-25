---
title: '&lt;cstddef&gt;'
ms.date: 11/04/2016
f1_keywords:
- <cstddef>
helpviewer_keywords:
- cstddef header
ms.assetid: be8d1e39-5974-41ee-b41d-eafa6c82ffce
ms.openlocfilehash: 87d268977ee46112fedce517e66a9e68071863db
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/24/2019
ms.locfileid: "68457574"
---
# <a name="ltcstddefgt"></a>&lt;cstddef&gt;

Zawiera nagłówek \<standardowej biblioteki C STDDEF. h > i dodaje skojarzone nazwy `std` do przestrzeni nazw. Dołączenie tego nagłówka zapewnia, że nazwy zadeklarowane za pomocą zewnętrznego powiązania w nagłówku standardowej biblioteki C są `std` deklarowane w przestrzeni nazw.

> [!NOTE]
> \<cstddef > obejmuje typ **Byte** i nie zawiera typu **wchar_t**.

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
Synonim dla typu wyrażenia **nullptr** . Mimo że nie można pobrać adresu **nullptr** , można wykonać adres innego obiektu *nullptr_t* , który jest lvalue.

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
[C++Omówienie biblioteki standardowej](../standard-library/cpp-standard-library-overview.md)\
[Bezpieczeństwo wątku w standardowej bibliotece C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)
