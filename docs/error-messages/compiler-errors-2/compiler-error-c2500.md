---
title: Błąd kompilatora C2500
ms.date: 11/04/2016
f1_keywords:
- C2500
helpviewer_keywords:
- C2500
ms.assetid: 6bff8161-dc9a-48ca-91f1-fd2eefdbbc93
ms.openlocfilehash: a5753fc99efcdb1064a21981c62faaba84d44189
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62165589"
---
# <a name="compiler-error-c2500"></a>Błąd kompilatora C2500

"identifier1": "identifier2" jest już bezpośrednią klasą bazową

Klasa lub struktura występuje więcej niż jeden raz na liście klas bazowych.

Bezpośredniej klasy podstawowej jest jednym wymienione na liście bazowych. Pośrednią podstawą jest klasą bazową dla jednej z klas na liście bazowych.

Klasa nie można określić jako bezpośrednią klasą bazową więcej niż jeden raz. Klasa może służyć jako pośrednią klasą bazową więcej niż jeden raz.

Poniższy przykład spowoduje wygenerowanie od C2500:

```
// C2500.cpp
// compile with: /c
class A {};
class B : public A, public A {};    // C2500

// OK
class C : public A {};
class D : public A {};
class E : public C, public D {};
```