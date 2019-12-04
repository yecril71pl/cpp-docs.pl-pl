---
title: Błąd kompilatora C2652
ms.date: 11/04/2016
f1_keywords:
- C2652
helpviewer_keywords:
- C2652
ms.assetid: 6e3d1a90-a989-4088-8afd-dc82f6a2d66f
ms.openlocfilehash: cedee3f1e3289aaf0ea38d75b6c812b61f891435
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/03/2019
ms.locfileid: "74756126"
---
# <a name="compiler-error-c2652"></a>Błąd kompilatora C2652

"Identyfikator": niedozwolony Konstruktor kopiujący: pierwszy parametr nie może być identyfikatorem

Pierwszy parametr w konstruktorze kopiującym ma ten sam typ, który jest klasą, strukturą lub Unią, dla której jest zdefiniowany. Pierwszy parametr może być odwołaniem do typu, ale nie do samego typu.

Poniższy przykład generuje C2651:

```cpp
// C2652.cpp
// compile with: /c
class A {
   A( A );   // C2652 takes an A
};
class B {
   B( B& );   // OK, reference to B
};
```
