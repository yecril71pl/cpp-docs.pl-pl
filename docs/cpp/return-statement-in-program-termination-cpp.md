---
title: Return, instrukcja w zakończeniu programu (C++) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- data types [C++], function return types
- function return types [C++], return statement
- return keyword [C++], syntax
ms.assetid: 66d002ab-5625-4b68-8446-71e1b8fcdbd8
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: cfcf65258767178c0f74f63ca6e938e1d940e3be
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46061139"
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