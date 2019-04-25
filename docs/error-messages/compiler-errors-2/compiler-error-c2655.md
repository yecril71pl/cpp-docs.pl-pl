---
title: Błąd kompilatora C2655
ms.date: 11/04/2016
f1_keywords:
- C2655
helpviewer_keywords:
- C2655
ms.assetid: beaefa6e-51b3-4df9-9150-960f3fbf40e0
ms.openlocfilehash: 094dabb5ad07796194ae391000ca1e9025602d93
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62161189"
---
# <a name="compiler-error-c2655"></a>Błąd kompilatora C2655

'Identyfikator': definicja lub ponowna deklaracja jest niedozwolona w bieżącym zakresie

Identyfikator może być ponownie zadeklarowany tylko w zakresie globalnym.

Poniższy przykład spowoduje wygenerowanie C2655:

```
// C2655.cpp
class A {};
class B {
public:
   static int i;
};

int B::i;  // OK

int main() {
   A B::i;  // C2655
}
```