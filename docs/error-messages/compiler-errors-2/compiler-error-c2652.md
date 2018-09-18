---
title: Błąd kompilatora C2652 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2652
dev_langs:
- C++
helpviewer_keywords:
- C2652
ms.assetid: 6e3d1a90-a989-4088-8afd-dc82f6a2d66f
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 37b7b259b8eb42692641883c8d69578542cce06e
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46076622"
---
# <a name="compiler-error-c2652"></a>Błąd kompilatora C2652

'Identyfikator': niedozwolony Konstruktor kopiujący: pierwszy parametr nie może być 'Identyfikator'

Pierwszy parametr w Konstruktorze kopiowania ma taki sam jak klasy, struktury lub Unii, dla którego zdefiniowano. Pierwszy parametr może być odwołanie do typu, ale nie samego typu.

Poniższy przykład spowoduje wygenerowanie C2651:

```
// C2652.cpp
// compile with: /c
class A {
   A( A );   // C2652 takes an A
};
class B {
   B( B& );   // OK, reference to B
};
```