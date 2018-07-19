---
title: is_default_constructible, klasa | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
f1_keywords:
- type_traits/std::is_default_constructible
dev_langs:
- C++
helpviewer_keywords:
- is_default_constructible
ms.assetid: dd8f1c44-dae5-4258-891f-c5e048d94092
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 23a361362d574910d21b0031d5687331f8c11dda
ms.sourcegitcommit: 3614b52b28c24f70d90b20d781d548ef74ef7082
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/11/2018
ms.locfileid: "38964258"
---
# <a name="isdefaultconstructible-class"></a>is_default_constructible, klasa

Sprawdza, czy typ ma konstruktora domyślnego.

## <a name="syntax"></a>Składnia

```cpp
template <class Ty>
struct is_default_constructible;
```

### <a name="parameters"></a>Parametry

*T* typ do zapytania.

## <a name="remarks"></a>Uwagi

Wystąpienie typu predykatu ma wartość true, jeśli typ *T* jest typu klasy, która ma Konstruktor domyślny w przeciwnym razie przechowuje wartość false. Jest to równoważne do predykatu `is_constructible<T>`. Typ *T* musi być typem kompletnym **void**, lub tablicę nieznany powiązane z.

## <a name="example"></a>Przykład

```cpp
#include <type_traits>
#include <iostream>

struct Simple
{
    Simple() : val(0) {}
    int val;
};

struct Simple2
{
    Simple2(int v) : val(v) {}
    int val;
};

int main()
{
    std::cout << "is_default_constructible<Simple> == " << std::boolalpha
        << std::is_default_constructible<Simple>::value << std::endl;
    std::cout << "is_default_constructible<Simple2> == " << std::boolalpha
        << std::is_default_constructible<Simple2>::value << std::endl;

    return (0);
}

```

```Output
is_default_constructible<Simple> == true
is_default_constructible<Simple2> == false
```

## <a name="requirements"></a>Wymagania

**Nagłówek:** \<type_traits >

**Namespace:** standardowe

## <a name="see-also"></a>Zobacz także

[<type_traits>](../standard-library/type-traits.md)<br/>
