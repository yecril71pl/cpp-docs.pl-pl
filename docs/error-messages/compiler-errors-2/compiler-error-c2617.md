---
title: Błąd kompilatora C2617
ms.date: 11/04/2016
f1_keywords:
- C2617
helpviewer_keywords:
- C2617
ms.assetid: d6a435d2-7d95-4dbf-ad4a-abe4744f63e8
ms.openlocfilehash: 60dd4e7de083bc4258eb7289d7b1c90d90871655
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/03/2019
ms.locfileid: "74754787"
---
# <a name="compiler-error-c2617"></a>Błąd kompilatora C2617

"Function": niespójna instrukcja return

Określona funkcja nie ma zadeklarowanego typu zwracanego, a poprzednia instrukcja return nie dostarczyła wartości.

Poniższy przykład generuje C2617:

```cpp
// C2617.cpp
int i;
func() {   // no return type prototype
   if( i ) return;   // no return value
   else return( 1 );   // C2617 detected on this line
}
```

Możliwe rozwiązanie:

```cpp
// C2617b.cpp
// compile with: /c
int i;
int MyF() {
   if (i)
      return 0;
   else
      return (1);
}
```
