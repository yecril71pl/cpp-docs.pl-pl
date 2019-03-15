---
title: Kompilator ostrzeżenie (poziom 1) C4556
ms.date: 08/27/2018
f1_keywords:
- C4556
helpviewer_keywords:
- C4556
ms.assetid: e4c0e296-b747-4db1-9608-30b8b74feac2
ms.openlocfilehash: c31602766261a8d6d0c4f0bb0a880ee34ee1ed45
ms.sourcegitcommit: 8105b7003b89b73b4359644ff4281e1595352dda
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2019
ms.locfileid: "57815397"
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