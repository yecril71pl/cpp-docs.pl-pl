---
title: Ostrzeżenie kompilatora (poziom 4) C4725
ms.date: 11/04/2016
f1_keywords:
- C4725
helpviewer_keywords:
- C4725
ms.assetid: effa0335-71c3-4b3b-8618-da4b9b46a95d
ms.openlocfilehash: c86d1a5351adf5ba29752613f2301a11fb1b93ce
ms.sourcegitcommit: 573b36b52b0de7be5cae309d45b68ac7ecf9a6d8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/10/2019
ms.locfileid: "74989518"
---
# <a name="compiler-warning-level-4-c4725"></a>Ostrzeżenie kompilatora (poziom 4) C4725

Instrukcja może być niedokładna na niektórych procesorach Pentium

Kod zawiera wbudowaną instrukcję asemblera, która może nie generować dokładnych wyników dla mikroprocesorów Pentium.

Poniższy przykład generuje C4725:

```cpp
// C4725.cpp
// compile with: /W4
// processor: x86
double m32fp = 2.0003e-17;

void f() {
   __asm
   {
      FDIV m32fp   // C4725
   }
}

int main() {
}
```
