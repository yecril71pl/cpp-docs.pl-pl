---
title: Błąd kompilatora C3153
ms.date: 11/04/2016
f1_keywords:
- C3153
helpviewer_keywords:
- C3153
ms.assetid: d775d97e-2480-484f-81f1-88406b10f947
ms.openlocfilehash: 54fa7de8eb3df8d4b3695544c5285cc202275492
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/03/2019
ms.locfileid: "74745920"
---
# <a name="compiler-error-c3153"></a>Błąd kompilatora C3153

"Interface": nie można utworzyć wystąpienia interfejsu

Nie można utworzyć wystąpienia interfejsu. Aby użyć elementów członkowskich interfejsu, należy utworzyć klasę z interfejsu, zaimplementować elementy członkowskie interfejsu, a następnie użyć elementów członkowskich.

Poniższy przykład generuje C3153:

```cpp
// C3153.cpp
// compile with: /clr
interface class A {
};

int main() {
   A^ a = gcnew A;   // C3153
}
```
