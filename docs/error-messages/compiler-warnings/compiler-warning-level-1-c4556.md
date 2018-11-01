---
title: Kompilator ostrzeżenie (poziom 1) C4556
ms.date: 08/27/2018
f1_keywords:
- xml
- C4556
helpviewer_keywords:
- C4556
ms.assetid: e4c0e296-b747-4db1-9608-30b8b74feac2
ms.openlocfilehash: 53261b97249340ce56ce6ae0f5cc0eab7e97a107
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50538492"
---
# <a name="compiler-warning-level-1-c4556"></a>Kompilator ostrzeżenie (poziom 1) C4556

> wartość wewnętrznego argumentu natychmiastowego "*wartość*"jest poza zakresem"*ich* - *górnej granicy*"

## <a name="remarks"></a>Uwagi

Wewnętrzna pasuje do instrukcji sprzętu. Instrukcja sprzętu ma stałą liczbę bitów, aby zakodować stałej. Jeśli *wartość* jest poza zakresem, go nie koduje nowe prawidłowo. Kompilator obcina dodatkowych bitów.

## <a name="example"></a>Przykład

Poniższy przykład C4556 spowoduje wygenerowanie:

```cpp
// C4556.cpp
// compile with: /W1
// processor: x86 IPF
#include <xmmintrin.h>

void test()
{
   __m64 m;
   _m_pextrw(m, 5);   // C4556
}

int main()
{
}
```