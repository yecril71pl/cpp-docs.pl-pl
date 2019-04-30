---
title: Błąd kompilatora C3765
ms.date: 11/04/2016
f1_keywords:
- C3765
helpviewer_keywords:
- C3765
ms.assetid: feadee7a-fcfb-402c-af2f-0e656f814a13
ms.openlocfilehash: 86c043889c5342ed4f3edfc4d8a298bcbd345b3b
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62400243"
---
# <a name="compiler-error-c3765"></a>Błąd kompilatora C3765

"event": nie można zdefiniować określone zdarzenie w klasie/strukturze "type" oznaczonej jako event_receiver

Jeśli klasa jest oznaczona atrybutem [event_receiver](../../windows/event-receiver.md) atrybut klasy nie może zawierać [__event](../../cpp/event.md) deklaracji.

Poniższy przykład spowoduje wygenerowanie C3765:

```
// C3765.cpp
[event_receiver(native)]
struct ER2 {
   __event void f();   // C3765
   __event void b(int);   // C3765
};
```