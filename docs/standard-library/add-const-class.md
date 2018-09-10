---
title: add_const — klasa | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
f1_keywords:
- type_traits/std::add_const
dev_langs:
- C++
helpviewer_keywords:
- add_const class
- add_const
ms.assetid: 1262a1eb-8c9c-4dd6-9f43-88ba280182f1
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 46d0d52f53a45b53c8634a40c56feb167793e565
ms.sourcegitcommit: 761c5f7c506915f5a62ef3847714f43e9b815352
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/07/2018
ms.locfileid: "44102839"
---
# <a name="addconst-class"></a>add_const — Klasa

Tworzy typ const z typu.

## <a name="syntax"></a>Składnia

```cpp
template <class Ty>
struct add_const;
```

### <a name="parameters"></a>Parametry

*Ty*<br/>
Typ do modyfikacji.

## <a name="remarks"></a>Uwagi

Wystąpienie modyfikatora typu przechowuje zmodyfikowany typ, który jest *Ty* Jeśli *Ty* jest odwołaniem, funkcją lub kwalifikowanego typu const, w przeciwnym razie `const Ty`.

## <a name="example"></a>Przykład

```cpp
// std__type_traits__add_const.cpp
// compile with: /EHsc
#include <type_traits>
#include <iostream>

int main()
{
    std::add_const<int>::type *p = (const int *)0;

    p = p;  // to quiet "unused" warning
    std::cout << "add_const<int> == "
        << typeid(*p).name() << std::endl;

    return (0);
}
```

```Output
add_const<int> == int
```

## <a name="requirements"></a>Wymagania

**Nagłówek:** \<type_traits >

**Namespace:** standardowe

## <a name="see-also"></a>Zobacz także

[<type_traits>](../standard-library/type-traits.md)<br/>
[remove_const, klasa](../standard-library/remove-const-class.md)<br/>
