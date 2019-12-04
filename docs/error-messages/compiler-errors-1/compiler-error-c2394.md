---
title: Błąd kompilatora C2394
ms.date: 11/04/2016
f1_keywords:
- C2394
helpviewer_keywords:
- C2394
ms.assetid: 653fa9a0-29b3-48aa-bc01-82f98f717a2b
ms.openlocfilehash: 2c8c23939298f5603b59636ede08b65acaa0f22b
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/03/2019
ms.locfileid: "74744995"
---
# <a name="compiler-error-c2394"></a>Błąd kompilatora C2394

"your_type:: operator'op" ": środowisko CLR lub WinRToperator jest nieprawidłowe. Co najmniej jeden parametr musi mieć następujące typy: "t ^", "^%", "^ &", gdzie T = "your_type"

Operator w środowisko wykonawcze systemu Windows lub typie zarządzanym nie ma co najmniej jednego parametru, którego typ jest taki sam jak typ zwracanej wartości operatora.

Poniższy przykład generuje C2394:

```cpp
// C2394.cpp
// compile with: /clr /c
ref struct Y {
   static Y^ operator -(int i, char c);   // C2394

   // OK
   static Y^ operator -(Y^ hY, char c);
   // or
   static Y^ operator -(int i, Y^& rhY);
};
```
