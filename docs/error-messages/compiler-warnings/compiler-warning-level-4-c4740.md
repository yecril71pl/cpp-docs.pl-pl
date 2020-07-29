---
title: Ostrzeżenie kompilatora (poziom 4) C4740
ms.date: 11/04/2016
f1_keywords:
- C4740
helpviewer_keywords:
- C4740
ms.assetid: 85528969-966a-44b4-8a2f-971704c64477
ms.openlocfilehash: 0aa4cb9df3f6f9d7499c67fb0b07bee5dabd6d73
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/27/2020
ms.locfileid: "87219836"
---
# <a name="compiler-warning-level-4-c4740"></a>Ostrzeżenie kompilatora (poziom 4) C4740

przepływ wewnątrz lub z wbudowanego kodu ASM pomija optymalizację globalną

W przypadku przejścia do lub z **`asm`** bloku, optymalizacje globalne są wyłączone dla tej funkcji.

Poniższy przykład generuje C4740:

```cpp
// C4740.cpp
// compile with: /O2 /W4
// processor: x86
int main() {
   __asm jmp tester
   tester:;
}
```
