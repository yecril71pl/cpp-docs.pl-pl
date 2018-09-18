---
title: Błąd kompilatora C3650 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3650
dev_langs:
- C++
helpviewer_keywords:
- C3650
ms.assetid: ca4d8de4-b027-4d13-9b9f-03ca62905c33
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 0ee7477acc26621a13a1a1d3b4f2d0d0f563c665
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46016549"
---
# <a name="compiler-error-c3650"></a>Błąd kompilatora C3650

"interface_method": nie można użyć jako jawnego przesłaniania, musi być wirtualną składową klasy bazowej

Próbowano wykonać jawnego przesłaniania na element członkowski, który nie jest wirtualny.

Aby uzyskać więcej informacji, zobacz [jawne zastępowanie](../../windows/explicit-overrides-cpp-component-extensions.md).

Poniższy przykład spowoduje wygenerowanie C3650:

```
// C3650.cpp
// compile with: /clr
public interface struct I {
   void a();
};

public ref class S {
public:
   static int f() { return 0; }
   static int g() { return 0; }
};

public ref struct T1 : public S, I {
   virtual int f() new sealed = S::f;   // C3650
   virtual int g() { return 0; }   // OK does not override S::g
   virtual void a() new sealed = I::a {}   // OK
};
```