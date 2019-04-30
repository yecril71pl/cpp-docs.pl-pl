---
title: is_placeholder — Klasa
ms.date: 11/04/2016
f1_keywords:
- functional/std::is_placeholder
helpviewer_keywords:
- is_placeholder class
ms.assetid: 2b21a792-96d1-4bb8-b911-0db796510835
ms.openlocfilehash: 2c7848c88194a9b541867b26ffe27764ad862503
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62413635"
---
# <a name="isplaceholder-class"></a>is_placeholder — Klasa

Sprawdza, czy typ jest symbolem zastępczym.

## <a name="syntax"></a>Składnia

struct is_placeholder { static const int value; };

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
