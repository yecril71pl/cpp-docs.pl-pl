---
title: Ostrzeżenie kompilatora (poziom 1) C4556
ms.date: 08/27/2018
f1_keywords:
- C4556
helpviewer_keywords:
- C4556
ms.assetid: e4c0e296-b747-4db1-9608-30b8b74feac2
ms.openlocfilehash: 501d79a8a86fcd3e2d8ba08dc2f03488f9abb827
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/24/2020
ms.locfileid: "80162312"
---
# <a name="compiler-warning-level-1-c4556"></a>Ostrzeżenie kompilatora (poziom 1) C4556

> wartość wewnętrznego argumentu bezpośredniego "*Value*" jest poza zakresem "*lowerbound* - *upperbound*"

## <a name="remarks"></a>Uwagi

Wewnętrznie pasuje do instrukcji sprzętowej. Instrukcja sprzętowa ma ustaloną liczbę bitów do zakodowania stałej. Jeśli *wartość* znajduje się poza zakresem, nie zostanie poprawnie zakodować. Kompilator obcina dodatkowe bity.

## <a name="example"></a>Przykład

Poniższy przykład generuje C4556:

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
