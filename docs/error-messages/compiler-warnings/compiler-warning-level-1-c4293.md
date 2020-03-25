---
title: Ostrzeżenie kompilatora (poziom 1) C4293
ms.date: 11/04/2016
f1_keywords:
- C4293
helpviewer_keywords:
- C4293
ms.assetid: babecd96-eb51-41a5-9835-462c7a46dbad
ms.openlocfilehash: 6f224996904c583001496e04c020de97bc932738
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/24/2020
ms.locfileid: "80175691"
---
# <a name="compiler-warning-level-1-c4293"></a>Ostrzeżenie kompilatora (poziom 1) C4293

"operator": licznik przesunięć ujemny lub zbyt duży, niezdefiniowane zachowanie

Jeśli licznik przesunięć jest ujemny lub zbyt duży, zachowanie wynikowego obrazu jest niezdefiniowane.

## <a name="example"></a>Przykład

Poniższy przykład generuje C4293:

```cpp
// C4293.cpp
// compile with: /c /W1
unsigned __int64 combine (unsigned lo, unsigned hi) {

   return (hi << 32) | lo;   // C4293

   // try the following line instead
   // return ( (unsigned __int64)hi << 32) | lo;
}
```
