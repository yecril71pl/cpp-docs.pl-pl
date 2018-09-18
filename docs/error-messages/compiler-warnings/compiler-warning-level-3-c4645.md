---
title: Kompilator ostrzeżenie (poziom 3) C4645 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4645
dev_langs:
- C++
helpviewer_keywords:
- C4645
ms.assetid: fd7c1ddf-f0d0-4e10-bab9-ccb4c3476298
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: b597678e726d6b10240c442ed7e48698a993e2fa
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46046540"
---
# <a name="compiler-warning-level-3-c4645"></a>Kompilator ostrzeżenie (poziom 3) C4645

Funkcja zadeklarowana ze __declspec(noreturn) zawiera instrukcję return

A [zwracają](../../cpp/return-statement-in-program-termination-cpp.md) instrukcji został znaleziony w funkcji, która jest oznaczona za pomocą [noreturn](../../cpp/noreturn.md) `__declspec` modyfikator. `return` Instrukcji zostało zignorowane.

Poniższy przykład spowoduje wygenerowanie C4645:

```
// C4645.cpp
// compile with:  /W3
void __declspec(noreturn) func() {
   return;   // C4645, delete this line to resolve
}

int main() {
}
```