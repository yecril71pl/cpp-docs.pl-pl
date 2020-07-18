---
title: Ostrzeżenie kompilatora (poziom 1) C4293
description: Opisuje przyczyny wystąpienia ostrzeżenia kompilatora MSVC C4293 i pokazuje, jak rozwiązać ten problem.
ms.date: 07/15/2020
f1_keywords:
- C4293
helpviewer_keywords:
- C4293
ms.assetid: babecd96-eb51-41a5-9835-462c7a46dbad
ms.openlocfilehash: 3b5a05d4a744b084f1cc34210a5374962064e85d
ms.sourcegitcommit: e15b46ea7888dbdd7e0bb47da76aeed680c3c1f3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/17/2020
ms.locfileid: "86446479"
---
# <a name="compiler-warning-level-1-c4293"></a>Ostrzeżenie kompilatora (poziom 1) C4293

> "*operator*": licznik przesunięć ujemny lub zbyt duży, niezdefiniowane zachowanie

Jeśli licznik przesunięć jest ujemny lub zbyt duży, zachowanie wynikowego obrazu jest niezdefiniowane.

## <a name="remarks"></a>Uwagi

Aby rozwiązać ten problem, można użyć rzutowania pierwszego operandu, aby rozwinąć go do rozmiaru typu wyniku.

## <a name="example"></a>Przykład

Poniższy przykład generuje C4293 i przedstawia sposoby jego rozwiązania:

```cpp
// C4293.cpp
// compile with: /c /W1
unsigned __int64 combine (unsigned lo, unsigned hi)
{
   return (hi << 32) | lo;   // C4293

   // In C, try the following line instead:
   // return ( (unsigned __int64)hi << 32) | lo;
   // In C++, try this line instead:
   // return (static_cast<unsigned __int64>(hi) << 32) | lo;
}
```
