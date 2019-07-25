---
title: is_pod — Klasa
ms.date: 11/04/2016
f1_keywords:
- type_traits/std::is_pod
helpviewer_keywords:
- is_pod class
- is_pod
ms.assetid: d73ebdee-746b-4082-9fa4-2db71432eb0e
ms.openlocfilehash: 1249e9a3689d4b91334e545ba294c28984898035
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/24/2019
ms.locfileid: "68455762"
---
# <a name="ispod-class"></a>is_pod — Klasa

Testuje, czy typ jest POD.

## <a name="syntax"></a>Składnia

```cpp
template <class T>
struct is_pod;
```

### <a name="parameters"></a>Parametry

*&* \
Typ do zapytania.

## <a name="remarks"></a>Uwagi

`is_pod<T>::value`ma **wartość true** , jeśli typ *T* jest zwykłymi danymi (pod). W przeciwnym razie ma **wartość false**.

Typy arytmetyczne, typy wyliczeniowe, typy wskaźników i wskaźniki do typów elementów członkowskich są poniżej.

Kwalifikowana dla CV wersja typu POD jest sama typem POD.

Tablica POD jest sama POD.

Struktura lub Unia, dla której wszystkie niestatyczne składowe danych znajdują się na poziomie, jest sama POD, jeśli ma:

- Brak konstruktorów zadeklarowanych przez użytkownika.

- Brak prywatnych lub chronionych niestatycznych elementów członkowskich danych.

- Nie mają klas bazowych.

- Brak funkcji wirtualnych.

- Brak niestatycznych elementów członkowskich danych typu referencyjnego.

- Brak zdefiniowanego przez użytkownika operatora przypisania kopiowania.

- Brak destruktora zdefiniowanego przez użytkownika.

W związku z tym można rekursywnie kompilować struktury i tablice, które zawierają POD struktury i tablice.

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

**Przestrzeń nazw:** std

## <a name="see-also"></a>Zobacz także

[<type_traits>](../standard-library/type-traits.md)
