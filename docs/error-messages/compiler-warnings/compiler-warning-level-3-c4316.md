---
title: Kompilator ostrzeżenie (poziom 3) C4316 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4316
dev_langs:
- C++
helpviewer_keywords:
- C4316
ms.assetid: 10371f01-aeb8-40ac-a290-59e63efa5ad4
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: a4170481b95cca0d43aa03c776009a5030194a4c
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46032929"
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