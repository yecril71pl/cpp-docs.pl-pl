---
title: Ostrzeżenie kompilatora (poziom 3) C4316
ms.date: 11/04/2016
f1_keywords:
- C4316
helpviewer_keywords:
- C4316
ms.assetid: 10371f01-aeb8-40ac-a290-59e63efa5ad4
ms.openlocfilehash: 0d920cb3dc967854d1a507d06ce31fde6a670434
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/24/2020
ms.locfileid: "80198851"
---
# <a name="compiler-warning-level-3-c4316"></a>Ostrzeżenie kompilatora (poziom 3) C4316

Obiekt przydzielony na stercie może nie być wyrównany dla tego typu.

Obiekt z nadmiernym wyrównaniem przydzielony przy użyciu `operator new` może nie mieć określonego wyrównania. Zastąp [operator new](../../c-runtime-library/operator-new-crt.md) i [operator delete](../../c-runtime-library/operator-delete-crt.md) dla niewyrównanych typów, tak aby korzystały z wyrównanych procedur alokacji, na przykład [_aligned_malloc](../../c-runtime-library/reference/aligned-malloc.md) i [_aligned_free](../../c-runtime-library/reference/aligned-free.md). Poniższy przykład generuje C4316:

```cpp
// C4316.cpp
// Test: cl /W3 /c C4316.cpp

__declspec(align(32)) struct S {}; // C4324

int main() {
    new S; // C4316
}
```
