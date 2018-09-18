---
title: Błąd kompilatora C3912 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3912
dev_langs:
- C++
helpviewer_keywords:
- C3912
ms.assetid: 674e050c-11fb-4db1-8bdf-a3e95b41161d
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 26ffa49a6b54769db5b24d91ffcaf72579a6e458
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46115258"
---
# <a name="compiler-error-c3912"></a>Błąd kompilatora C3912

"event": typ zdarzenia musi być typem delegowanym

Zdarzenie została zadeklarowana, ale nie jest obiektem właściwego typu.

Aby uzyskać więcej informacji, zobacz [zdarzeń](../../windows/event-cpp-component-extensions.md).

Poniższy przykład spowoduje wygenerowanie C3912:

```
// C3912.cpp
// compile with: /clr
delegate void H();
ref class X {
   event int Ev;   // C3912
   event H^ Ev2;   // OK
};
```