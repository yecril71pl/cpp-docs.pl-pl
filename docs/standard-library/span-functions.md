---
title: '&lt;&gt;funkcje span'
ms.date: 05/28/2020
f1_keywords:
- span/std::span::as_bytes
- span/std::as_writable_bytes
helpviewer_keywords:
- std::span [C++], as_writable_bytes
- std::as_bytes [C++]
ms.openlocfilehash: 6573ea061673091113244ada0ab0cd84bdd7db75
ms.sourcegitcommit: 1a8fac06478da8bee1f6d70e25afbad94144af1a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/30/2020
ms.locfileid: "84226119"
---
# <a name="ltspangt-functions"></a>&lt;&gt;funkcje span

\<span>Nagłówek zawiera następujące funkcje, które nie są elementami członkowskimi, które działają na obiektach **span** .

| **Funkcje nieczłonkowskie** | **Opis** |
|-|-|
|[as_bytes](#as_bytes) | Pobierz widok tylko do odczytu dla reprezentacji elementów w zakresie. |
|[as_writable_bytes](#as_writable_bytes) | Pobierz widok do odczytu/zapisu dla reprezentacji elementów w zakresie. |

## <a name="as_bytes"></a>`as_bytes`

Pobierz widok tylko do odczytu dla reprezentacji elementów w zakresie.

```cpp
template <class T, size_t Extent>
auto as_bytes(span<T, Extent> s) noexcept;
```

### <a name="parameters"></a>Parametry

*&*\
Typ elementów w zakresie.

*Rozmiaru*\
Liczba elementów w zakresie (jeśli jest znana w czasie kompilacji), w przeciwnym razie `dynamic_extent` wskazuje, że liczba elementów nie jest znana do czasu wykonania.

*wolumin*\
Zakres do pobrania nieprzetworzonej reprezentacji.

### <a name="return-value"></a>Wartość zwracana

`span<const byte, S>`Do pierwszego elementu przechowywanego w zakresie, gdzie `S` jest`{reinterpret_cast<const std::byte*>(s.data()), s.size_bytes()}`

### <a name="example"></a>Przykład

```cpp
#include <span>
#include <iostream>

using namespace std;

void main()
{
    int a[] = { 0,1,2 };
    span <int> mySpan(a);
    auto bytes = std::as_bytes(mySpan);
}
```

## <a name="as_writable_bytes"></a>`as_writable_bytes`

Jeśli `T` nie jest `const` , pobiera widok do odczytu/zapisu dla reprezentacji nieprzetworzonego bajtu elementów w zakresie.

```cpp
template <class T, size_t Extent>
auto as_writable_bytes(span<T, Extent> s) noexcept;
```

### <a name="parameters"></a>Parametry

*&*\
Typ elementów w zakresie.

*Rozmiaru*\
Liczba elementów w zakresie (jeśli jest znana w czasie kompilacji), w przeciwnym razie `dynamic_extent` wskazuje, że liczba elementów nie jest znana do czasu wykonania.

*wolumin*\
Zakres do pobrania nieprzetworzonej reprezentacji.

### <a name="return-value"></a>Wartość zwracana

`span<byte, S>`Do pierwszego elementu przechowywanego w zakresie, gdzie `S` jest`{reinterpret_cast<std::byte*>(s.data()), s.size_bytes()}`

### <a name="example"></a>Przykład

```cpp
#include <span>
#include <iostream>

using namespace std;

void main()
{
    int a[] = { 0,1,2 };
    span <int> mySpan(a);
    auto bytes = as_writable_bytes(mySpan);
}
```

## <a name="see-also"></a>Zobacz także

[\<span>](span.md)
