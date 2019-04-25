---
title: return — instrukcja w zakończeniu działania programu (C++)
ms.date: 11/04/2016
helpviewer_keywords:
- data types [C++], function return types
- function return types [C++], return statement
- return keyword [C++], syntax
ms.assetid: 66d002ab-5625-4b68-8446-71e1b8fcdbd8
ms.openlocfilehash: 9c7b6130ee1a0b49ab75a70d84764d3a1f8c5ef0
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62267616"
---
# <a name="return-statement-in-program-termination-c"></a>return — instrukcja w zakończeniu działania programu (C++)

Wystawianie **zwracają** instrukcji z `main` jest funkcjonalnym odpowiednikiem wywołania `exit` funkcji. Rozważmy następujący przykład:

```cpp
// return_statement.cpp
#include <stdlib.h>
int main()
{
    exit( 3 );
    return 3;
}
```

`exit` i **zwracają** instrukcji w powyższym przykładzie są funkcjonalnie identyczny. Jednak C++ wymaga funkcji, które mają inne niż zwracane typy **void** zwracają wartość. **Zwracają** instrukcji umożliwia zwracanie wartości z `main`.

## <a name="see-also"></a>Zobacz także

[Kończenie działania programu](../cpp/program-termination.md)