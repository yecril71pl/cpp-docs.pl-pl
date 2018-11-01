---
title: Kompilator ostrzeżenie (poziom 1) C4612
ms.date: 08/27/2018
f1_keywords:
- C4612
helpviewer_keywords:
- C4612
ms.assetid: 21ac02b2-51cd-4aff-9b70-d543511d5962
ms.openlocfilehash: ed5458fc52c1c9c9f12187095e4658204613d1a1
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50574268"
---
# <a name="compiler-warning-level-1-c4612"></a>Kompilator ostrzeżenie (poziom 1) C4612

> Błąd w nazwie pliku dołączanego

## <a name="remarks"></a>Uwagi

Ostrzeżenie to pojawia się za pomocą **#pragma include_alias** gdy nazwa pliku jest nieprawidłowe lub niekompletne.

Argumenty **#pragma include_alias** instrukcji można użyć formy oferty ("*filename*") lub formularz nawias kątowy (\<*filename*>), ale oba muszą Użyj tego samego formularza.

## <a name="example"></a>Przykład

```cpp
// C4612.cpp
// compile with: /W1 /LD
#pragma include_alias("StandardIO", <stdio.h>) // C4612
```