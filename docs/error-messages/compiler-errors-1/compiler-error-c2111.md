---
title: Błąd kompilatora C2111
ms.date: 11/04/2016
f1_keywords:
- C2111
helpviewer_keywords:
- C2111
ms.assetid: 38fd42ec-1480-4a44-aaca-ae4593ed5f50
ms.openlocfilehash: 193fa787c8e6beb0d4a45f419d3af3baf7988cc1
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/03/2019
ms.locfileid: "74757816"
---
# <a name="compiler-error-c2111"></a>Błąd kompilatora C2111

' + ': Dodawanie wskaźników wymaga całkowitego operandu

Podjęto próbę dodania niecałkowitej wartości do wskaźnika przy użyciu operatora plus (`+`).

Poniższy przykład generuje C2111:

```cpp
// C2111.cpp
int main() {
   int *a = 0, *pa = 0, b = 0;
   double d = 0.00;

   a = pa + d;   // C2111
   a = pa + b;   // OK
}
```
