---
title: is_pod — Klasa
ms.date: 11/04/2016
f1_keywords:
- type_traits/std::is_pod
helpviewer_keywords:
- is_pod class
- is_pod
ms.assetid: d73ebdee-746b-4082-9fa4-2db71432eb0e
ms.openlocfilehash: 3dff4650cf0337a5ff54065d3b1644e11008ecfe
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62413622"
---
# <a name="ispod-class"></a>is_pod — Klasa

Sprawdza, czy typ jest ZASOBNIKÓW.

## <a name="syntax"></a>Składnia

```cpp
template <class T>
struct is_pod;
```

### <a name="parameters"></a>Parametry

*T*<br/>
Typ do zapytania.

## <a name="remarks"></a>Uwagi

`is_pod<T>::value` jest **true** Jeśli typ *T* to zwykłe stare dane (POD). W przeciwnym razie jest **false**.

Arytmetyczne typy, Typy wyliczeniowe, typy wskaźników i wskaźnik na typy Członkowskie są ZASOBNIKÓW.

Kwalifikowana cv wersji typu ZASOBNIKA jest typem POD.

Tablica ZASOBNIKA jest ZASOBNIKÓW.

Struktury lub Unii, są wszystkie których elementy członkowskie danych niestatycznych ZASOBNIKÓW, sama jest ZASOBNIKA jeśli ma ona:

- Zgłoszone przez użytkownika konstruktorów.

- Nie prywatnych lub chronionych niestatycznych składowych danych.

- Nie mają klas bazowych.

- Żadnych funkcji wirtualnych.

- Nie niestatycznych elementów członkowskich danych typu referencyjnego.

- Żaden operator przypisywania kopiowania zdefiniowanych przez użytkownika.

- Nie destruktor zdefiniowany przez użytkownika.

W związku z tym można rekursywnie kompilacji POD struktur i tablic, które zawierają ZASOBNIKA struktur i tablic.

## <a name="example"></a>Przykład

```cpp
// std__type_traits__is_pod.cpp
// compile with: /EHsc
#include <type_traits>
#include <iostream>

struct trivial {
    int val;
};

struct throws {
    throws() {}  // User-declared ctor, so not POD

    int val;
};

int main() {
    std::cout << "is_pod<trivial> == " << std::boolalpha
        << std::is_pod<trivial>::value << std::endl;
    std::cout << "is_pod<int> == " << std::boolalpha
        << std::is_pod<int>::value << std::endl;
    std::cout << "is_pod<throws> == " << std::boolalpha
        << std::is_pod<throws>::value << std::endl;

    return (0);
}
```

```Output
is_pod<trivial> == true
is_pod<int> == true
is_pod<throws> == false
```

## <a name="requirements"></a>Wymagania

**Nagłówek:** \<type_traits >

**Namespace:** standardowe

## <a name="see-also"></a>Zobacz także

[<type_traits>](../standard-library/type-traits.md)<br/>
