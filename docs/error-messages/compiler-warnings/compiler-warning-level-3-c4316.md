---
title: Kompilator ostrzeżenie (poziom 3) C4316
ms.date: 11/04/2016
f1_keywords:
- C4316
helpviewer_keywords:
- C4316
ms.assetid: 10371f01-aeb8-40ac-a290-59e63efa5ad4
ms.openlocfilehash: 5f895a231c8b32d76e4ccd3c15ffae5717d8017f
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50476066"
---
# <a name="compiler-warning-level-3-c4316"></a>Kompilator ostrzeżenie (poziom 3) C4316

Obiekt przydzielony na stosie może nie wyrównany dla tego typu.

Obiekt zbyt wyrównany, przydzielany przy użyciu `operator new` nie może mieć określonego wyrównania. Zastąp [nowy operator](../../c-runtime-library/operator-new-crt.md) i [operatora delete](../../c-runtime-library/operator-delete-crt.md) dla nadmiernie wyrównanych typów, tak aby używały wyrównanych procedur alokacji — na przykład [_aligned_malloc](../../c-runtime-library/reference/aligned-malloc.md) i [_aligned_free —](../../c-runtime-library/reference/aligned-free.md). Poniższy przykład spowoduje wygenerowanie C4316:

```cpp
// C4316.cpp
// Test: cl /W3 /c C4316.cpp

__declspec(align(32)) struct S {}; // C4324

int main() {
    new S; // C4316
}
```