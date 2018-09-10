---
title: add_rvalue_reference, klasa | Dokumentacja firmy Microsoft
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
ms.openlocfilehash: a20a637872c8c26433920da313d4e6c001736d06
ms.sourcegitcommit: 761c5f7c506915f5a62ef3847714f43e9b815352
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/07/2018
ms.locfileid: "44105760"
---
# <a name="addrvaluereference-class"></a>add_rvalue_reference — klasa

Tworzy typ odwołania rvalue parametru szablonu, jeśli jest to typ obiektu lub funkcji. W przeciwnym razie ze względu na semantykę odniesienie zwijania typ jest taka sama jak wartość parametru szablonu.

## <a name="syntax"></a>Składnia

```cpp
template <class T>
struct add_rvalue_reference;

template <class T>
using add_rvalue_reference_t = typename add_rvalue_reference<T>::type;
```

### <a name="parameters"></a>Parametry

*T*<br/>
Typ do modyfikacji.

## <a name="remarks"></a>Uwagi

`add_rvalue_reference` Klasa ma składową o nazwie `type`, która jest aliasem dla typu odwołania rvalue do parametru szablonu *T*. Semantyka odniesienie zwijania oznacza, że, dla typów niebędących obiektami i innych funkcji *T*, `T&&` jest *T*. Na przykład, gdy *T* jest typem odwołania wartościowanego lewostronnie `add_rvalue_reference<T>::type` jest l-wartości typu odwołania, nie odwołanie rvalue.

Dla wygody \<type_traits > określa szablon Pomocnika `add_rvalue_reference_t`, które aliasy `type` członkiem `add_rvalue_reference`.

## <a name="example"></a>Przykład

Ten przykład kodu używa static_assert, aby pokazać, jak typy odwołań r-wartości są tworzone za pomocą `add_rvalue_reference` i `add_rvalue_reference_t`i w jaki sposób wynik `add_rvalue_reference` na odwołanie lvalue nie jest odwołaniem rvalue typu, ale jest ustawiana na typ odwołania lvalue.

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
Namespace: standardowe

## <a name="see-also"></a>Zobacz także

[<type_traits>](../standard-library/type-traits.md)<br/>
[add_lvalue_reference, klasa](../standard-library/add-lvalue-reference-class.md)<br/>
[is_rvalue_reference, klasa](../standard-library/is-rvalue-reference-class.md)<br/>
