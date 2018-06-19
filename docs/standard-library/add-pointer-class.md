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
ms.openlocfilehash: c7a80ffbfbcfb8c350eecc54e87c4cadaaab0295
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/07/2018
ms.locfileid: "33841421"
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

*T* typu do zmodyfikowania.

## <a name="remarks"></a>Uwagi

Element członkowski typedef `type` nazwy tego samego typu co `remove_reference<T>::type*`. Alias `add_pointer_t` to skrót do dostępu — element członkowski typedef `type`.

Ponieważ jest on nieprawidłowy wskaźnik z odwołania, aby `add_pointer` Usuwa odwołanie, z określonego typu przed nią sprawia, że wskaźnik do typu. W związku z tym, można użyć typu z `add_pointer` bez trwa zależy od tego, czy typ jest odwołanie.

## <a name="example"></a>Przykład

W poniższym przykładzie pokazano, że `add_pointer` typu jest taka sama jak wskaźnik do typu.

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

**Namespace:** Standard

## <a name="see-also"></a>Zobacz także

[<type_traits>](../standard-library/type-traits.md)<br/>
[remove_pointer, klasa](../standard-library/remove-pointer-class.md)<br/>
