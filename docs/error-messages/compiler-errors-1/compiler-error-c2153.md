---
title: Błąd kompilatora C2153
ms.date: 11/04/2016
f1_keywords:
- C2153
helpviewer_keywords:
- C2153
ms.assetid: cfc50cb7-9a0f-4b5b-879a-d419c99f7be1
ms.openlocfilehash: 1f03b196b7ddaae80dac1941cdde5be16acace5f
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/03/2019
ms.locfileid: "74748687"
---
# <a name="compiler-error-c2153"></a>Błąd kompilatora C2153

stałe szesnastkowe muszą mieć co najmniej jedną cyfrę szesnastkową

Stałe szesnastkowe 0x, 0X i \x są nieprawidłowe. Co najmniej jedna cyfra szesnastkowa musi następować po x lub X.

Poniższy przykład generuje C2153:

```cpp
// C2153.cpp
int main() {
   int a= 0x;    // C2153
   int b= 0xA;   // OK
}
```
