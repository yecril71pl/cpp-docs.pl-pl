---
title: Błąd kompilatora C2881 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2881
dev_langs:
- C++
helpviewer_keywords:
- C2881
ms.assetid: b49c63c2-b064-4d4b-a75e-ddd2af947522
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: a7f74a4336af3b8ce8bfe0fa87f7f1a84746ff11
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46052494"
---
# <a name="compiler-error-c2881"></a>Błąd kompilatora C2881

"{1 & gt": jest już używana jako alias dla "namespace2"

Nie możesz użyć tej samej nazwie jako alias dla dwóch przestrzeni nazw.

Poniższy przykład spowoduje wygenerowanie C2881:

```
// C2881.cpp
// compile with: /c
namespace A {
   int k;
}

namespace B {
   int i;
}

namespace C = A;
namespace C = B;   // C2881 C is already an alias for A
```