---
title: add_rvalue_reference — klasa
ms.date: 11/04/2016
f1_keywords:
- type_traits/std::add_rvalue_reference
helpviewer_keywords:
- add_rvalue_reference Class
ms.assetid: 76b0cb7c-1031-45d0-b409-f03ab0297580
ms.openlocfilehash: 64694f2428c1dd536df4d242a17f3f011cfb290c
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/24/2019
ms.locfileid: "68456538"
---
# <a name="addrvaluereference-class"></a>add_rvalue_reference — klasa

Tworzy typ odwołania rvalue dla parametru szablonu, jeśli jest typem obiektu lub funkcji. W przeciwnym razie, ze względu na semantykę zwijania odwołania, typ jest taki sam jak parametr szablonu.

## <a name="syntax"></a>Składnia

```cpp
template <class T>
struct add_rvalue_reference;

template <class T>
using add_rvalue_reference_t = typename add_rvalue_reference<T>::type;
```

### <a name="parameters"></a>Parametry

*&* \
Typ do modyfikacji.

## <a name="remarks"></a>Uwagi

Klasa ma element członkowski o nazwie `type`, który jest aliasem dla typu odwołania rvalue do parametru szablonu *T.* `add_rvalue_reference` Semantyka zwijania odwołania oznacza, że dla typu niebędącego obiektem i nienależącym do funkcji t `T&&` , to *t*. Na przykład, jeśli *T* jest typem odwołania lvalue, `add_rvalue_reference<T>::type` jest typem referencyjnym lvalue, a nie odwołaniem rvalue.

Dla wygody \<type_traits > definiuje `add_rvalue_reference_t`szablon pomocnika, `add_rvalue_reference`który aliasuje `type` element członkowski.

## <a name="example"></a>Przykład

Ten przykład kodu używa static_assert, aby pokazać, jak rvalue typy odwołań są tworzone `add_rvalue_reference` za `add_rvalue_reference_t`pomocą i, `add_rvalue_reference` i w jaki sposób wynik dla typu odwołania lvalue nie jest odwołaniem rvalue, ale jest zwijany do typu odwołania lvalue.

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

Nagłówek: \<type_traits >

Przestrzeń nazw: std

## <a name="see-also"></a>Zobacz także

[< type_traits >](../standard-library/type-traits.md)\
[Klasa add_lvalue_reference](../standard-library/add-lvalue-reference-class.md)\
[is_rvalue_reference, klasa](../standard-library/is-rvalue-reference-class.md)
