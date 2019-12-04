---
title: Błąd kompilatora od C2500
ms.date: 11/04/2016
f1_keywords:
- C2500
helpviewer_keywords:
- C2500
ms.assetid: 6bff8161-dc9a-48ca-91f1-fd2eefdbbc93
ms.openlocfilehash: 152546fce8f3ee63f8b95595bff052f18cd4ebda
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/03/2019
ms.locfileid: "74746971"
---
# <a name="compiler-error-c2500"></a>Błąd kompilatora od C2500

"Identifier1": "identifier2" jest już bezpośrednią klasą bazową

Klasa lub struktura pojawia się więcej niż jeden raz na liście klas bazowych.

Baza bezpośrednia jest wymieniona na liście podstawowej. Baza pośrednia jest klasą bazową jednej z klas na liście podstawowej.

Nie można określić klasy jako bezpośredniej klasy bazowej więcej niż raz. Klasy można użyć jako pośredniej klasy bazowej więcej niż raz.

Poniższy przykład generuje od C2500:

```cpp
// C2500.cpp
// compile with: /c
class A {};
class B : public A, public A {};    // C2500

// OK
class C : public A {};
class D : public A {};
class E : public C, public D {};
```
