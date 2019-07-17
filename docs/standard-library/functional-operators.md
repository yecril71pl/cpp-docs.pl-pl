---
title: '&lt;funkcjonalności&gt; operatorów'
ms.date: 11/04/2016
f1_keywords:
- functional/std::operator!=
- functional/std::operator==
helpviewer_keywords:
- functional operators
ms.assetid: d4b3c760-f3e2-4b65-bdaa-d42e8dd6f5e1
ms.openlocfilehash: b396e5c692129821c0deb9aef9469a5c54e600b0
ms.sourcegitcommit: 3590dc146525807500c0477d6c9c17a4a8a2d658
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/16/2019
ms.locfileid: "68243773"
---
# <a name="ltfunctionalgt-operators"></a>&lt;funkcjonalności&gt; operatorów

## <a name="op_eq_eq"></a> operator ==

Sprawdza, czy obiekt jest pusty.

```cpp
template <class Fty>
    bool operator==(const function<Fty>& f, null_ptr_type npc);

template <class Fty>
    bool operator==(null_ptr_type npc, const function<Fty>& f);
```

### <a name="parameters"></a>Parametry

*Fty*\
Typ funkcji do opakowania.

*F*\
Obiekt funkcji

*npc*\
Wskaźnik zerowy.

### <a name="remarks"></a>Uwagi

Operatory zarówno przyjmują argument, który jest odwołaniem do `function` obiektu i argument, który jest stałą pustego wskaźnika. Oba zwracają wartość true tylko wtedy, gdy `function` obiekt jest pusty.

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

## <a name="op_neq"></a> operator! =

Sprawdza, czy obiekt nie jest pusty.

```cpp
template <class Fty>
    bool operator!=(const function<Fty>& f, null_ptr_type npc);

template <class Fty>
    bool operator!=(null_ptr_type npc, const function<Fty>& f);
```

### <a name="parameters"></a>Parametry

*Fty*\
Typ funkcji do opakowania.

*F*\
Obiekt funkcji

*npc*\
Wskaźnik zerowy.

### <a name="remarks"></a>Uwagi

Operatory zarówno przyjmują argument, który jest odwołaniem do `function` obiektu i argument, który jest stałą pustego wskaźnika. Oba zwracają wartość true tylko wtedy, gdy `function` obiektu nie jest pusty.

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
