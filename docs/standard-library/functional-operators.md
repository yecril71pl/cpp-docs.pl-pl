---
title: '&lt;funkcjonalne operatory&gt;'
ms.date: 11/04/2016
f1_keywords:
- functional/std::operator!=
- functional/std::operator==
helpviewer_keywords:
- functional operators
ms.assetid: d4b3c760-f3e2-4b65-bdaa-d42e8dd6f5e1
ms.openlocfilehash: b396e5c692129821c0deb9aef9469a5c54e600b0
ms.sourcegitcommit: 7ecd91d8ce18088a956917cdaf3a3565bd128510
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/16/2020
ms.locfileid: "79419057"
---
# <a name="ltfunctionalgt-operators"></a>&lt;funkcjonalne operatory&gt;

## <a name="op_eq_eq"></a>operator = =

Testuje, czy możliwy do przeprowadzenia obiekt jest pusty.

```cpp
template <class Fty>
    bool operator==(const function<Fty>& f, null_ptr_type npc);

template <class Fty>
    bool operator==(null_ptr_type npc, const function<Fty>& f);
```

### <a name="parameters"></a>Parametry

*Fty*\
Typ funkcji do oblewania.

\ *f*
Obiekt Function

*npc*\
Wskaźnik o wartości null.

### <a name="remarks"></a>Uwagi

Operatory przyjmują argument, który jest odwołaniem do obiektu `function` i argumentem, który jest stałą wskaźnika o wartości null. Oba zwracają wartość true tylko wtedy, gdy obiekt `function` jest pusty.

### <a name="example"></a>Przykład

```cpp
// std__functional__operator_eq.cpp
// compile with: /EHsc
#include <functional>
#include <iostream>

int neg(int val)
{
    return (-val);
}

int main()
{
    std::function<int(int)> fn0;
    std::cout << std::boolalpha << "empty == "
        << (fn0 == 0) << std::endl;

    std::function<int(int)> fn1(neg);
    std::cout << std::boolalpha << "empty == "
        << (fn1 == 0) << std::endl;

    return (0);
}
```

```Output
empty == true
empty == false
```

## <a name="op_neq"></a>operator! =

Testuje, czy możliwy do przeprowadzenia obiekt nie jest pusty.

```cpp
template <class Fty>
    bool operator!=(const function<Fty>& f, null_ptr_type npc);

template <class Fty>
    bool operator!=(null_ptr_type npc, const function<Fty>& f);
```

### <a name="parameters"></a>Parametry

*Fty*\
Typ funkcji do oblewania.

\ *f*
Obiekt Function

*npc*\
Wskaźnik o wartości null.

### <a name="remarks"></a>Uwagi

Operatory przyjmują argument, który jest odwołaniem do obiektu `function` i argumentem, który jest stałą wskaźnika o wartości null. Oba zwracają wartość true tylko wtedy, gdy obiekt `function` nie jest pusty.

### <a name="example"></a>Przykład

```cpp
// std__functional__operator_ne.cpp
// compile with: /EHsc
#include <functional>
#include <iostream>

int neg(int val)
    {
    return (-val);
    }

int main()
    {
    std::function<int (int)> fn0;
    std::cout << std::boolalpha << "not empty == "
        << (fn0 != 0) << std::endl;

    std::function<int (int)> fn1(neg);
    std::cout << std::boolalpha << "not empty == "
        << (fn1 != 0) << std::endl;

    return (0);
    }
```

```Output
not empty == false
not empty == true
```
