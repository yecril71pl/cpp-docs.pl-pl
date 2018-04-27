---
title: is_pod — klasa | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: ''
ms.topic: reference
f1_keywords:
- type_traits/std::is_pod
dev_langs:
- C++
helpviewer_keywords:
- is_pod class
- is_pod
ms.assetid: d73ebdee-746b-4082-9fa4-2db71432eb0e
caps.latest.revision: 20
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: c6aeccf783ecd3914e69af8542ec3ef07bb9f084
ms.sourcegitcommit: dd1a509526fa8bb18e97ab7bc7b91cbdb3ec7059
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/26/2018
---
# <a name="ispod-class"></a>is_pod — Klasa

Testy, jeśli typ jest POD.

## <a name="syntax"></a>Składnia

```cpp
template <class T>
struct is_pod;
```

### <a name="parameters"></a>Parametry

*T* typ do zapytania.

## <a name="remarks"></a>Uwagi

`is_pod<T>::value` jest `true` Jeśli typ *T* jest zwykły stare dane (POD). W przeciwnym razie jest `false`.

Typów arytmetycznych, Typy wyliczeniowe typów wskaźnikowych i wskaźnika do elementu członkowskiego typy są POD.

Kwalifikowana cv wersji typ POD jest typ POD.

Tablica POD jest POD.

Struktura lub związek, w których elementy członkowskie danych niestatyczna są POD, jest POD jeśli ma ona:

- Nie konstruktorów zadeklarowanych przez użytkownika.

- Nie członków prywatnych lub chronionych danych niestatycznego.

- Nie mają klas bazowych.

- Nie funkcji wirtualnych.

- Nie niestatyczna elementy członkowskie danych typu referencyjnego.

- Nie operatora przypisania kopii zdefiniowane przez użytkownika.

- Nie ma destruktora zdefiniowane przez użytkownika.

W związku z tym można rekursywnie kompilacji POD struktury i tablic zawierających POD struktury i tablic.

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

**Namespace:** Standard

## <a name="see-also"></a>Zobacz także

[<type_traits>](../standard-library/type-traits.md)<br/>
