---
title: Błąd kompilatora C2624
ms.date: 11/04/2016
f1_keywords:
- C2624
helpviewer_keywords:
- C2624
ms.assetid: 32f2ec15-a7cd-4049-a64b-131746d3152b
ms.openlocfilehash: d97722306e5c995a4921c6eb9577d623b21c9517
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/27/2020
ms.locfileid: "87216170"
---
# <a name="compiler-error-c2624"></a>Błąd kompilatora C2624

klas lokalnych nie można używać do deklarowania zmiennych "extern"

Nie można użyć lokalnej klasy lub struktury do deklarowania **`extern`** zmiennych.

Poniższy przykład generuje C2624:

```cpp
// C2624.cpp
int main() {
   struct C {};
   extern C ac;   // C2624
}
```
