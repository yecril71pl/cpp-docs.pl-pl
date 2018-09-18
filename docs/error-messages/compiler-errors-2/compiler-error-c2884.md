---
title: Błąd kompilatora C2884 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2884
dev_langs:
- C++
helpviewer_keywords:
- C2884
ms.assetid: 8b4d43e3-3fb5-4360-86c8-de59d8736d4f
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 9d9266162d4608e39982cce1e94751e427bc5e47
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46054717"
---
# <a name="compiler-error-c2884"></a>Błąd kompilatora C2884

"name": wprowadzone za pomocą deklaracji koliduje z lokalnej funkcji "function"

Próbowano zdefiniować funkcję więcej niż jeden raz. Pierwsza definicja jest lokalnej definicji. Druga jest z przestrzeni nazw za pomocą `using` deklaracji.

Poniższy przykład spowoduje wygenerowanie C2884:

```
// C2884.cpp
namespace A {
   void z(int);
}

void f() {
   void z(int);
   using A::z;   // C2884 z is already defined
}
```