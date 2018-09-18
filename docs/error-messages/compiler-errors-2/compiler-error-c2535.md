---
title: Błąd kompilatora C2535 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2535
dev_langs:
- C++
helpviewer_keywords:
- C2535
ms.assetid: a958f83e-e2bf-4a59-b44b-d406ec325d7e
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 98e1920b2163a318fbdba3b64d56bf74a8cd809f
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46085904"
---
# <a name="compiler-error-c2535"></a>Błąd kompilatora C2535

'Identyfikator': funkcja składowa już zdefiniowana lub zadeklarowana

Ten błąd może być spowodowane przy użyciu tej samej listy parametrów formalnych w więcej niż jednej definicji lub deklaracji przeciążonej funkcji.

Jeśli z powodu funkcji Dispose C2535, zobacz [destruktory i finalizatory](../../dotnet/how-to-define-and-consume-classes-and-structs-cpp-cli.md#BKMK_Destructors_and_finalizers) Aby uzyskać więcej informacji.

Jeśli kompilacja projektu ATL, zobacz artykuł bazy wiedzy Q241852.

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