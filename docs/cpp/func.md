---
title: __FUNC__
ms.date: 10/19/2017
f1_keywords:
- __func__
ms.assetid: a5299b8d-f0ee-4af2-91dd-8fb165e68798
ms.openlocfilehash: eecd3efea6239c92a8bc81c0ed13a9563e5b87d2
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50438587"
---
# <a name="func"></a>__FUNC__

**(C ++ 11)**  Predefiniowany identyfikator &#95; &#95;func&#95; &#95; jest niejawnie definiowany jako ciąg zawierający niekwalifikowaną i unadorned nazwę funkcji otaczającej. &#95;&#95;FUNC&#95; &#95; jest wymagane na podstawie stosownych C++ standard, a nie jest rozszerzeniem firmy Microsoft.

## <a name="syntax"></a>Składnia

```cpp
__func__
```

## <a name="return-value"></a>Wartość zwracana

Zwraca zakończony znakiem null const char tablicę znaków zawierający nazwę funkcji.

## <a name="example"></a>Przykład

```cpp
#include <string>
#include <iostream>

namespace Test
{
    struct Foo
    {
        static void DoSomething(int i, std::string s)
        {
           std::cout << __func__ << std::endl; // Output: DoSomething
        }
    };
}

int main()
{
    Test::Foo::DoSomething(42, "Hello");

    return 0;
}
```

## <a name="requirements"></a>Wymagania

C++11