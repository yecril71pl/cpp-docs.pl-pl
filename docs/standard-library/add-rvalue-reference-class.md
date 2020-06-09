---
title: add_rvalue_reference — klasa
ms.date: 11/04/2016
f1_keywords:
- type_traits/std::add_rvalue_reference
helpviewer_keywords:
- add_rvalue_reference Class
ms.assetid: 76b0cb7c-1031-45d0-b409-f03ab0297580
ms.openlocfilehash: 6d7cc1d45ed3b963de0a0a004c1696ddbf0af440
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/09/2020
ms.locfileid: "84623916"
---
# <a name="add_rvalue_reference-class"></a>add_rvalue_reference — klasa

Tworzy typ odwołania rvalue dla parametru szablonu, jeśli jest typem obiektu lub funkcji. W przeciwnym razie, ze względu na semantykę zwijania odwołania, typ jest taki sam jak parametr szablonu.

## <a name="syntax"></a>Składnia

```cpp
template <class T>
struct add_rvalue_reference;

template <class T>
using add_rvalue_reference_t = typename add_rvalue_reference<T>::type;
```

### <a name="parameters"></a>Parametry

*&*\
Typ do modyfikacji.

## <a name="remarks"></a>Uwagi

`add_rvalue_reference`Klasa ma element członkowski o nazwie `type` , który jest aliasem dla typu odwołania rvalue do parametru szablonu *T*. Semantyka zwijania odwołania oznacza, że dla typu niebędącego obiektem i nienależącym do funkcji *t*, `T&&` to *t*. Na przykład, jeśli *T* jest typem odwołania lvalue, `add_rvalue_reference<T>::type` jest typem referencyjnym lvalue, a nie odwołaniem rvalue.

Dla wygody \<type_traits> definiuje szablon pomocnika, `add_rvalue_reference_t` który aliasuje `type` element członkowski `add_rvalue_reference` .

## <a name="example"></a>Przykład

W poniższym przykładzie kodu użyto static_assert, aby pokazać, jak typy odwołań rvalue są tworzone za pomocą `add_rvalue_reference` i `add_rvalue_reference_t` , oraz jak wynik `add_rvalue_reference` dla typu odwołania lvalue nie jest odwołaniem rvalue, ale jest zwijany do typu odwołania lvalue.

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

Nagłówki\<type_traits>

Przestrzeń nazw: std

## <a name="see-also"></a>Zobacz też

[<type_traits>](type-traits.md)\
[Klasa add_lvalue_reference](add-lvalue-reference-class.md)\
[Klasa is_rvalue_reference](is-rvalue-reference-class.md)
