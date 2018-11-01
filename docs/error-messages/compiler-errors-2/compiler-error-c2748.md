---
title: Błąd kompilatora C2748
ms.date: 11/04/2016
f1_keywords:
- C2748
helpviewer_keywords:
- C2748
ms.assetid: b63ac78b-a200-499c-afea-15af1a1e819e
ms.openlocfilehash: a85ee151d9a4d62cc4b95248d669ff924365a95a
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50655640"
---
# <a name="compiler-error-c2748"></a>Błąd kompilatora C2748

zarządzane lub utworzenia tablicy WinRT musi mieć rozmiar tablicy lub inicjatora tablicy

A zarządzany lub tablicy WinRT został niewłaściwie sformatowany. Aby uzyskać więcej informacji, zobacz [tablicy](../../windows/arrays-cpp-component-extensions.md).

Poniższy przykład generuje C2748 i pokazuje, jak go naprawić:

```
// C2748.cpp
// compile with: /clr
int main() {
   array<int> ^p1 = new array<int>();   // C2748
   // try the following line instead
   array<int> ^p2 = new array<int>(2);
}
```