---
title: is_placeholder — Klasa
ms.date: 11/04/2016
f1_keywords:
- functional/std::is_placeholder
helpviewer_keywords:
- is_placeholder class
ms.assetid: 2b21a792-96d1-4bb8-b911-0db796510835
ms.openlocfilehash: 2c7848c88194a9b541867b26ffe27764ad862503
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50613736"
---
# <a name="isplaceholder-class"></a>is_placeholder — Klasa

Sprawdza, czy typ jest symbolem zastępczym.

## <a name="syntax"></a>Składnia

is_placeholder — struktura {statyczny const int wartość;};

## <a name="remarks"></a>Uwagi

Stała wartość `value` wynosi 0, jeśli typ `Ty` nie jest symbolem zastępczym; w przeciwnym razie jego wartość to pozycja argumentu wywołania funkcji, który powiąże. Możesz użyć do określenia wartości `N` n-ty symbolu zastępczego `_N`.

## <a name="example"></a>Przykład

```cpp
// std__functional__is_placeholder.cpp
// compile with: /EHsc
#include <functional>
#include <iostream>

using namespace std::placeholders;

template<class Expr>
void test_for_placeholder(const Expr&)
{
    std::cout << std::is_placeholder<Expr>::value << std::endl;
}

int main()
{
    test_for_placeholder(3.0);
    test_for_placeholder(_3);

    return (0);
}
```

```Output
0
3
```

## <a name="requirements"></a>Wymagania

**Nagłówek:** \<funkcjonalności >

**Namespace:** standardowe

## <a name="see-also"></a>Zobacz także

[Obiekt _1](../standard-library/1-object.md)<br/>
