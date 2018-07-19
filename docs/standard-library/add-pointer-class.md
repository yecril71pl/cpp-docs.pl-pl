---
title: add_pointer — klasa | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
f1_keywords:
- type_traits/std::add_pointer
dev_langs:
- C++
helpviewer_keywords:
- add_pointer class
- add_pointer
ms.assetid: d8095cb0-6578-4143-b78f-87f82485298c
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 85efc646daf6ddb55f37c1f46157671eda2f13a8
ms.sourcegitcommit: 3614b52b28c24f70d90b20d781d548ef74ef7082
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/11/2018
ms.locfileid: "38963579"
---
# <a name="addpointer-class"></a>add_pointer — Klasa

Tworzy wskaźnik do typu z określonego typu.

## <a name="syntax"></a>Składnia

```cpp
template <class T>
struct add_pointer;

template <class T>
using add_pointer_t = typename add_pointer<T>::type;
```

### <a name="parameters"></a>Parametry

*T* typ do modyfikacji.

## <a name="remarks"></a>Uwagi

Element członkowski **typedef** `type` nazwy tego samego typu co `remove_reference<T>::type*`. Alias `add_pointer_t` to skrót umożliwiający dostęp do elementu członkowskiego **typedef** `type`.

Ponieważ jest ono nieprawidłowe tworzenie wskaźnika z odwołania `add_pointer` Usuwa odwołanie, jeśli istnieje, z określonego typu, zanim sprawia, że wskaźnik do typu. W związku z tym, można użyć typu z `add_pointer` nie, czy typ jest odwołaniem.

## <a name="example"></a>Przykład

Poniższy przykład pokazuje, że `add_pointer` typu jest taki sam jak wskaźnik do tego typu.

```cpp
#include <type_traits>
#include <iostream>

int main()
{
    std::add_pointer_t<int> *p = (int **)0;

    p = p;  // to quiet "unused" warning
    std::cout << "add_pointer_t<int> == "
        << typeid(*p).name() << std::endl;

    return (0);
}
```

```Output
add_pointer_t<int> == int *
```

## <a name="requirements"></a>Wymagania

**Nagłówek:** \<type_traits >

**Namespace:** standardowe

## <a name="see-also"></a>Zobacz także

[<type_traits>](../standard-library/type-traits.md)<br/>
[remove_pointer, klasa](../standard-library/remove-pointer-class.md)<br/>
