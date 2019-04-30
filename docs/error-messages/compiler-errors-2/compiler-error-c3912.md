---
title: Błąd kompilatora C3912
ms.date: 11/04/2016
f1_keywords:
- C3912
helpviewer_keywords:
- C3912
ms.assetid: 674e050c-11fb-4db1-8bdf-a3e95b41161d
ms.openlocfilehash: bd66196c35715304577b8f6785261be8bdcdafec
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62406681"
---
# <a name="compiler-error-c3912"></a>Błąd kompilatora C3912

"event": typ zdarzenia musi być typem delegowanym

Zdarzenie została zadeklarowana, ale nie jest obiektem właściwego typu.

Aby uzyskać więcej informacji, zobacz [zdarzeń](../../extensions/event-cpp-component-extensions.md).

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