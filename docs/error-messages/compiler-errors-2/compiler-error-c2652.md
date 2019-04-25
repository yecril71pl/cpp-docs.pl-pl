---
title: Błąd kompilatora C2652
ms.date: 11/04/2016
f1_keywords:
- C2652
helpviewer_keywords:
- C2652
ms.assetid: 6e3d1a90-a989-4088-8afd-dc82f6a2d66f
ms.openlocfilehash: 9c9772052b690ad87de1d408c06478d82d48e724
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62282117"
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