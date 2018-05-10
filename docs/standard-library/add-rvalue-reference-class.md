---
title: add_rvalue_reference — klasa | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
f1_keywords:
- type_traits/std::add_rvalue_reference
dev_langs:
- C++
helpviewer_keywords:
- add_rvalue_reference Class
ms.assetid: 76b0cb7c-1031-45d0-b409-f03ab0297580
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 1cceec4e7d954e07e1d776042f311dfa1a386300
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/07/2018
---
# <a name="addrvaluereference-class"></a>add_rvalue_reference — klasa

Tworzy typ referencyjny wartościowany prawostronnie parametru szablonu, jeśli jest to typ obiektu lub funkcji. W przeciwnym razie ze względu na semantykę odwołania zwijanie typ jest taki sam, jak parametr szablonu.

## <a name="syntax"></a>Składnia

```cpp
template <class T>
struct add_rvalue_reference;

template <class T>
using add_rvalue_reference_t = typename add_rvalue_reference<T>::type;
```

### <a name="parameters"></a>Parametry

T typu do zmodyfikowania.

## <a name="remarks"></a>Uwagi

`add_rvalue_reference` Klasa ma element członkowski o nazwie `type`, która jest alias dla typu odwołania do r-wartości na parametr szablonu `T`. Semantykę odwołania zwijanie oznacza, że dla typów innych niż obiekt i funkcji z systemem innym niż `T`, `T&&` jest `T`. Na przykład, jeśli `T` jest typem referencyjnym l-wartością `add_rvalue_reference<T>::type` jest typem referencyjnym l-wartość, nie odwołania do r-wartości.

Dla wygody \<type_traits > definiuje szablon Pomocnika `add_rvalue_reference_t`, że aliasy `type` członkiem `add_rvalue_reference`.

## <a name="example"></a>Przykład

W tym przykładzie kodu używane static_assert pokazanie, jak typy referencyjne wartościowania prawostronnego są tworzone za pomocą `add_rvalue_reference` i `add_rvalue_reference_t`i w jaki sposób wynik `add_rvalue_reference` na odwołania do wartości typu nie jest odwołaniem wartościowanym prawostronnie, ale zwija na typ referencyjny l-wartością.

```cpp
// ex_add_rvalue_reference.cpp
// Build by using: cl /EHsc /W4 ex_add_rvalue_reference.cpp
#include <type_traits>
#include <iostream>
#include <string>

using namespace std;
int main()
{
    static_assert(is_same<add_rvalue_reference<string>::type, string&&>::value,
        "Expected add_rvalue_reference_t<string> to be string&&");
    static_assert(is_same<add_rvalue_reference_t<string*>, string*&&>::value,
        "Expected add_rvalue_reference_t<string*> to be string*&&");
    static_assert(is_same<add_rvalue_reference<string&>::type, string&>::value,
        "Expected add_rvalue_reference_t<string&> to be string&");
    static_assert(is_same<add_rvalue_reference_t<string&&>, string&&>::value,
        "Expected add_rvalue_reference_t<string&&> to be string&&");
    cout << "All static_assert tests of add_rvalue_reference passed." << endl;
    return 0;
}

/*Output:
All static_assert tests of add_rvalue_reference passed.
*/
```

## <a name="requirements"></a>Wymagania

Nagłówek: < type_traits > Namespace: Standard

## <a name="see-also"></a>Zobacz także

[<type_traits>](../standard-library/type-traits.md)<br/>
[add_lvalue_reference, klasa](../standard-library/add-lvalue-reference-class.md)<br/>
[is_rvalue_reference, klasa](../standard-library/is-rvalue-reference-class.md)<br/>
