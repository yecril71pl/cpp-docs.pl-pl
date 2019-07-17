---
title: '&lt;cstddef&gt;'
ms.date: 11/04/2016
f1_keywords:
- <cstddef>
helpviewer_keywords:
- cstddef header
ms.assetid: be8d1e39-5974-41ee-b41d-eafa6c82ffce
ms.openlocfilehash: 15d13a3af35cb41950df8aeba0c86d779e701ddb
ms.sourcegitcommit: 3590dc146525807500c0477d6c9c17a4a8a2d658
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/16/2019
ms.locfileid: "68244451"
---
# <a name="ltcstddefgt"></a>&lt;cstddef&gt;

Dołącza nagłówek biblioteki standardowej C \<stddef.h > i dodaje skojarzone nazwy `std` przestrzeni nazw. Dołączenie tego pliku nagłówkowego gwarantuje również, że nazwy zadeklarowane za pomocą zewnętrznego powiązania w nagłówku standardowej biblioteki C są deklarowane w `std` przestrzeni nazw.

> [!NOTE]
> \<cstddef — > zawiera typ **bajtów** i nie zawiera typu **wchar_t**.

## <a name="syntax"></a>Składnia

```cpp
#include <cstddef>
```

## <a name="namespace-and-macros"></a>Makra i Namespace

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

*ptrdiff_t —* \
Zdefiniowane w implementacji podpisany typ całkowitoliczbowy, który może pomieścić różnica dwóch indeksy dolne tablicy obiektów.

*size_t*\
Typ zdefiniowanych w implementacji liczb całkowitych bez znaku, który jest wystarczająco duży, aby zawierać rozmiar w bajtach każdego obiektu.

*max_align_t*\
Typem POD, którego wymóg wyrównania jest przynajmniej tak duży jak w przypadku wszystkich typów skalarnych i którego wymóg wyrównania jest obsługiwana w każdym kontekście.

*nullptr_t*\
Synonim dla typu **nullptr** wyrażenia. Mimo że **nullptr** adresu nie może być przyjęty, adresu innego *nullptr_t* obiekt, który jest l-wartości, które mogą być podejmowane.

## <a name="byte-class"></a>Byte, klasa

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

[Odwołanie do plików nagłówkowych](../standard-library/cpp-standard-library-header-files.md)<br/>
[Standardowa biblioteka C++ — przegląd](../standard-library/cpp-standard-library-overview.md)<br/>
[Bezpieczeństwo wątku w standardowej bibliotece C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)<br/>
