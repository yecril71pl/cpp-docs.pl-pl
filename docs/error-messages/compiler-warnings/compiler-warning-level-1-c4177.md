---
title: Kompilator ostrzeżenie (poziom 1) C4177 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4177
dev_langs:
- C++
helpviewer_keywords:
- C4177
ms.assetid: 2b05a5b3-696e-4f21-818e-227b9335e748
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 489b3a23fa17cbe7fac473c7c0b51f1c680c234a
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46032552"
---
# <a name="compiler-warning-level-1-c4177"></a>Kompilator ostrzeżenie (poziom 1) C4177

\#dyrektywy pragma powinien być w zakresie globalnym

[Pragma](../../preprocessor/pragma-directives-and-the-pragma-keyword.md) pragma nie powinny być używane w ramach zakresu lokalnego. **Pragma** nie będzie obowiązywać do momentu występuje zakresie globalnym po bieżącym zakresie.

Poniższy przykład spowoduje wygenerowanie C4177:

```
// C4177.cpp
// compile with: /W1
// #pragma bss_seg("global")   // OK

int main() {
   #pragma bss_seg("local")    // C4177
}
```