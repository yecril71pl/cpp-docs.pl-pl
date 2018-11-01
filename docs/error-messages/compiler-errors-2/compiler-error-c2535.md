---
title: Błąd kompilatora C2535
ms.date: 11/04/2016
f1_keywords:
- C2535
helpviewer_keywords:
- C2535
ms.assetid: a958f83e-e2bf-4a59-b44b-d406ec325d7e
ms.openlocfilehash: b2b5452cfe59284d56b019674ffbabbda0dc62d1
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50574032"
---
# <a name="compiler-error-c2535"></a>Błąd kompilatora C2535

'Identyfikator': funkcja składowa już zdefiniowana lub zadeklarowana

Ten błąd może być spowodowane przy użyciu tej samej listy parametrów formalnych w więcej niż jednej definicji lub deklaracji przeciążonej funkcji.

Jeśli z powodu funkcji Dispose C2535, zobacz [destruktory i finalizatory](../../dotnet/how-to-define-and-consume-classes-and-structs-cpp-cli.md#BKMK_Destructors_and_finalizers) Aby uzyskać więcej informacji.

Poniższy przykład spowoduje wygenerowanie C2535:

```
// C2535.cpp
// compile with: /c
class C {
public:
   void func();   // forward declaration
   void func() {}   // C2535
};
```