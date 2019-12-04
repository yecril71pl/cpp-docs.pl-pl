---
title: Błąd kompilatora C2208
ms.date: 11/04/2016
f1_keywords:
- C2208
helpviewer_keywords:
- C2208
ms.assetid: 9ae704bc-bf70-45f1-8e47-0470f21edd4e
ms.openlocfilehash: 208e15e98a05089c0e9b1c98400f5267e4f3a48f
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/03/2019
ms.locfileid: "74758934"
---
# <a name="compiler-error-c2208"></a>Błąd kompilatora C2208

"Type": brak składowych zdefiniowanych przy użyciu tego typu

Identyfikator rozpoznania nazwy typu jest w deklaracji agregacji, ale kompilator nie może zadeklarować elementu członkowskiego.

Poniższy przykład generuje C2208:

```cpp
// C2208.cpp
class C {
   C;   // C2208
   C(){}   // OK
};
```
