---
title: Błąd kompilatora C3748 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3748
dev_langs:
- C++
helpviewer_keywords:
- C3748
ms.assetid: 6fe71a0a-dd93-4ce6-9729-b9616360cf34
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 31b2d0434ec48f0c1d7ecf767ce2746e2c603401
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46116857"
---
# <a name="compiler-error-c3748"></a>Błąd kompilatora C3748

"interface": zarządzane interfejsy nie mogą wyzwalać zdarzeń

[__Event](../../cpp/event.md) — słowo kluczowe nie może występować wewnątrz interfejsu.

Poniższy przykład spowoduje wygenerowanie C3748:

```
// C3748.cpp
__interface I {
// try the following line instead
// struct I {
   __event void f();   // C3748
};

int main() {
}
```